# django-1
All Topics regarding Django 

home.html
<!DOCTYPE html>

<html>

<head>

    <title>Home</title>

</head>

<body>

    <h1>Invoice Form</h1>

    <form method="post" action="{% url 'home' %}">

        {% csrf_token %}

        <label for="vendor_client">Vendor/Client:</label>

        <select name="vendor_client" id="vendor_client">

            <option value="Vendor">Vendor</option>

            <option value="Client">Client</option>

        </select>

        <br><br>

        <label for="vendor_client_id">Vendor/Client ID:</label>

        <input type="text" name="vendor_client_id" id="vendor_client_id" required>

        <br><br>

        <label for="email">Email:</label>

        <input type="email" name="email" id="email" required>

        <br><br>

        <label for="contact_no">Contact No:</label>

        <input type="tel" name="contact_no" id="contact_no" required pattern="[0-9]{10}">

        <br><br>

        <label for="product_name">Product Name:</label>

        <input type="text" name="product_name" id="product_name" required>

        <br><br>

        <label for="quantity">Quantity:</label>

        <input type="number" name="quantity" id="quantity" required>

        <br><br>

        <label for="product_cost">Product Cost:</label>

        <input type="number" name="product_cost" id="product_cost" step="0.01" required>

        <br><br>

        <label for="location">Location:</label>

        <input type="text" name="location" id="location" required>

        <br><br>

        <label for="delivery_date">Delivery Date:</label>

        <input type="date" name="delivery_date" id="delivery_date" required min="{{ today }}">

        <br><br>

        <input type="submit" value="Submit">

        <input type="reset" value="Reset">

    </form>

    <br>

    <a href="{% url 'invoice_list' %}">View Invoices</a>

    <br>

    <a href="{% url 'admin:index' %}">Go to Admin</a>

</body>

</html>




invoice_list.html

<!DOCTYPE html>

<html>

<head>

    <title>Invoice List</title>

</head>

<body>

    <h1>Invoice List</h1>

    <table>

        <tr>

            <th>Invoice Number</th>

            <th>Vendor/Client</th>

            <th>Vendor/Client ID</th>

            <th>Email</th>

            <th>Contact No</th>

            <th>Product Name</th>

            <th>Quantity</th>

            <th>Product Cost</th>

            <th>Location</th>

            <th>Delivery Date</th>

        </tr>

        {% for invoice in invoices %}

        <tr>

            <td>{{ invoice.invoice_number }}</td>

            <td>{{ invoice.vendor_client }}</td>

            <td>{{ invoice.vendor_client_id }}</td>

            <td>{{ invoice.email }}</td>

            <td>{{ invoice.contact_no }}</td>

            <td>{{ invoice.product_name }}</td>

            <td>{{ invoice.quantity }}</td>

            <td>{{ invoice.product_cost }}</td>
