---
title: "BroadcomWireless Driver"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by shadowfax1 on 2010-02-27
I have the Broadcom 1390 wireless mini card on a dell d620.  Nothing comes up on available networks after a clean install of 9.10.  If I hard wire the laptop will the driver be available in the updates?

If not is my next step ndiswrapper and if so what does that do?

Thanxs

---

### Post by Crafty Kisses on 2010-02-27
Let's see what Broadcom card you actually have, go into the terminal and type:
```
lspci
```
You should see something like this:
```
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```
Once I have more information, I can help you further.

---

### Post by shadowfax1 on 2010-02-27
okay it says
network controller: Broadcom Corp BCM4311 802.11/bg WLAN (REV 01)

---

### Post by bkratz on 2010-02-27
> **shadowfax1 said:**
> okay it says
network controller: Broadcom Corp BCM4311 802.11/bg WLAN (REV 01)

In the terminal Applications>>Accessories>>Terminal and enter

sudo apt-get install bcmwl-kernel-source


will need your password which will not be echoed, just hit enter when you put it in.
then reboot and see if there is  driver to activate in system>>admistration>>hardware drivers, may need to reboot again.

---

### Post by shadowfax1 on 2010-02-27
this is the response..

Couldn't find package bcmw1-kernel-source

Now I havn't hardwired this yet to get the updates...

---

### Post by bkratz on 2010-02-27
> **shadowfax1 said:**
> this is the response..

Couldn't find package bcmw1-kernel-source

Now I havn't hardwired this yet to get the updates...

Did you put in a "1" instead of an "l" (L)? and also you do have to have an ethernet connection to do it this way. It can be done from the live CD if you don't have a wired connection. Do you?

---

### Post by shadowfax1 on 2010-02-27
Hi
No I put in the 'L' and the spaces...I'll try the live cd thats the same as the
iso I burnt to install the program?

Ethernet kinda hard for me..

---

### Post by bkratz on 2010-02-27
> **shadowfax1 said:**
> Hi
No I put in the 'L' and the spaces...I'll try the live cd thats the same as the
iso I burnt to install the program?

Ethernet kinda hard for me..

Well it looked like a 1 in the last entry. Anyway, the instructions with the live CD are here.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by shadowfax1 on 2010-02-27
Hi there
Just wanted to thank you for all your help...worked out great!

---

### Post by bkratz on 2010-02-27
> **shadowfax1 said:**
> Hi there
Just wanted to thank you for all your help...worked out great!

It is always nice to have a good ending!  Please go to the thread tools and mark as [solve] in case it helps someone else.

---

### Post by aci016 on 2010-04-15
tried this one. and it worked!!! thank you. :)

i'm very grateful since the other one did not worked. thanks again. :)

---

