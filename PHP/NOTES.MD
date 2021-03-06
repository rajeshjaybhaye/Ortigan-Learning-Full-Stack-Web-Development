# Notes

## Syntax eg.1

A PHP script can be placed anywhere in the document.

A PHP script starts with <?php and ends with ?>:

```php
<?php
// PHP code goes here
?>
```

PHP files are saved with .php extension 

Basic "Hello World" program

Example 1.1

```php
<!DOCTYPE html>
<html>
<body>

<h1>My first PHP page</h1>

<?php
echo "Hello World!";
?>

</body>
</html>
```

> PHP statement are end with a semicolon (;)

> All keywords are not case sensitive but variable names are case sensitive

## Variables eg.2

### Declaring a variable

In PHP variable starts with the $ sign, followed by the name of the variable:

```php
<?php 
	$name = "John Doe"; 
	$num1 = 10;
	$num2 = 15.70;
?>
```

A variable can have a short name (like x and y) or a more descriptive name (age, carname, total_volume).

Rules for PHP variables:

- A variable starts with the `$` sign, followed by the name of the variable
- A variable name must start with a letter or the underscore character
- A variable name cannot start with a number
- A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and _ )
- Variable names are case-sensitive (`$age` and `$AGE` are two different variables)

> Remember PHP variable name are case sensitive

### Using a variable

The PHP echo statement is often used to output data to the screen.

Example 2.1

```php
<?php 
	$name = "John Doe";
	echo "My name is $name";
?>
```

Output

```bash
My Name is John Doe
```

Eample 2.2

```php
<?php 
	$num1 = 10;
	$num2 = 25;
	$ans = $num1 + $num2; 
	echo "The ans is $ans";
?>
```

```bash
The ans is 35
```

## Strings eg.3

Functions to manipulate string 

### strlen() - returns the length of the string

Example 3.1

```php
<?php
	echo strlen("Welcome to Ortigan Learning");
?>
```

Output

```bash
	28
```

### str_word_count() - Count Words in a String

Example 3.2

```php
<?php
    echo str_word_count("Welcome to Ortigan Learning!"); 
?>
```

Output

```bash
4
```

## Loops eg.4

Like any other language, loop in PHP is used to execute a statement or a block of statements, multiple times until and unless a specific condition is met. This helps the user to save both time and effort of writing the same code multiple times.

PHP have for loops:

1. for loop
2. while loop
3. foreach loop
4. do-while loop

### For Loop

This type of loops is used when the user knows in advance, how many times the block needs to execute. That is, the number of iterations is known beforehand. These type of loops are also known as entry-controlled loops. There are three main parameters to the code, namely the initialization, the test condition and the counter.

**Syntax**

```php
for (init counter; test counter; increment counter) {
  code to be executed for each iteration;
}
```

**Parameters**

- *init counter*: Initialize the loop counter value
- *test counter*: Evaluated for each loop iteration. If it evaluates to TRUE, the loop continues. If it evaluates to FALSE, the loop ends.
- *increment counter*: Increases the loop counter value

Example 4.1

```php
<?php 
    for ($i=0; $i < 10; $i++) { 
        echo $i+1 . "<br>";
    }
?>
```

Output

```bash
1
2
3
4
5
6
7
8
9
10
```

### While Loop

The while loop is also an entry control loop like for loops i.e., it first checks the condition at the start of the loop and if its true then it enters the loop and executes the block of statements, and goes on executing it as long as the condition holds true.

**Syntax**

```php
while (condition is true) {
  code to be executed;
}
```

Example 4.2

```php
<?php 
	$a = 0;
	while ($a <= 10) {
	    echo $a . "<br>";
	    $a++;
	}
?>
```

Output

```bash
0
1
2
3
4
5
6
7
8
9
10
```

### Foreach Loop

This loop is used to iterate over arrays. For every counter of loop, an array element is assigned and the next counter is shifted to the next element.

**Syntax**

```php
foreach ($array as $value) {
  code to be executed;
}
```

For every loop iteration, the value of the current array element is assigned to $value and the array pointer is moved by one, until it reaches the last array element.

Example 4.3

```php
<?php
	$names = array('Pranav', 'Gaurav', "Parag", 'Jayesh', 'JD');
  foreach ( $names as $name ) {
    echo $name . "<br>";
	}
?>
```

Output

```bash
Pranav
Gaurav
Parag
Jayesh
JD
```

### Do while Loop

The do while loop will always execute the block of code once, it will then check the condition, and repeat the loop while the specified condition is true.

**Syntax**

```php
do {
  code to be executed;
} while (condition is true);
```

Example 4.4

```php
<?php
    $a = 0;
    do {
    echo $a . "<br>";
    $a++;
    } while ($a <= 10);
?>
```

Output

```bash
0
1
2
3
4
5
6
7
8
9
10
```

## Form Handling eg.5

There are two ways the browser client can send information to the web server.

