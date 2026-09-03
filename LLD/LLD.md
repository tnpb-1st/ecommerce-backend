# E-commerce System

## Requirements
### Functional Requirements (what a system do?)
* User authentication: Allow users to sign up, log in, and manage their profiles.
* Product catalog: Users should be able to browse and search for products.
* Cart: Users can add, update, or remove items from the shopping cart.
* Checkout: Handle billing information, delivery address, and payment.

### Nonfunctional requirements:
* Performance: The website should load quickly to provide a smooth experience to customers.
* Security: Implement strong security measures and payment processing to protect user data and transactions.
* Availability: The website should be accessible anytime.
* Fault tolerance: Recover from failures without affecting the user experience.

## High Level Description
### User
As a user i am able to login in the site, browse for products on the Catalog, see the products details, add and remove a product to the cart as i wish, proceed to checkout, select my address, select my credit card and then proceed to checkout.

As a user i am able to add/remove addresses and credit cards. I am also able to see my past orders.

### Product
A product must be shown in the system. It can be added to the cart if there is the amount wanted by the user available on its stock.

### Cart
A user can select one or more items from the catalog, add them to the cart if there is an amount available on stock and it can remove at most the quantity of items added on the cart. Each time a user adds an item to the cart, the price is dinamycally calculated. A user can choose to close the cart if has at least one item and proceed to checkout.

### Catalog
A user can see any available item on the system on the catalog. It can then select an item from the catalog to see it in details and the user can add it to the cart.

### Checkout
A user can enter the checkout page once he chooses to close the cart. The user must select an address and a credit cart at the checkout page. If the user has not an address or a credit card, he must create it. Once everything is setup the user can proceed to place an order.

### Adress
A user can have multiple addresses on its account. An address can be added or deleted by the user. A checkout must have an adress before the user can proceed to place an order.

### Credit Card
A user can have multiple credit cards on its wallet. A credit card can be added or deleted on the wallet by the user. A checkout must have an address before the user can proceed to place an order.

### Wallet
A wallet is associated with only one user and a user has only one wallet. A wallet can have multiple credit cards.

### Order
A user can place a order once he finishes the checkout. The Order then triggers the payment method and goes to the pending state while the payment method is not confirmed. Once the payment method is confirmed, the order receives a notification and goes to shipping state. If a certain time passes and the payment method is not confirmed, the order goes to declined and the products have their quantities reserved for the order replenished.

## Entities
I will exclude getters and setters from this definition
### User
* ID
* e-mail
* password

System
* createdAt
* UpdatedAt
* lastLogin

### Wallet
* ID

FKs
* UserID

System
* createdAt
* UpdatedAt

### Credit Card
* ID
* Card Number
* Card Name
* ExpireDay
* ExpireMonth
* CVV

FKs
* WalletID

System
* createdAt
* UpdatedAt

### Product
* ID
* Stock
* Description
* UnitPrice

System
* createdAt
* UpdatedAt

### OrderProduct
* Quantity

FKs
* ProductID
* CartID

### Cart
* ID

FK
* checkoutID

System
* createdAt
* UpdatedAt

### Checkout
* ID

FKs
* userID
* addressID
* creditCardID

System
* createdAt
* UpdatedAt

### Order
* ID
* orderStatus

FKs
* userID
* checkoutID

System
* createdAt
* UpdatedAt