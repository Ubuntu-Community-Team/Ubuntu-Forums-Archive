---
title: "Can't setup my IMON VFD"
date: 2010-09-21
forum: Multimedia Software
---

### Post by immoweichert on 2010-09-21
Hi everybody.

I am having problems getting to set up the iMON VFD on my Thermaltake Bach.

When I enter

lsusb

I get the following output:

Bus 003 Device 003: ID 099a:7202 Zippy Technology Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

From what I understand so far I do have the iMON VFD and not the LCD installed.

I've edited my 
LCDd.conf

and have changed there the initial entry 

Driver=curses 

to 

Driver=imon
When I am restarting, nothing is happening.

Where am I going wrong ?

---

### Post by immoweichert on 2010-09-27
Anybody PLEASE !!!!

---

### Post by rhpot1991 on 2010-10-09
Try this: [http://www.baablogic.net/drupal/node/6](http://www.baablogic.net/drupal/node/6)

---

### Post by Termo on 2010-11-03
Did you get it to work on 10.04??

I still have a blank display on my imon VFD :(

---

### Post by a-user on 2010-11-03
mine is working since 9.10. but it prints write errors in syslog due to my pc being to fast. there was a fix (inserting a longer delay in the send method) long time ago but this seems to never had made it into kernel, at least not in a reliable way.

the result of this are random characters on the display. it is a known problem, the imon vfd is not working correct on modern (faster) pcs.

but to not getting it to work at all is quite uncommon.

---

### Post by rhpot1991 on 2010-11-03
> **Termo said:**
> Did you get it to work on 10.04??

I still have a blank display on my imon VFD :(

The changes on my site worked for me from Karmic forward.  I have since disabled it in Maverick while messing around with the new imon driver, but I believe it was working before I disabled it.

---

