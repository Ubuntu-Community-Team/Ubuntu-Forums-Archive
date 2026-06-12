---
title: "Another Apache running..."
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by TideMan on 2009-07-09
Have a look at this:
```
derek@Athlon1700:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.1...
XAMPP: Another web server daemon is already running.
XAMPP: Starting MySQL...
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.

```

I was playing around trying to install MySQL only to find that it was already available in XAMPP.
But in the process, I appear to have screwed up my Apache and FTP daemons that were running perfectly before.  I now seem to have them running outside of XAMPP.
How can I fix this?

---

### Post by ewankho on 2009-07-09
Can't you just start MySQL only: /opt/lampp/lampp startmysql

---

### Post by TideMan on 2009-07-09
Yes, MySQL starts, but the Apache that is running is not the Apache from XAMMP, but one from somewhere else.  This means that localhost is different from the one that I've set up for MySQL.

What I need to do is somehow stop the other Apache.

Just to clarify this.  Here is what happens when I stop XAMPP
> derek@Athlon1700:~$ sudo /opt/lampp/lampp stop
Stopping XAMPP for Linux 1.7.1...
XAMPP: XAMPP-Apache is not running.
XAMPP: XAMPP-MySQL is not running.
XAMPP: XAMPP-ProFTPD is not running.
XAMPP stopped.


Then when I try to start it again:
> derek@Athlon1700:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.1...
XAMPP: Another web server daemon is already running.
XAMPP: Starting MySQL...
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.


So, my question is: how do I stop the other web server daemon running, so that I can run the XAMPP Apache?

---

### Post by TideMan on 2009-07-09
Hey!!
I solved it simply by removing Apache using Synaptic Package Manager.
While playing around installing MySQL, I must have inadvertently installed Apache as well and that over-rode the XAMPP Apache.

---

### Post by DominaDoom on 2009-11-11
> **TideMan said:**
> Hey!!
I solved it simply by removing Apache using Synaptic Package Manager.
While playing around installing MySQL, I must have inadvertently installed Apache as well and that over-rode the XAMPP Apache.

I had to manually search Synaptic as well and removed Apache and MySQL packages, but I am failing to see the [http://localhost/xampp/](http://localhost/xampp/) redirect page from [http://localhost/](http://localhost/).  I see the Index.html file which reads "It Works" on the screen at [http://localhost/](http://localhost/).  The Index.html file is in the /var/www directory.

---

