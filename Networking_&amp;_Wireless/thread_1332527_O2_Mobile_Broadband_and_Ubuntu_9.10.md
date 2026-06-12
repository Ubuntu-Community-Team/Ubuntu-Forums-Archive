---
title: "O2 Mobile Broadband and Ubuntu 9.10"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by Cheltspy on 2009-11-20
I cannot get Ubuntu 9.10 to connect to O2 mobile broadband pay as you go
 
I have an unlocked E160 and K3520 sticks.
 
Both connect using a Vodafone sim fine.
 
Yet the O2 sim with the correct apn,user and password will not connect.
 
It worked fine with 9.04 yet with 9.10 it immediately disconnects. 
 
I am using
m-bb.o2.co.uk
o2bb
password
 
which work under windows and a 3G router. 
 
I am really stuck :confused:

---

### Post by pdc on 2009-11-20
many have reported problems with 9.10; whereas they reported no problems with 9.04;

options:

1) reinstall 9.04
2) wait for Ubuntu experts to fix

3) don't install new software immediately; new software may well have problems; the circumspect wait 2-3 months for folks like yourself to report issues (and have someone else fix them)

---

### Post by Cheltspy on 2009-11-21
Found a work around

When you create a new mobile broadband DO NOT select any provider from list but manually enter the details.

Enter the correct APN name

Enter the Usename
Enter the Password
Then appy

Try and connect with it.

If it fails

Go back and edit the connect and put a space before APN name and after it.

appy

try and connect with it. It should fail (of course)

Go back and remove the spaces before and after the APN name and connect.

This seems to have got me connected it appears there is something wrong with the APN at first instance.

The E160 stick seem to drop sometimes but if you put a mSD card in it, it is okay. Mind you it does do that under Windows.

---

