---
title: "Public to Private redirecting"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by ashiq_rahman on 2011-01-20
Dear All,
 
I have 2 apache2 engines on 2 separate computers, A, and B.
 A and B are on the same network.
 "A" is published to the Internet, it has public IP.
 "B" is not published, it has a private IP 192.168.1.44.
 Machine "A", login.php will get user input from the internet and then
 pass the parameters to machine "B", process.php to process the data.
 I would like to know how "A" can send the parameter to "B" ?
I cannot use <a href='http://192.168.1.44/process.php"> in login.php.
Are there any solution to do the internal redirect ?

Thanks
 Ashiq

---

### Post by SeijiSensei on 2011-01-20
One simple solution that comes to mind is to use the curl options in PHP or wget to pass the parameters in a GET request to machine B.

If you're authenticating against a database on machine B, why not simply make that the target of machine A with pg_connect() or mysql_connect()?  Just query the database directly rather than some clumsy passing of parameters between the machines.

---

