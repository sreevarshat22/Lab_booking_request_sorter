# Lab Booking Request Sorter

## About the Project

This project is a simple Python program that helps to sort and check lab booking requests.

The requests are taken as sample data in the Python program. AI can also be used to extract the booking details from the request.

The program checks whether the request has the required details and whether the lab is available.

The final booking is only a tentative suggestion. The lab in-charge has to confirm the booking.

## What the Project Does

The program checks:

- Lab name
- Date
- Time slot
- Number of students
- Missing information
- Lab capacity
- Sunday requests
- Already booked labs
- Conflicting requests

## Labs Used

| Lab Code | Lab Name | Capacity |
|----------|----------|----------|
| LAB1 | Python Lab 1 | 60 |
| LAB3 | AI Lab | 40 |
| LAB5 | Seminar Hall | 120 |

## Time Slots

- FN = Morning (09:00 AM - 12:30 PM)
- AN = Afternoon (01:30 PM - 04:30 PM)

## How to Run

First open the project folder in the terminal.

Run the normal demo:

    python main.py

This runs the project using the saved sample details.

For using real AI:

    python main.py --ai

For AI mode, the Gemini API key must be set first.

## Output Files

After running the program, four files are created:

### 1. results.csv

This contains all the requests with their extracted details, status and reason.

### 2. schedule.csv

This contains the requests that are currently available.

These are only tentative bookings.

### 3. issues.csv

This contains requests that have some problem, such as:

- Missing information
- Over capacity
- Sunday
- Booking conflict

### 4. summary.txt

This gives a small summary of the results.

It shows the number of requests under each status and lab.

## Status Used

The program can give the following statuses:

- `available` - The request can be tentatively scheduled.
- `needs_more_info` - Some required information is missing.
- `lab_closed` - The request is on Sunday.
- `over_capacity` - The number of students is more than the lab capacity.
- `conflict` - The lab is already booked for that date and slot.

## AI Part

The AI is used to read a normal sentence and extract:

- Lab
- Date
- Slot
- Number of students
- Short summary

For example:

"Python Lab 1 on 15 October afternoon for 55 students"

can be converted into:

```json
{
  "lab": "LAB1",
  "date": "2026-10-15",
  "slot": "AN",
  "students": 55,
  "summary": "Lab practice"
}
