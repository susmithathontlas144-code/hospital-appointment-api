# Hospital Appointment API

A Node.js + TypeScript + Prisma 7 CRUD application for managing hospital patients, doctors, and appointments.

## Features

* Patient CRUD operations
* Doctor CRUD operations
* Appointment creation and management
* Patient-doctor relationships using Prisma `connect`
* Nested relational queries using Prisma `include`
* Patient search by name
* Doctor search by specialty
* Appointment status updates
* Upcoming doctor appointments
* Database seeding with Prisma
* TypeScript test script for verifying CRUD operations

## Database Models

### Patient

* `id`
* `name`
* `email`
* `phone`
* `dateOfBirth`
* `createdAt`

### Doctor

* `id`
* `name`
* `specialty`
* `email`
* `createdAt`

### Appointment

* `id`
* `patientId`
* `doctorId`
* `appointmentDate`
* `status`
* `notes`
* `createdAt`

Appointments are related to both patients and doctors.

## Technologies

* Node.js
* TypeScript
* PostgreSQL
* Prisma 7
* Prisma PostgreSQL Adapter
* `tsx`

## Setup

Install dependencies:

```bash
npm install
```

Create a `.env` file and add the PostgreSQL connection string:

```env
DATABASE_URL="postgresql://USERNAME:PASSWORD@localhost:5432/hospital_api?schema=public"
```

Generate the Prisma Client:

```bash
npx prisma generate
```

## Database

The project uses an existing PostgreSQL database schema containing:

* `patients`
* `doctors`
* `appointments`

The Prisma schema was introspected using:

```bash
npx prisma db pull
```

The generated schema was then cleaned to follow Prisma and TypeScript naming conventions using `@map` and `@@map`.

## Seed the Database

Run:

```bash
npx prisma db seed
```

This creates sample doctors, patients, and appointments.

## Test the CRUD Operations

Run:

```bash
npx tsx src/test.ts
```

The test script verifies:

1. Creating a patient
2. Finding a patient
3. Searching patients
4. Updating a patient's phone number
5. Creating a doctor
6. Searching doctors by specialty
7. Booking an appointment
8. Fetching an appointment with patient and doctor details
9. Fetching upcoming appointments
10. Updating appointment status
11. Cleaning up test records

## Type Checking

Run:

```bash
npx tsc --noEmit
```

The project should complete without TypeScript errors.

## Project Structure

```text
hospital-appointment-api/
│
├── prisma/
│   └── schema.prisma
│
├── src/
│   ├── lib/
│   │   └── prisma.ts
│   ├── appointments.ts
│   ├── doctors.ts
│   ├── patients.ts
│   ├── seed.ts
│   └── test.ts
│
├── .gitignore
├── package.json
├── prisma7.config.ts
├── tsconfig.json
└── README.md
```

## Safety

Database credentials are stored in `.env` and should never be committed to GitHub.

The `.gitignore` file excludes:

```text
node_modules/
.env
/generated/prisma
dist/
```

## Assignment Status

* [x] PostgreSQL database created
* [x] Prisma schema introspected
* [x] Prisma schema cleaned
* [x] Patient CRUD implemented
* [x] Doctor CRUD implemented
* [x] Appointment relational CRUD implemented
* [x] Seed script implemented
* [x] Test script implemented
* [x] TypeScript compilation verified

## Verification

The CRUD test script was successfully executed and all test records were cleaned up without errors.