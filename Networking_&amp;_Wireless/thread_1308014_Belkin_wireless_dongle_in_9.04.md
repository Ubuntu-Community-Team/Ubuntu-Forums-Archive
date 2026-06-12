---
title: "Belkin wireless dongle in 9.04"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by The Toxic Mite on 2009-10-31
Hey everyone!

I am preparing for the switch back to Ubuntu, a couple of months after my laptop borked, so... :P

Anyway, I have a Belkin wireless USB dongle that I would like to use, and I was wondering if there is a driver for it?

Here's some info about it:

Model number: F6D4050
Version: 1000ed

I ran a lsusb test on the Kubuntu 9.04 LiveCD to make sure it detects the dongle, and it did.

Thanks!

-TTM-

---

### Post by The Toxic Mite on 2009-10-31
Bump :P

---

### Post by The Toxic Mite on 2009-11-01
Bump

---

### Post by pdc on 2009-11-01
with the Belkin plugged in what does

> lsusb in a terminal say?

take the Vendor ID and PRoduct ID number you get for the Belkin:

enter into google with a title like

Ubuntu configure and whatever the above says, and see what you get:

ie something like

> Ubuntu configure 12d1:1003  (12d1: 1003 is a Huawei E220 modem device)

I think they are Ralink devices; using the rt2XXX series drivers is what I think folks says

9.04 seems more stable: you might be well advised to stay with it till 9.10 beds in: 

sadly many folks believe newly released software is stable and tested !!

---

### Post by The Toxic Mite on 2009-11-01
> **pdc said:**
> with the Belkin plugged in what does

 in a terminal say?

take the Vendor ID and PRoduct ID number you get for the Belkin:

enter into google with a title like

Ubuntu configure and whatever the above says, and see what you get:

ie something like

  (12d1: 1003 is a Huawei E220 modem device)

I think they are Ralink devices; using the rt2XXX series drivers is what I think folks says

9.04 seems more stable: you might be well advised to stay with it till 9.10 beds in: 

sadly many folks believe newly released software is stable and tested !!

I get you. I was thinking of going with 9.10 but after seeing a lot of complaints from other users here, I have decided to wait until the Devs can get it more stable.

Right, back in a mo :D

---

### Post by The Toxic Mite on 2009-11-01
```

ubuntu@ubuntu:~$ lsusb
Bus 001 Device 003: ID 050d:935a Belkin Components

```:)

EDIT: upon further searching, I have come across this:

[http://ubunturt2870.pbworks.com/FrontPage](http://ubunturt2870.pbworks.com/FrontPage)

HOPEFULLY this will work...

EDIT2: Just wondering, do I extract the package in / (the root directory)?

---

### Post by pdc on 2009-11-01
Make a directory called Downloads or some such title;

Download any downloads into your Downloads directory;

have you run tar.gz files before?

if you unzip the file in your downloads directory, that is a good place to do things from;

let us know how you get along

here was a posting I did on a similar USB stick I got working

[http://ubuntuforums.org/showthread.php?t=1281183&highlight=dick+smith+usb](http://ubuntuforums.org/showthread.php?t=1281183&highlight=dick+smith+usb)

---

### Post by The Toxic Mite on 2009-11-03
> **pdc said:**
> Make a directory called Downloads or some such title;

Download any downloads into your Downloads directory;

have you run tar.gz files before?

if you unzip the file in your downloads directory, that is a good place to do things from;

let us know how you get along

here was a posting I did on a similar USB stick I got working

[http://ubuntuforums.org/showthread.php?t=1281183&highlight=dick+smith+usb](http://ubuntuforums.org/showthread.php?t=1281183&highlight=dick+smith+usb)

Okay, cheers for that!

---

### Post by The Toxic Mite on 2009-11-03
Actually, coming to think about it, would this work in Debian GNU/Linux as well?

I'm just wondering...

---

### Post by pdc on 2009-11-03
try it and tell us !

You're the guy having all the good ideas; they have a huge supportive forum; try their community

---

