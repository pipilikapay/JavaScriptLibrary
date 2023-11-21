# Javascript Example Code

This is a simple Javascript checkout example of PipilikaPay.


### NOTE: 
#### Checkout-V1 => All response will send into webhook url with REST API CALL.

# Checkout-V1 Documents

## Step 1: Create Charge Checkout-V1

Here you will get charge response into data variable.

```bash
    function createPayment(){
      const requestBody = {
        apiKey: 'YOUR-API-KEY',
        secretkey: 'YOUR-SECRET-KEY',
        amount: '100',
        fullname: 'Nobody',
        email: 'nobody@gmail.com',
        metadata: {
          customerID: '54634635634',
          orderID: '65443443',
        },
        successurl: 'https://your-domain.com/success.php',
        cancelurl: 'https://your-domain.com/cancel.php',
        webhookUrl: 'https://your-domain.com/webhook.php',
      };

      // Fetch API POST request
      fetch('https://pay.your-domain.com/payment/api/create_payment', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(requestBody),
      })
        .then((response) => response.json())
        .then((data) => {
          console.log('Received JSON response:', data);
          // Handle the JSON response here
        })
        .catch((error) => {
          console.error('Error:', error);
        });

    }

```


## Checkout-V1 Charge Response Example:

```bash
[ 
    {
      "status": "success",
      "paymentID": "54646345345",
      "paymentURL": "https://pay.your-domain.com/payment/portal?ref=34645634634635"
    }
]
```


## Step 2: Complete Payment

## Step 3: Get Response & Verify Payment

Here you will get webhook response into data variable.

```bash
    function verifyPayment(){
      const requestBody = {
        apiKey: 'YOUR-API-KEY',
        secretkey: 'YOUR-SECRET-KEY',
        paymentID: '756447566',
      };

      // Fetch API POST request
      fetch('https://pay.your-domain.com/payment/api/verify_payment', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(requestBody),
      })
        .then((response) => response.json())
        .then((data) => {
          console.log('Received JSON response:', data);
          // Handle the JSON response here
        })
        .catch((error) => {
          console.error('Error:', error);
        });

    }
```

## Checkout-V1 Webhook Response Example:
```bash
    {
      "status": "success",
      "paymentID": "324523452345243",
      "PaymentStatus": "Completed"
    }
```

Enjoy