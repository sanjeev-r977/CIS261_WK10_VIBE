# Sanjeev Rana Magar
# CIS261
# Week 10 VIBE Coding
# Student Grade Calculator

# VIBE assisted with creating and testing the grade calculation functions.
# VIBE assisted with adding student search and class statistics.
# VIBE assisted with adding file save/load functions and testing persistence.


def calculate_average(test1, test2, test3):
    average = (test1 + test2 + test3) / 3
    return average


def calculate_letter_grade(average):
    if average >= 90:
        grade = "A"
    elif average >= 80:
        grade = "B"
    elif average >= 70:
        grade = "C"
    elif average >= 60:
        grade = "D"
    else:
        grade = "F"

    return grade


def display_all_students(students):
    print("\n" + "=" * 85)
    print("ALL STUDENT RECORDS")
    print("=" * 85)

    print(
        f"{'Name':<20}"
        f"{'ID':<10}"
        f"{'Test 1':<10}"
        f"{'Test 2':<10}"
        f"{'Test 3':<10}"
        f"{'Average':<10}"
        f"{'Grade':<5}"
    )

    print("-" * 85)

    for student in students:
        print(
            f"{student['name']:<20}"
            f"{student['id']:<10}"
            f"{student['test1']:<10.2f}"
            f"{student['test2']:<10.2f}"
            f"{student['test3']:<10.2f}"
            f"{student['average']:<10.2f}"
            f"{student['grade']:<5}"
        )

    print("=" * 85)


def display_statistics(students):
    averages = [student["average"] for student in students]

    highest_average = max(averages)
    lowest_average = min(averages)
    class_average = sum(averages) / len(averages)

    print("\n" + "=" * 50)
    print("CLASS STATISTICS")
    print("=" * 50)
    print(f"Highest Average: {highest_average:.2f}")
    print(f"Lowest Average: {lowest_average:.2f}")
    print(f"Class Average: {class_average:.2f}")
    print("=" * 50)


def search_student_by_name(students):
    search_name = input("\nEnter student name to search: ")

    found = False

    for student in students:
        if student["name"].lower() == search_name.lower():
            print("\n" + "=" * 50)
            print("STUDENT FOUND")
            print("=" * 50)
            print(f"Name: {student['name']}")
            print(f"Student ID: {student['id']}")
            print(f"Test 1: {student['test1']:.2f}")
            print(f"Test 2: {student['test2']:.2f}")
            print(f"Test 3: {student['test3']:.2f}")
            print(f"Average: {student['average']:.2f}")
            print(f"Letter Grade: {student['grade']}")
            print("=" * 50)

            found = True

    if found == False:
        print("\nNo matching student found.")


def save_students_to_file(students, filename):
    try:
        with open(filename, "w") as file:
            for student in students:
                line = (
                    f"{student['name']}|"
                    f"{student['id']}|"
                    f"{student['test1']:.2f}|"
                    f"{student['test2']:.2f}|"
                    f"{student['test3']:.2f}|"
                    f"{student['average']:.2f}|"
                    f"{student['grade']}\n"
                )

                file.write(line)

        print(f"\nSaved {len(students)} student record(s) to {filename}.")

    except Exception as e:
        print(f"\nError saving student records: {e}")


def load_students_from_file(filename):
    students = []

    try:
        with open(filename, "r") as file:
            for line in file:
                line = line.strip()

                if line:
                    parts = line.split("|")

                    student = {
                        "name": parts[0],
                        "id": parts[1],
                        "test1": float(parts[2]),
                        "test2": float(parts[3]),
                        "test3": float(parts[4]),
                        "average": float(parts[5]),
                        "grade": parts[6]
                    }

                    students.append(student)

        print(f"Loaded {len(students)} student record(s).")

    except FileNotFoundError:
        print("No previous student grade file found.")
        print("Starting with an empty student list.")

    except Exception as e:
        print(f"Error loading student records: {e}")

    return students


def main():
    filename = "student_grades.txt"

    students = load_students_from_file(filename)

    print("\n" + "=" * 50)
    print("STUDENT GRADE CALCULATOR")
    print("=" * 50)
    print("Enter student information when prompted.")
    print("Type ESC as the student name when finished.")
    print("=" * 50)

    while True:
        name = input("Enter student name (or ESC to exit): ")

        if name.upper() == "ESC":
            break

        student_id = input("Enter student ID: ")

        test1 = float(input("Enter Test 1 score: "))
        test2 = float(input("Enter Test 2 score: "))
        test3 = float(input("Enter Test 3 score: "))

        average = calculate_average(
            test1,
            test2,
            test3
        )

        grade = calculate_letter_grade(average)

        student = {
            "name": name,
            "id": student_id,
            "test1": test1,
            "test2": test2,
            "test3": test3,
            "average": average,
            "grade": grade
        }

        students.append(student)

        print("\nStudent record added.")
        print(f"Average: {average:.2f}")
        print(f"Letter Grade: {grade}")
        print()

    save_students_to_file(
        students,
        filename
    )

    if len(students) > 0:
        display_all_students(students)

        display_statistics(students)

        search_choice = input(
            "\nWould you like to search for a student? (yes/no): "
        )

        if search_choice.lower() == "yes":
            search_student_by_name(students)

    print("\nThank you for using the Student Grade Calculator.")


main()
