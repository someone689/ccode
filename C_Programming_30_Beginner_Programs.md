# C Programming -- 30 Important Practical Programs

## Contents

Click any title below to jump directly to its program.

1.  [Check Whether a Number Is
    Prime](#1-check-whether-a-number-is-prime)
2.  [Find the Inverse of a 2×2
    Matrix](#2-find-the-inverse-of-a-22-matrix)
3.  [Find the Largest and Smallest Elements in an
    Array](#3-find-the-largest-and-smallest-elements-in-an-array)
4.  [Count Vowels and Consonants in Each
    Word](#4-count-vowels-and-consonants-in-each-word)
5.  [Sum of the Digits of a Positive
    Integer](#5-sum-of-the-digits-of-a-positive-integer)
6.  [Multiply Two Matrices](#6-multiply-two-matrices)
7.  [Copy a String Without Built-in
    Functions](#7-copy-a-string-without-built-in-functions)
8.  [Binary Search in a Sorted
    Array](#8-binary-search-in-a-sorted-array)
9.  [Check Whether a Number Is a
    Palindrome](#9-check-whether-a-number-is-a-palindrome)
10. [Print a Diamond Pattern](#10-print-a-diamond-pattern)
11. [Transpose a Matrix](#11-transpose-a-matrix)
12. [Factorial Using Recursion](#12-factorial-using-recursion)
13. [Check Whether a Number Is an Armstrong
    Number](#13-check-whether-a-number-is-an-armstrong-number)
14. [Selection Sort](#14-selection-sort)
15. [Sum of Diagonal Elements of a
    Matrix](#15-sum-of-diagonal-elements-of-a-matrix)
16. [Bubble Sort](#16-bubble-sort)
17. [Display a Student's Grade](#17-display-a-students-grade)
18. [Arrange Characters of a String in Ascending
    Order](#18-arrange-characters-of-a-string-in-ascending-order)
19. [Check Whether a Number Is Even or
    Odd](#19-check-whether-a-number-is-even-or-odd)
20. [Find the Largest of Three
    Numbers](#20-find-the-largest-of-three-numbers)
21. [Swap Two Numbers Using a Temporary
    Variable](#21-swap-two-numbers-using-a-temporary-variable)
22. [Sum of the First N Natural
    Numbers](#22-sum-of-the-first-n-natural-numbers)
23. [Print a Multiplication Table](#23-print-a-multiplication-table)
24. [Reverse the Digits of an
    Integer](#24-reverse-the-digits-of-an-integer)
25. [Generate the Fibonacci Series](#25-generate-the-fibonacci-series)
26. [Find the Sum and Average of Array
    Elements](#26-find-the-sum-and-average-of-array-elements)
27. [Linear Search in an Array](#27-linear-search-in-an-array)
28. [Add Two Matrices](#28-add-two-matrices)
29. [Find String Length Without Built-in
    Functions](#29-find-string-length-without-built-in-functions)
30. [Check Whether a Year Is a Leap
    Year](#30-check-whether-a-year-is-a-leap-year)

------------------------------------------------------------------------

## 1. Check Whether a Number Is Prime

``` c
#include <stdio.h>

int main(void) {
    int n, i, prime = 1;

    printf("Enter a number: ");
    scanf("%d", &n);

    if (n < 2) {
        prime = 0;
    } else {
        for (i = 2; i <= n / 2; i++) {
            if (n % i == 0) {
                prime = 0;
                break;
            }
        }
    }

    if (prime)
        printf("%d is prime.\\n", n);
    else
        printf("%d is not prime.\\n", n);

    return 0;
}
```

## 2. Find the Inverse of a 2×2 Matrix

This beginner version works for a **2×2 matrix**. Its inverse exists
when the determinant is not zero.

``` c
#include <stdio.h>

int main(void) {
    float a, b, c, d, det;

    printf("Enter the 4 elements of a 2x2 matrix: ");
    scanf("%f %f %f %f", &a, &b, &c, &d);

    det = a * d - b * c;

    if (det == 0) {
        printf("Inverse does not exist.\\n");
    } else {
        printf("Inverse matrix:\\n");
        printf("%.2f  %.2f\\n", d / det, -b / det);
        printf("%.2f  %.2f\\n", -c / det, a / det);
    }

    return 0;
}
```

## 3. Find the Largest and Smallest Elements in an Array

``` c
#include <stdio.h>

int main(void) {
    int a[100], n, i, largest, smallest;

    printf("Enter number of elements (1-100): ");
    scanf("%d", &n);

    if (n < 1 || n > 100) {
        printf("Invalid size.\\n");
        return 0;
    }

    printf("Enter the elements: ");
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);

    largest = smallest = a[0];

    for (i = 1; i < n; i++) {
        if (a[i] > largest) largest = a[i];
        if (a[i] < smallest) smallest = a[i];
    }

    printf("Largest = %d\\nSmallest = %d\\n", largest, smallest);
    return 0;
}
```

## 4. Count Vowels and Consonants in Each Word

This version reads a sentence one character at a time and prints the
vowel and consonant counts for each word. It does not use string library
functions.

``` c
#include <stdio.h>

int main(void) {
    char ch;
    int vowels = 0, consonants = 0, word = 1, inWord = 0;

    printf("Enter a sentence: ");

    while ((ch = getchar()) != '\\n' && ch != EOF) {
        if (ch == ' ' || ch == '\\t') {
            if (inWord) {
                printf("Word %d: vowels = %d, consonants = %d\\n",
                       word++, vowels, consonants);
                vowels = consonants = 0;
                inWord = 0;
            }
        } else {
            inWord = 1;
            if ((ch >= 'A' && ch <= 'Z') || (ch >= 'a' && ch <= 'z')) {
                if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u' ||
                    ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U')
                    vowels++;
                else
                    consonants++;
            }
        }
    }

    if (inWord)
        printf("Word %d: vowels = %d, consonants = %d\\n",
               word, vowels, consonants);

    return 0;
}
```

## 5. Sum of the Digits of a Positive Integer

``` c
#include <stdio.h>

int main(void) {
    int n, digit, sum = 0;

    printf("Enter a positive integer: ");
    scanf("%d", &n);

    while (n > 0) {
        digit = n % 10;
        sum += digit;
        n /= 10;
    }

    printf("Sum of digits = %d\\n", sum);
    return 0;
}
```

## 6. Multiply Two Matrices

``` c
#include <stdio.h>

int main(void) {
    int a[10][10], b[10][10], c[10][10];
    int r1, c1, r2, c2, i, j, k;

    printf("Enter rows and columns of first matrix: ");
    scanf("%d %d", &r1, &c1);
    printf("Enter rows and columns of second matrix: ");
    scanf("%d %d", &r2, &c2);

    if (r1 < 1 || r1 > 10 || c1 < 1 || c1 > 10 ||
        r2 < 1 || r2 > 10 || c2 < 1 || c2 > 10 || c1 != r2) {
        printf("Invalid dimensions for multiplication.\\n");
        return 0;
    }

    printf("Enter first matrix:\\n");
    for (i = 0; i < r1; i++)
        for (j = 0; j < c1; j++)
            scanf("%d", &a[i][j]);

    printf("Enter second matrix:\\n");
    for (i = 0; i < r2; i++)
        for (j = 0; j < c2; j++)
            scanf("%d", &b[i][j]);

    for (i = 0; i < r1; i++) {
        for (j = 0; j < c2; j++) {
            c[i][j] = 0;
            for (k = 0; k < c1; k++)
                c[i][j] += a[i][k] * b[k][j];
        }
    }

    printf("Product matrix:\\n");
    for (i = 0; i < r1; i++) {
        for (j = 0; j < c2; j++)
            printf("%d ", c[i][j]);
        printf("\\n");
    }

    return 0;
}
```

## 7. Copy a String Without Built-in Functions

``` c
#include <stdio.h>

int main(void) {
    char source[100], copy[100];
    int i = 0;

    printf("Enter a word (no spaces): ");
    scanf("%99s", source);

    while (source[i] != '\\0') {
        copy[i] = source[i];
        i++;
    }
    copy[i] = '\\0';

    printf("Copied string = %s\\n", copy);
    return 0;
}
```

## 8. Binary Search in a Sorted Array

The array must be sorted in ascending order.

``` c
#include <stdio.h>

int main(void) {
    int a[100], n, key, low, high, mid, i, found = 0;

    printf("Enter number of sorted elements (1-100): ");
    scanf("%d", &n);

    if (n < 1 || n > 100) {
        printf("Invalid size.\\n");
        return 0;
    }

    printf("Enter elements in ascending order: ");
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);

    printf("Enter element to search: ");
    scanf("%d", &key);

    low = 0;
    high = n - 1;

    while (low <= high) {
        mid = low + (high - low) / 2;

        if (a[mid] == key) {
            printf("Found at position %d\\n", mid + 1);
            found = 1;
            break;
        } else if (a[mid] < key) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }

    if (!found)
        printf("Element not found.\\n");

    return 0;
}
```

## 9. Check Whether a Number Is a Palindrome

``` c
#include <stdio.h>

int main(void) {
    int n, original, digit, reverse = 0;

    printf("Enter a non-negative integer: ");
    scanf("%d", &n);

    if (n < 0) {
        printf("Not a palindrome.\\n");
        return 0;
    }

    original = n;
    while (n > 0) {
        digit = n % 10;
        reverse = reverse * 10 + digit;
        n /= 10;
    }

    if (original == reverse)
        printf("Palindrome number.\\n");
    else
        printf("Not a palindrome number.\\n");

    return 0;
}
```

## 10. Print a Diamond Pattern

``` c
#include <stdio.h>

int main(void) {
    int n, i, j;

    printf("Enter half-height of diamond: ");
    scanf("%d", &n);

    if (n < 1 || n > 50) {
        printf("Enter a value from 1 to 50.\\n");
        return 0;
    }

    for (i = 1; i <= n; i++) {
        for (j = i; j < n; j++) printf(" ");
        for (j = 1; j <= 2 * i - 1; j++) printf("*");
        printf("\\n");
    }

    for (i = n - 1; i >= 1; i--) {
        for (j = i; j < n; j++) printf(" ");
        for (j = 1; j <= 2 * i - 1; j++) printf("*");
        printf("\\n");
    }

    return 0;
}
```

## 11. Transpose a Matrix

``` c
#include <stdio.h>

int main(void) {
    int a[10][10], r, c, i, j;

    printf("Enter rows and columns (max 10 each): ");
    scanf("%d %d", &r, &c);

    if (r < 1 || r > 10 || c < 1 || c > 10) {
        printf("Invalid dimensions.\\n");
        return 0;
    }

    printf("Enter matrix elements:\\n");
    for (i = 0; i < r; i++)
        for (j = 0; j < c; j++)
            scanf("%d", &a[i][j]);

    printf("Transpose:\\n");
    for (j = 0; j < c; j++) {
        for (i = 0; i < r; i++)
            printf("%d ", a[i][j]);
        printf("\\n");
    }

    return 0;
}
```

## 12. Factorial Using Recursion

``` c
#include <stdio.h>

long long factorial(int n) {
    if (n <= 1)
        return 1;
    return n * factorial(n - 1);
}

int main(void) {
    int n;

    printf("Enter a number (0-20): ");
    scanf("%d", &n);

    if (n < 0 || n > 20) {
        printf("Please enter a number from 0 to 20.\\n");
    } else {
        printf("Factorial = %lld\\n", factorial(n));
    }

    return 0;
}
```

## 13. Check Whether a Number Is an Armstrong Number

This program supports non-negative integers and works by counting the
digits first.

``` c
#include <stdio.h>

int main(void) {
    int n, original, temp, digits = 0, digit, i;
    long long sum = 0, power;

    printf("Enter a non-negative integer: ");
    scanf("%d", &n);

    if (n < 0) {
        printf("Not an Armstrong number.\\n");
        return 0;
    }

    original = n;
    temp = n;

    do {
        digits++;
        temp /= 10;
    } while (temp > 0);

    temp = n;
    do {
        digit = temp % 10;
        power = 1;
        for (i = 0; i < digits; i++)
            power *= digit;
        sum += power;
        temp /= 10;
    } while (temp > 0);

    if (sum == original)
        printf("Armstrong number.\\n");
    else
        printf("Not an Armstrong number.\\n");

    return 0;
}
```

## 14. Selection Sort

``` c
#include <stdio.h>

int main(void) {
    int a[100], n, i, j, minIndex, temp;

    printf("Enter number of elements (1-100): ");
    scanf("%d", &n);

    if (n < 1 || n > 100) {
        printf("Invalid size.\\n");
        return 0;
    }

    printf("Enter elements: ");
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);

    for (i = 0; i < n - 1; i++) {
        minIndex = i;
        for (j = i + 1; j < n; j++) {
            if (a[j] < a[minIndex])
                minIndex = j;
        }
        temp = a[i];
        a[i] = a[minIndex];
        a[minIndex] = temp;
    }

    printf("Sorted array: ");
    for (i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\\n");

    return 0;
}
```

## 15. Sum of Diagonal Elements of a Matrix

This program adds the main diagonal of a square matrix.

``` c
#include <stdio.h>

int main(void) {
    int a[10][10], n, i, j, sum = 0;

    printf("Enter order of square matrix (1-10): ");
    scanf("%d", &n);

    if (n < 1 || n > 10) {
        printf("Invalid size.\\n");
        return 0;
    }

    printf("Enter matrix elements:\\n");
    for (i = 0; i < n; i++)
        for (j = 0; j < n; j++)
            scanf("%d", &a[i][j]);

    for (i = 0; i < n; i++)
        sum += a[i][i];

    printf("Sum of main diagonal = %d\\n", sum);
    return 0;
}
```

## 16. Bubble Sort

``` c
#include <stdio.h>

int main(void) {
    int a[100], n, i, j, temp;

    printf("Enter number of elements (1-100): ");
    scanf("%d", &n);

    if (n < 1 || n > 100) {
        printf("Invalid size.\\n");
        return 0;
    }

    printf("Enter elements: ");
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);

    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - 1 - i; j++) {
            if (a[j] > a[j + 1]) {
                temp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = temp;
            }
        }
    }

    printf("Sorted array: ");
    for (i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\\n");

    return 0;
}
```

## 17. Display a Student's Grade

``` c
#include <stdio.h>

int main(void) {
    int marks;

    printf("Enter marks (0-100): ");
    scanf("%d", &marks);

    if (marks < 0 || marks > 100) {
        printf("Invalid marks.\\n");
    } else if (marks >= 90) {
        printf("Grade A\\n");
    } else if (marks >= 75) {
        printf("Grade B\\n");
    } else if (marks >= 60) {
        printf("Grade C\\n");
    } else if (marks >= 40) {
        printf("Grade D\\n");
    } else {
        printf("Grade F (Fail)\\n");
    }

    return 0;
}
```

## 18. Arrange Characters of a String in Ascending Order

This sorts characters by their character codes. It does not use string
library functions and accepts a single word.

``` c
#include <stdio.h>

int main(void) {
    char s[100], temp;
    int i, j, length = 0;

    printf("Enter a word (no spaces): ");
    scanf("%99s", s);

    while (s[length] != '\\0')
        length++;

    for (i = 0; i < length - 1; i++) {
        for (j = 0; j < length - 1 - i; j++) {
            if (s[j] > s[j + 1]) {
                temp = s[j];
                s[j] = s[j + 1];
                s[j + 1] = temp;
            }
        }
    }

    printf("Characters in ascending order: %s\\n", s);
    return 0;
}
```

## 19. Check Whether a Number Is Even or Odd

``` c
#include <stdio.h>

int main(void) {
    int n;

    printf("Enter an integer: ");
    scanf("%d", &n);

    if (n % 2 == 0)
        printf("Even number.\\n");
    else
        printf("Odd number.\\n");

    return 0;
}
```

## 20. Find the Largest of Three Numbers

``` c
#include <stdio.h>

int main(void) {
    int a, b, c, largest;

    printf("Enter three numbers: ");
    scanf("%d %d %d", &a, &b, &c);

    if (a >= b && a >= c)
        largest = a;
    else if (b >= a && b >= c)
        largest = b;
    else
        largest = c;

    printf("Largest = %d\\n", largest);
    return 0;
}
```

## 21. Swap Two Numbers Using a Temporary Variable

``` c
#include <stdio.h>

int main(void) {
    int a, b, temp;

    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);

    temp = a;
    a = b;
    b = temp;

    printf("After swapping: a = %d, b = %d\\n", a, b);
    return 0;
}
```

## 22. Sum of the First N Natural Numbers

``` c
#include <stdio.h>

int main(void) {
    int n, i;
    long long sum = 0;

    printf("Enter N: ");
    scanf("%d", &n);

    if (n < 0) {
        printf("Enter a non-negative number.\\n");
        return 0;
    }

    for (i = 1; i <= n; i++)
        sum += i;

    printf("Sum = %lld\\n", sum);
    return 0;
}
```

## 23. Print a Multiplication Table

``` c
#include <stdio.h>

int main(void) {
    int n, i;

    printf("Enter a number: ");
    scanf("%d", &n);

    for (i = 1; i <= 10; i++)
        printf("%d x %d = %d\\n", n, i, n * i);

    return 0;
}
```

## 24. Reverse the Digits of an Integer

``` c
#include <stdio.h>

int main(void) {
    int n, digit;
    long long reverse = 0;

    printf("Enter an integer: ");
    scanf("%d", &n);

    while (n != 0) {
        digit = n % 10;
        reverse = reverse * 10 + digit;
        n /= 10;
    }

    printf("Reversed number = %lld\\n", reverse);
    return 0;
}
```

## 25. Generate the Fibonacci Series

This prints the first N terms, starting with 0 and 1.

``` c
#include <stdio.h>

int main(void) {
    int n, i;
    long long first = 0, second = 1, next;

    printf("Enter number of terms (1-90): ");
    scanf("%d", &n);

    if (n < 1 || n > 90) {
        printf("Enter a value from 1 to 90.\\n");
        return 0;
    }

    for (i = 1; i <= n; i++) {
        printf("%lld ", first);
        next = first + second;
        first = second;
        second = next;
    }
    printf("\\n");

    return 0;
}
```

## 26. Find the Sum and Average of Array Elements

``` c
#include <stdio.h>

int main(void) {
    int a[100], n, i;
    long long sum = 0;
    double average;

    printf("Enter number of elements (1-100): ");
    scanf("%d", &n);

    if (n < 1 || n > 100) {
        printf("Invalid size.\\n");
        return 0;
    }

    printf("Enter elements: ");
    for (i = 0; i < n; i++) {
        scanf("%d", &a[i]);
        sum += a[i];
    }

    average = (double)sum / n;
    printf("Sum = %lld\\nAverage = %.2f\\n", sum, average);
    return 0;
}
```

## 27. Linear Search in an Array

``` c
#include <stdio.h>

int main(void) {
    int a[100], n, key, i, found = 0;

    printf("Enter number of elements (1-100): ");
    scanf("%d", &n);

    if (n < 1 || n > 100) {
        printf("Invalid size.\\n");
        return 0;
    }

    printf("Enter elements: ");
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);

    printf("Enter element to search: ");
    scanf("%d", &key);

    for (i = 0; i < n; i++) {
        if (a[i] == key) {
            printf("Found at position %d\\n", i + 1);
            found = 1;
            break;
        }
    }

    if (!found)
        printf("Element not found.\\n");

    return 0;
}
```

## 28. Add Two Matrices

``` c
#include <stdio.h>

int main(void) {
    int a[10][10], b[10][10], sum[10][10];
    int r, c, i, j;

    printf("Enter rows and columns (max 10 each): ");
    scanf("%d %d", &r, &c);

    if (r < 1 || r > 10 || c < 1 || c > 10) {
        printf("Invalid dimensions.\\n");
        return 0;
    }

    printf("Enter first matrix:\\n");
    for (i = 0; i < r; i++)
        for (j = 0; j < c; j++)
            scanf("%d", &a[i][j]);

    printf("Enter second matrix:\\n");
    for (i = 0; i < r; i++)
        for (j = 0; j < c; j++)
            scanf("%d", &b[i][j]);

    printf("Sum matrix:\\n");
    for (i = 0; i < r; i++) {
        for (j = 0; j < c; j++) {
            sum[i][j] = a[i][j] + b[i][j];
            printf("%d ", sum[i][j]);
        }
        printf("\\n");
    }

    return 0;
}
```

## 29. Find String Length Without Built-in Functions

This example accepts a single word, then counts its characters using a
loop.

``` c
#include <stdio.h>

int main(void) {
    char s[100];
    int length = 0;

    printf("Enter a word (no spaces): ");
    scanf("%99s", s);

    while (s[length] != '\\0')
        length++;

    printf("Length = %d\\n", length);
    return 0;
}
```

## 30. Check Whether a Year Is a Leap Year

A year is a leap year if it is divisible by 400, or divisible by 4 but
not by 100.

``` c
#include <stdio.h>

int main(void) {
    int year;

    printf("Enter a year: ");
    scanf("%d", &year);

    if (year % 400 == 0 || (year % 4 == 0 && year % 100 != 0))
        printf("%d is a leap year.\\n", year);
    else
        printf("%d is not a leap year.\\n", year);

    return 0;
}
```

------------------------------------------------------------------------

**Beginner tip:** Save each program in its own `.c` file and compile/run
it separately. The contents links at the top jump to each program
heading in Markdown viewers that support heading anchors.
