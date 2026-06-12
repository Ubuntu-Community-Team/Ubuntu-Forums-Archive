---
title: "Internet issues"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by Slack44 on 2010-06-09
The internet was working okay when i first used this, i updated everything on there and when i restarted no matter what i did i couldn't possibly get on the internet, i am using broadband and works 100% on anything else i use, for example works great on win 7 but wont even connect on ubuntu. any sugguestions?

---

### Post by ixifx on 2010-06-09
if you have a wired connection available, try hooking up to that and going to System > Administration > Hardware Drivers

if there are drivers available for your card, activate them and reboot

I would also recommend doing
```
sudo apt-get update
```
from the command line
doing this fixed the issues I was having with my broadcom wireless card in my old laptop.

a search of the forums will pull up SEVERAL threads about fixing broadcom issues

---

### Post by Slack44 on 2010-06-09
> **ixifx said:**
> if you have a wired connection available, try hooking up to that and going to System > Administration > Hardware Drivers

if there are drivers available for your card, activate them and reboot

I would also recommend doing
```
sudo apt-get update
```from the command line
doing this fixed the issues I was having with my broadcom wireless card in my old laptop.

a search of the forums will pull up SEVERAL threads about fixing broadcom issues



wireless and the second thing requires to be on the internet....

---

### Post by ixifx on 2010-06-09
> **ixifx said:**
> if you have a wired connection available

so I guess what you meant to say was, "No, I do not currently have access to a wired connection"

if in fact you do have a wired connection, but cannot connect to the internet using that, then I have no idea.  I had to plug my laptop up to my router to get the drivers I needed, but they WERE available and worked flawlessly after getting them installed.

It is possible to get b43fwcutter (assuming it's a b43 model chip) and the windows drivers for your card and get everything set up that way.

---

### Post by Iowan on 2010-06-09
Moved to Networking & Wireless.
From a terminal (Applications>Accessories>Terminal) check **ifconfig -a** to see if any interfaces have an IP address.  **sudo lshw -C network** will provide more information about your interfaces. 
Check (**cat /var/lib/NetworkManager/NetworkManager.state**) to see if networking is enabled. [This]("http://ubuntuforums.org/showthread.php?t=1505217") thread proposes a way to reset, but making a backup copy somewhere might be a good idea ;)

---