- The GET Method
- The POST Method

When we develop a website or a web application, we often have to create forms to take input from users, like a **Login** form or a **Registration** form.

Creating a form on the webpage is accomplished using HTML, while PHP serves as a transport for those values from the webpage to the server and then in further processing those values.

PHP provides two **superglobals** `$_GET` and `$_POST` for collecting form-data for processing.

### The GET Method

The GET method sends the encoded user information appended to the page request. The page and the encoded information are separated by the ? character.

```bash
http://www.test.com/index.htm?name1=value1&name2=value2
```

**When to use Get Method?**

- The variable names and values will be visible in URL if HTML forms submitted by the GET method.
- The GET method is restricted to send up to *2048 characters* only.
- When you submit sensitive information like passwords then should not use this method.
- GET method can't be used, to send binary data like images and Word documents.
- GET method data can be accessed using PHP QUERY_STRING environment variable.
- PHP $_GET associative array is used to access all the sent information by GET method.

Example 5.1

`Filename: form_get_5.1.html`

```html
<!doctype html>
<html lang="en">
    <head>
        <title>Title</title>
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
    </head>
    <body>
        <div class="container mt-3">
            <h2>Form Handling <br/> <small>using <b>GET</b> Method</small></h2>
            <div class="row">
                <div class="col-md-4">
                    <form action="form_get_process_5.1.php" method="get">
                        <div class="form-group">
                            <label for="Name"></label>
                            <input type="text"
                            class="form-control" name="name" id="name" aria-describedby="helpId" placeholder="">
                            <small id="" class="form-text text-muted">Name</small>
                        </div>
                        <div class="form-group">
                            
                            <label for="email"></label>
                            <input type="text"
                            class="form-control" name="email" id="email" aria-describedby="helpId" placeholder="">
                            <small id="" class="form-text text-muted">Email</small>
                        </div>
                        <div class="form-group">
                            
                            <label for="password"></label>
                            <input type="password"
                            class="form-control" name="password" id="password" aria-describedby="helpId" placeholder="">
                            <small id="" class="form-text text-muted">Password</small>
                        </div>
                        <button class="btn btn-primary" type="submit">Submit</button>
                    </form>
                </div>
            </div>
        </div>
    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.2.1.slim.min.js" integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN" crossorigin="anonymous"></script>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</body>
</html>
```

`Filename: form_get_process_5.1.php`

```php
<?php 
    $name = $_GET['name'];
    $email = $_GET['email'];
    $password = $_GET['password'];
    echo "Hello " . $name . "<br>";
    echo "Your email is ".$email;
?>
```

Output

```bash
Hello John Doe
Your email is john.doe@gmail.com
```

### The POST Method

Information sent from a form with the POST method is invisible and has no limits on the amount of information to send.

> However, there is an 8 MB max size for the POST method, by default (can be changed by setting the post_max_size in the php.ini file).

**When to use POST Method?**

- The POST method can be used to send ASCII as well as binary data.
- The data sent by POST method goes through HTTP header, so security depends on HTTP protocol. By using Secure HTTP, you can make sure that your information is secure.
- PHP $_POST associative array is used to access all the sent information by POST method.
- Variables are not visible in the URL so users can't bookmark your page.

Example 5.2

`Filename: form_post_5.2.html`

```html
<!doctype html>
<html lang="en">
    <head>
        <title>Title</title>
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
    </head>
    <body>
        <div class="container mt-3">
            <h2>Form Handling <br/> <small>using <b>POST</b> Method</small></h2>
            <div class="row">
                <div class="col-md-4">
                    <form action="form_post_process_5.2.php" method="post">
                        <div class="form-group">
                            <label for="Name"></label>
                            <input type="text"
                            class="form-control" name="name" id="name" aria-describedby="helpId" placeholder="">
                            <small id="" class="form-text text-muted">Name</small>
                        </div>
                        <div class="form-group">
                            
                            <label for="email"></label>
                            <input type="text"
                            class="form-control" name="email" id="email" aria-describedby="helpId" placeholder="">
                            <small id="" class="form-text text-muted">Email</small>
                        </div>
                        <div class="form-group">
                            
                            <label for="password"></label>
                            <input type="password"
                            class="form-control" name="password" id="password" aria-describedby="helpId" placeholder="">
                            <small id="" class="form-text text-muted">Password</small>
                        </div>
                        <button class="btn btn-primary" type="submit">Submit</button>
                    </form>
                </div>
            </div>
        </div>
    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.2.1.slim.min.js" integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN" crossorigin="anonymous"></script>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</body>
</html>
```

`Filename: form_post_process_5.2.php`

```php
<?php 
    $name = $_POST['name'];
    $email = $_POST['email'];
    $password = $_POST['password'];
    echo "Hello " . $name . "<br>";
    echo "Your email is ".$email;
?>
```

Output

```bash
Hello John Doe
Your email is john.doe@gmail.com
```