---
title: "How to Configure Ubuntu for PPPoE"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by chirag64 on 2009-07-27
Can someone please tell me step by step as to how i should configure ubuntu for PPPoE internet connection? I'm a complete n00b to ubuntu. :)

---

### Post by martinbaselier on 2009-07-27
Isn't that one of the options in the networkmanager?

---

### Post by chirag64 on 2009-07-27
> **martinbaselier said:**
> Isn't that one of the options in the networkmanager?

Well, I don't know what PPPoE stands for, so if there is an option for it under some other name, i wouldn't know.

---

### Post by martinbaselier on 2009-07-27
[http://en.wikipedia.org/wiki/Pppoe](http://en.wikipedia.org/wiki/Pppoe)

I thought there was an option for pppoe in the network manager, but I haven't got it installed, so it's hard to tell for sure.

---

### Post by fvanham on 2009-07-27
open a terminal...
run the command
```
sudo pppoeconf
```then your userpassword is asked (you won't see anything appear,  keep typing :p)
press the return to enter you password
if everything is in order, you should see a text-based pppoe setup program :)
you change from option with you TAB-key and the arrows :) the return key to select something.
Good luck! :)

---

### Post by chirag64 on 2009-07-27
It does not ask me my ISP name. How do i configure that?!? :O

---

### Post by sarfarazkazi on 2009-07-27
ISP name is not required.

---

### Post by chirag64 on 2009-07-27
But in windows xp, i need to enter ISP name and service name. Else it does not connect to the internet. I guess the ISP name is only for our reference then. Then how do i put the service name?!?

---

### Post by ZhuaSD on 2009-07-28
pppoe just needs user / password.  No special service name.

The system names it as dsl-provider no matter what.

---

### Post by chirag64 on 2009-07-30
In XP, when i setup a new PPPoE connection, i'm supposed to go to its properties and enter my service provider's name, else it does not work. 
My net is not working in ubuntu wen i enter my username and password.

---

### Post by alexandari on 2009-07-30
are you sure you have your network interface selected? I mean eth0 (or whatever you wanna use) ?
try it the old "click click" way. 
**System --> Administration --> Network.** 
You unlock it by using your user password. After which you should see a **"Point to point connection"**. Ok time to configure it. After you open the configuration window on top you should see **"Activate this connection"** (or something like that my ubuntu is not in enligsh). Connection type - select PPPoE. After you write your username and pass,check out the other 2 tabs on top and configure things like you want them to be. I mean select your Ethernet interface and stuff...
I hope I helped somehow...

---

