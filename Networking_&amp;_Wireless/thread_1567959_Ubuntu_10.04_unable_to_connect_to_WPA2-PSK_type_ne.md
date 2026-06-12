---
title: "Ubuntu 10.04 unable to connect to WPA2-PSK type network"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by T40 on 2010-09-04
[LEFT]I have freshly installed Ubuntu 10.04  I downloaded all the updates using Update Manager
Reboot. 

I can see all available networks, but each time I try to logon to my home network using preshared key it just fails.
It doesn't give any error messages, it asks for a password. I supply the password and nothing. No ip address no connection established. I can take WPA2 off all together and it works.

LSPCI shows : 

Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


It's a HP NX7010 , Any thoughts ?

Could anyone tell me what's the problem ? I saw many many events, and posts created by many people having the same problem, but I haven't found any solution. 

Are developers aware of this bug ?
[/LEFT]

---

### Post by grahammechanical on 2010-09-04
It might sound stupid but are you using the correct password or key? Also, when you say

> I can take WPA2 off all together and it works, do you mean that you set the security to "none?" If you can connect without any security but cannot when the connection is secured, then perhaps it is an incorrect password that is causing the problem.

Regards.

---

### Post by Joe of loath on 2010-09-04
What about if you set it to WPA1?

---

### Post by T40 on 2010-09-04
I have 4 laptops at home and all of them use the same password.
It works normally.
I haven't tried to change to WPA1 yet.

I'll check and let you know.

---

### Post by bkratz on 2010-09-04
Another potential issue is shown here

[http://ubuntuforums.org/showpost.php?p=9680300&postcount=14](http://ubuntuforums.org/showpost.php?p=9680300&postcount=14)

---

