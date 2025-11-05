# Ex-5 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM

```
#include <stdio.h>
#include <string.h>
int main() {
 char str[1000];
 int rails, len;
 printf("Enter a Secret Message: ");
 fgets(str, sizeof(str), stdin);
 len = strlen(str);
 if(str[len-1] == '\n') str[len-1] = '\0'; // Remove newline
 len = strlen(str);
 printf("Enter number of rails: ");
 scanf("%d", &rails);
 int code[rails][len];
 for(int i = 0; i < rails; i++) {
 for(int j = 0; j < len; j++) {
 code[i][j] = 0;
 }
 }
 int dir = 1; // 1: moving down, -1: moving up
 int row = 0;
 for(int j = 0; j < len; j++) {
 code[row][j] = str[j];
 row += dir;
 if(row == 0 || row == rails-1) dir = -dir; // Change direction
 }
 printf("Encrypted Message: ");
 for(int i = 0; i < rails; i++) {
 for(int j = 0; j < len; j++) {
 if(code[i][j] != 0) printf("%c", code[i][j]);
 }
 }
 printf("\n");
 return 0;
}
```

# OUTPUT

<img width="1122" height="624" alt="image" src="https://github.com/user-attachments/assets/e75472d1-cd54-4707-94fc-283f7798084e" />

