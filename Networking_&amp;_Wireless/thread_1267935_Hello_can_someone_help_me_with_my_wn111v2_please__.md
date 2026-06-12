---
title: "Hello can someone help me with my wn111v2? please :/ [HELP]"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by Daylon on 2009-09-16
Hello I am having ALOT of trouble downloading a working file for NDISwrapper I've tried to many things but it turns out I was downloading the driver for wG111v2 not wN111v2 I wasreally hoping someone around here knew exactly what the problem is and how to get it working? I'd very much appreciate it as this is my last step to permanently using linux rather than windows :/ I set the pc up to a wired network in my living room and the internet worked great I would like to have it back in my room and working wireless so once again I would very much appreciate some help thanks.

Also this is my lsusb return since some people ask for it:

daylon@daylon-ubuntu:~$ lsusb
Bus 001 Device 003: ID 0846:9001 NetGear, Inc.      <---- My wn111v2 USB adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by bkratz on 2009-09-16
> **Daylon said:**
> Hello I am having ALOT of trouble downloading a working file for NDISwrapper I've tried to many things but it turns out I was downloading the driver for wG111v2 not wN111v2 I wasreally hoping someone around here knew exactly what the problem is and how to get it working? I'd very much appreciate it as this is my last step to permanently using linux rather than windows :/ I set the pc up to a wired network in my living room and the internet worked great I would like to have it back in my room and working wireless so once again I would very much appreciate some help thanks.

Also this is my lsusb return since some people ask for it:

daylon@daylon-ubuntu:~$ lsusb
Bus 001 Device 003: ID 0846:9001 NetGear, Inc.      <---- My wn111v2 USB adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

It might be helpful to look at the following (esp post after number 5).

[http://ubuntuforums.org/showthread.php?t=885520&highlight=wn111v2](http://ubuntuforums.org/showthread.php?t=885520&highlight=wn111v2)


Good Luck

---

### Post by Daylon on 2009-09-16
> **bkratz said:**
> It might be helpful to look at the following (esp post after number 5).

[http://ubuntuforums.org/showthread.php?t=885520&highlight=wn111v2](http://ubuntuforums.org/showthread.php?t=885520&highlight=wn111v2)


Good Luck

oh my god dude i got it to work!

---

### Post by bkratz on 2009-09-16
> **Daylon said:**
> oh my god dude i got it to work!



Please mark the thread solved!

---

### Post by Xiuuy on 2009-09-25
Hey I've got the Wn111v2 and I can't get mine working. I'm new to ubuntu can anybody help?

---

### Post by Daylon on 2009-09-25
> **Xiuuy said:**
> Hey I've got the Wn111v2 and I can't get mine working. I'm new to ubuntu can anybody help?


You need to download the driver and install it with ndiswrapper

try this:

[http://ubuntuforums.org/attachment.php?attachmentid=86443&d=1222397627](http://ubuntuforums.org/attachment.php?attachmentid=86443&d=1222397627)

---

### Post by ontoa on 2009-11-10
> **Daylon said:**
> You need to download the driver and install it with ndiswrapper

try this:

[http://ubuntuforums.org/attachment.php?attachmentid=86443&d=1222397627](http://ubuntuforums.org/attachment.php?attachmentid=86443&d=1222397627)


Tried all that, both sets of drivers don't work, The atheros one installs but does not detect dongle and the wanda3100 shows up as invalid driver

---

### Post by cjmiller00 on 2010-06-18
> **ontoa said:**
> Tried all that, both sets of drivers don't work, The atheros one installs but does not detect dongle and the wanda3100 shows up as invalid driver


ndiswrapper -i arusb_xp.inf 0846:9001 keeps telling me 

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

but when i sudo ndisgtk 
i am able to locate driver from disk and it goes in and says harware present but I can not use it. seems as though it wont associate with USB 0846:9001

---

