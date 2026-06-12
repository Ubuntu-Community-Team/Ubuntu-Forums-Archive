---
title: "LAMP - can not access my site via the internet"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by peet1909 on 2010-05-20
I've recently installed LAMP on Ubuntu desktop 10.
I can access my site through local LAN, but not via the internet.

If I try to access it using the ubuntu machine's external/internet IP address nothing loads.

The firewall is disabled.

Please help.:confused:

---

### Post by Charlietje on 2010-05-20
when your machine is connected to a router, then you need to set portforwarding in the router.
meaning: incomming trafic on port 80, forward that to an internal ip (your server)

regards

---

### Post by peet1909 on 2010-05-20
Thanks, that seem to have done the trick.

I have another problem however...
I can not add/update anything to my tables as it says it's read only.

I copied the database from another machine on to the Ubuntu machine I'm now using.

Any idea how I can change my database and tables to read and write, etc?:confused:

---

### Post by Charlietje on 2010-05-20
install phpmyadmin in your server
connect to the database
look to the privilages and adjust where neccesary

regards

---

### Post by peet1909 on 2010-05-20
I have phpmyadmin on and tried to adjust, giving it privileges but it doesn't seem to work.:(

---

### Post by Charlietje on 2010-05-20
Can you take a screenshot of your privilage page?

thanks

---

### Post by peet1909 on 2010-05-20
Here's 2 screenshots

---

### Post by Charlietje on 2010-05-20
Everythings seems ok.
What and how are you trying to do?
What are the error messages?

---

### Post by peet1909 on 2010-05-21
When I try to insert data into any table it says table is read only.:confused:

---

### Post by Charlietje on 2010-05-21
try this
```
chown mysql:mysql /var/lib/mysql/mysql/*
```

---

### Post by peet1909 on 2010-05-21
I get the error missing operand after 
mysql:mysql /var/lib/mysql/mysql/*

---

### Post by Charlietje on 2010-05-21
can you cd into that folder and then sudo chown to the folder?

---

### Post by peet1909 on 2010-05-21
I've tried that as well but the syntax seem to be wrong?

It still gives me the same error.

I do apologize - I do not know linux well at all

---

### Post by Charlietje on 2010-05-21
try this

```
chown -R mysql:mysql /var/lib/mysql/mysql/
```

---

### Post by peet1909 on 2010-05-21
The command seem to have worked (no errors) but it still says database/table is read only

---

### Post by Charlietje on 2010-05-21
maybe you should try to drop the database and re-import it

---

### Post by peet1909 on 2010-05-21
It's extremely big though.
Do you mean export to a file and then re-import?
It's going to be too big?:(

---

### Post by Charlietje on 2010-05-21
how big is big?

---

### Post by Charlietje on 2010-05-21
did you upgrade your ubunut to 10.04 or is it a clean install.
how did you import the database the first time?

---

### Post by peet1909 on 2010-05-21
Nearly 5 Gig

---

### Post by peet1909 on 2010-05-21
It's a clean install.
I copied the databases from an external drive

---

