#include <stdio.h>
#include <string.h>
int stringLength(char s[]) {
    int i = 0;
    while (s[i]) i++;
    return i;
}
void stringCopy(char d[], char s[]) {
    int i = 0;
    while (s[i]) {
        d[i] = s[i];
        i++;
    }
    d[i] = '\0';
}
void stringConcat(char s1[], char s2[]) {
    int i = stringLength(s1), j = 0;
    while (s2[j]) {
        s1[i++] = s2[j++];
    }
    s1[i] = '\0';
}
int isAlpha(char str[]) {
    int i = 0;
    while (str[i]) {
        if (!((str[i] >= 'A' && str[i] <= 'Z') || (str[i] >= 'a' && str[i] <= 'z')))
            return 0;
        i++;
    }
    return 1;
}
int isDigit(char str[]) {
    int i = 0;
    while (str[i]) {
        if (!(str[i] >= '0' && str[i] <= '9'))
            return 0;
        i++;
    }
    return 1;
}
int main() {
    char firstName[30], lastName[30], roll[15], studentID[100];
    int i, j;
    printf("Enter First Name: ");
    scanf("%s", firstName);
    while (!isAlpha(firstName)) {
        printf("Invalid. Enter alphabets only: ");
        scanf("%s", firstName);
    }
 printf("Enter Last Name: ");
    scanf("%s", lastName);
 while (!isAlpha(lastName)) {
        printf("Invalid. Enter alphabets only: ");
        scanf("%s", lastName);
    }
printf("Enter Roll Number: ");
    scanf("%s", roll);

 while (!isDigit(roll)) {
        printf("Invalid. Enter digits only: ");
        scanf("%s", roll);
    }
    for (i = 0; i < 3 && firstName[i]; i++)
        studentID[i] = firstName[i];
    studentID[i] = '\0';
 for (j = 0; j < 3 && lastName[j]; j++) {
        char temp[2] = {lastName[j], '\0'};
        stringConcat(studentID, temp);
    }
  stringConcat(studentID, roll);
 printf("\nGenerated Student ID: %s\n", studentID);
  return 0;
}

