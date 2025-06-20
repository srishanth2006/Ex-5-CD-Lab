# Ex-5-RECOGNITION-OF-THE-GRAMMAR-anb-where-n-10-USING-YACC
### NAME:SRISHANTH J
### REG NO:212223240160
# Date : 11\05\25
RECOGNITION OF THE GRAMMAR(anb where n>=10) USING YACC

# Aim:
To write a YACC program to recognize the grammar anb where n>=10.
# ALGORITHM
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the variables a and b.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
6.	Compile the yacc program with yacc compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
7.	Compile these with the C compiler as gcc lex.yy.c y.tab.c
8.	Enter a string as input and it is identified as valid or invalid.
# PROGRAM:

Grammar.l:
```
%{
#include "y.tab.h"
%}

%%
a    { return A; }  // Recognize 'a' as token A
b    { return B; }  // Recognize 'b' as token B
.    { return 0; }  // End of input
%%

int yywrap() {
    return 1;
}
```

Grammar.y:
```
%{
#include <stdio.h>
int yylex(void);
void yyerror(const char *s);
%}

%token A B

%%
S   : A A A A A A A A A A B    { printf("Valid string\n"); }
    | A S B                    { printf("Valid string\n"); }
    ;

%%

int main() {
    printf("Enter a string:\n");
    yyparse();
    return 0;
}

void yyerror(const char *s) {
    printf("Invalid string\n");
}
```

# OUTPUT
![Screenshot 2025-05-15 151633](https://github.com/user-attachments/assets/df5e6f3f-2c76-4b16-92fd-d0525c30c39b)




# RESULT
The YACC program to recognize the grammar anb where n>=10 is executed successfully and the output is verified.
