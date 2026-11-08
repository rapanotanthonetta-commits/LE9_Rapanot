
#include <stdio.h>
#include <stdlib.h>

int main()
{
    FILE *fp;
    char name[100];
    int age, i, students;
    char course[100];
    char line[200];

    // Create and write student records
    fp = fopen("student_records.txt", "w");

    if (fp == NULL)
    {
        printf("Error opening file!\n");
        return 1;
    }

    printf("Writing Student Database:\n");
    printf("How many students do you want to record? ");
    scanf("%d", &students);

    for (i = 1; i <= students; i++)
    {
        printf("\nStudent %d\n", i);

        printf("Enter Name: ");
        scanf(" %[^\n]", name);

        printf("Enter Age: ");
        scanf("%d", &age);

        printf("Enter Course: ");
        scanf(" %[^\n]", course);

        fprintf(fp, "Student %d\n", i);
        fprintf(fp, "Name: %s\n", name);
        fprintf(fp, "Age: %d\n", age);
        fprintf(fp, "Course: %s\n", course);
        fprintf(fp, "--------------------\n");
    }

    fclose(fp);

    printf("\nStudent database successfully saved to file.\n");

    // Read student records
    fp = fopen("student_records.txt", "r");

    if (fp == NULL)
    {
        printf("Error reading file!\n");
        return 1;
    }

    printf("\nReading Student Database:\n\n");

    while (fgets(line, sizeof(line), fp) != NULL)
    {
        printf("%s", line);
    }

    fclose(fp);

    return 0;
}


