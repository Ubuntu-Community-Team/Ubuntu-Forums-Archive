---
title: "You are not allowed to acess the system configuration"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by New_Ubie on 2009-01-24
Hi,

  i have installed ubuntu 8.04 successfully and i was able to get the wireless setup done as well...

To install oracle software and create a DB i made some chnages to some file in /etc folder. After i rebooted..i started getting this issue...

The Configuration could not be loaded
You are not allowed to access the system configuration...

I am not able to connect as root as i don't have a password...
it does not let me do a su - root....

my wireless does not connect....

Please help..i am new to linux...

---

### Post by cariboo on 2009-01-24
It would really help if you gave us a little more info than:

> some file in /etc folder

You may have noticed there are a lot of files and directories in /etc

Jim

---

### Post by New_Ubie on 2009-01-24
Hi..thanks for the reply..my apologies ..here are the files..

/etc/sysctl.conf

/etc/security/limits.conf:

/etc/pam.d/login

i fixed the issue of su - root..i am able to sudo as root...

it still gives me the same error when i try to open networking...

---

### Post by New_Ubie on 2009-01-24
i did undo the changes...it is still the same...

seems to be some issue with the OS..is there a bug related to this?

---

