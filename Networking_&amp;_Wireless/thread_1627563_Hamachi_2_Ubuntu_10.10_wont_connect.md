---
title: "Hamachi 2 Ubuntu 10.10 wont connect"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by Blue_Alien on 2010-11-21
I have installed Hamachi 2 on Ubuntu 10.10 but I can not get it to start after hours of trying. Whenever I try and start it, I get this output


 version    : 2.0.0.12
  pid        : 1188
  status     : offline
  client id  : 086-682-666
  address    : 0.0.0.0
  nickname   : 
  lmi account: 

Whenever I try and add my account, it says that I need to be online for it to work. How can I fix this?

---

### Post by DooBLER on 2010-12-02
README says:

> When you run the daemon for the first time, it stays offline. To change its status to online, run:

hamachi login

> hamachi -h

---

### Post by SoDman on 2010-12-10
Thank you for the information. Got my Hamachi2 to work and connect to my network with this help. I am actually running Lucid 10.04 just so others know this info works for that also.

My next question is, do you know how to get one of the GUI's out there to work with the newest Hamachi Linux version? I haven't rebooted since I got it to work, but I am not even sure if it will auto-load when I do reboot. At that point it is kind of a pain to go into a terminal window to try and track down if it is running or not. Anyway, not a huge deal, at least it's working :)  Just thought if someone knew a way to get a GUI working for it, then it would be very helpful.

Thanks!

SoDman

---

### Post by ztefn on 2010-12-18
> **SoDman said:**
> My next question is, do you know how to get one of the GUI's out there to work with the newest Hamachi Linux version?
I'm the developer of [Haguichi]("http://www.haguichi.net/") and i dare to claim it works out of the box with the latest Hamachi² Beta! :D

---

### Post by suselinux2 on 2010-12-19
Sorry, but I have one question about ubuntu 10.10 x64 and Hamachi / Haguichi 1.0.3. .

I have problems with login on my network. I start with join network, then I enter network name and password. The result is invalid password.

What is wrong?

Thank you for your help

---

### Post by ztefn on 2010-12-19
Did you create the network using Hamachi/Haguichi or via the LogMeIn website? In the latter case you'll have to use the ID as network name when joining the network.

---

