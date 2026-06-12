---
title: "GAIM: connection fails on MSN protocol"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by chinaski on 2006-06-04
hi,

cannot get GAIM to work with my MSN account, it gives back a username and password error, which are correct

I can chat with aMSN with same account details, but I do not like to have many software for same purpose

also, it is not possible (as far as I know) to remove GAIM without removing other important stuff such as ubuntu-desktop

anyone experiencing same issue and maybe found a workaround?

cheers

---

### Post by cyracks on 2006-06-04
[quote=chinaski]
also, it is not possible (as far as I know) to remove GAIM without removing other important stuff such as ubuntu-desktop
[/quote] 
From ubuntu-desktop description:
[I]It is safe to remove this package if some of the desktop system
packages are not desired...[/I]

The package itself has no meaning except during the install, since it depends on a lot of other packages. So instead of installing every single package like *apt-get install acpi acpi-support acpid anacron ....* you just install ubuntu-desktop. But after that when all the packages are installed you can remove it.

---

### Post by chinaski on 2006-06-05
thank you cyracks for your explanation

so I guess I'll remove GAIM, but still I wonder why I cannot get connected

---

### Post by cyracks on 2006-06-05
I am using GAIM and have no problem connecting to MSN. 
Look at the file /home/*your-user-name*/.gaim/accounts.xml to see if you really have the right username and password.
If that doen't work try to install ethereal and check the network flow.

---

### Post by chinaski on 2006-06-05
[QUOTE=cyracks]I am using GAIM and have no problem connecting to MSN. 
Look at the file /home/*your-user-name*/.gaim/accounts.xml to see if you really have the right username and password.
[/quote]
yes they are correct :)
> 
If that doen't work try to install ethereal and check the network flow.
I'll have to learn to do it but thank you very much for the tip cyracks ;)

---

### Post by barnabas on 2006-06-05
I have also experienced not being able to log into gaim. My problem was in my /etc/resolv.conf file. I had two nameservers in there: 
1. My Router 
2. My ISP

I have to comment out the router nameserver line and save the file to be able to connect to the messaging service. Maybe you're dealing with something similar?

just try: sudo gedit /etc/resolv.conf
and check out what you have.

---

### Post by vlghltlh on 2006-09-14
Thank you barnabas! Mine wasn't working either until I tried that, finally.

---

### Post by Isoss on 2006-09-14
chinaski note that if you are behind a proxy server then you need to fill the proxy options for msn and choose http and also select HTTP Method for MSN options.

---

