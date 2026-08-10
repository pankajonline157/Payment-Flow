# Payment-Flow
How money moves from one bank to another:

 Alice
 Bank A
   │
   │ 1. "Send $100 to Bob"
   ▼
┌──────────────────────┐
│       BANK A         │
│ Authentication       │
│ Balance check        │
│ Fraud/AML checks     │
│ Create payment       │
└──────────┬───────────┘
           │
           │ 2. Payment instruction
           ▼
┌──────────────────────┐
│ PAYMENT / CLEARING   │
│ SYSTEM                │
│                      │
│ Route + validate     │
│ payment              │
└──────────┬───────────┘
           │
           │ 3. Clearing
           ▼
┌──────────────────────┐
│   SETTLEMENT SYSTEM  │
│                      │
│ Bank A owes Bank B   │
│ $100                  │
└──────────┬───────────┘
           │
           │ 4. Settlement
           ▼
┌──────────────────────┐
│       BANK B         │
│ Validate payment     │
│ Credit Bob's account │
└──────────┬───────────┘
           │
           │ 5. Account updated
           ▼
          Bob
       + $100


1. 👤 Alice creates the transaction

Alice opens her banking app and enters:

From:       Alice's Bank A account
To:         Bob's Bank B account
Amount:     $100
Reference:  "Payment"

She presses Send.

2. 🔐 Bank A authenticates Alice

Bank A first needs to make sure the person requesting the payment is authorized.

For example:

Login
  ↓
Password / PIN
  ↓
2FA / Biometrics
  ↓
Transaction authorization

If the bank cannot authenticate Alice, the transaction is rejected.

3. 💰 Bank A checks Alice's account

Bank A checks things such as:

Available balance
       ↓
Is $100 available?
       ↓
Transaction limits
       ↓
Account restrictions

For example:

Alice's balance = $1,000
Transfer        = $100
Remaining       = $900

The bank may also consider fees.

4. 🛡️ Fraud and compliance checks

Before sending the payment onward, the bank may run automated controls.

For example:

Is this unusual?
        │
        ├── No → Continue
        │
        └── Yes → Additional review / hold

Depending on the payment and jurisdiction, checks can include fraud detection, sanctions screening, and other compliance controls.

5. 🧾 Bank A creates a payment instruction

Bank A now creates an electronic payment instruction.

Conceptually, it contains information like:

Sender:
    Alice
    Bank A

Amount:
    $100

Receiver:
    Bob
    Bank B

Payment reference:
    ABC123

The actual message format depends on the payment system.

This is important: the bank is not simply sending a physical "$100 digital file" to Bank B.

It is sending payment instructions, while the actual movement/settlement of funds happens through the relevant financial infrastructure.

6. 🌐 Payment goes to the appropriate payment network

Bank A sends the payment through the payment rail it uses.

Conceptually:

Bank A
  │
  ▼
Payment / Clearing Network
  │
  ▼
Bank B

Examples of payment infrastructure vary by country and transaction type.
