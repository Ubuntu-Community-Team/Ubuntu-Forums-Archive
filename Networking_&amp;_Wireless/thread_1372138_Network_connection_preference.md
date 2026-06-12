---
title: "Network connection preference"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by krishnamohan on 2010-01-04
Hi...

In Network Manager, I have profiles called eth0 and eth1. eth1 is the one I use most often. Thus, I want it to be the default. But eth0 is the one that gets activated on login. How can I change this? I am posting this for the second time......

---

### Post by suseendran.rengabashyam on 2010-01-04
Hi,
You need to go to System->Preferences->Network Connections->Auto eth0->Edit and then uncheck "Connect Automatically". 

Also make sure that you have checked "Connect Automatically" in Auto eth1.

---

### Post by tsucol11 on 2010-01-05
> **suseendran.rengabashyam said:**
> Hi,
You need to go to System->Preferences->Network Connections->Auto eth0->Edit and then uncheck "Connect Automatically". 

Also make sure that you have checked "Connect Automatically" in Auto eth1.

Worked for me. eth0 is dedicated to XP while eth1 is dedicated to ubuntu 9.04

Brian

---

### Post by krishnamohan on 2010-01-09
The problem is that, for eth0, the edit button is not working...I can edit eth1 though...dont know why it has become so..

As far as I can remember, eth0 connection could also be edited sometime back..dunno what happened..

---

### Post by Iowan on 2010-01-09
> **krishnamohan said:**
>  I am posting this for the second time......A "bump" might have been adequate...
You may need to click on (highlight) the interface before it becomes editable. (Maybe you have already done that...)

---

### Post by krishnamohan on 2010-01-10
Yes....for my other two connections, when I click on them, the three buttons add,edit and delete become active.....

For eth0, only the add button is active.....

---

### Post by krishnamohan on 2010-01-12
Isn't there some way to do that by editing some configuration file somewhere or something?

---

### Post by Iowan on 2010-01-12
For a quick and (very) dirty: 
Add a line to */etc/network/interfaces* that reads "auto eth0". Save file and restart/reboot (reboot might do better job of synching with Network Manager. It might make no difference whatsoever... or might work!

---

### Post by krishnamohan on 2010-01-13
Okayyyy...that worked!! I added auto eth1 to the interfaces file.....thanks.....:D

---

