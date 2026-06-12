---
title: "Possible issue with wireless card?"
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by TheMTtakeover on 2013-04-19
So I just installed Ubuntu on an old laptop that my girlfriend was gonna toss. aLL is well except that I cant seem to get the wireless to connect to my router.

I have updated it using a wired connection
I have checked to see if "additional drivers" (proprietary drivers) needed installed.

It shows that I have a wireless card in the top right hand side of the screen. I have networking enabled.
Here is the card that I have in the computer from the terminal

```
09:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
```

I'm all out of ideas. Help please?

---

### Post by chaos_monkey on 2013-04-19
Missing firmware?
Look here:
[https://launchpad.net/ubuntu/+source/b43-fwcutter](https://launchpad.net/ubuntu/+source/b43-fwcutter)
or
[http://launchpadlibrarian.net/103658095/firmware-b43-installer_015-14_all.deb](http://launchpadlibrarian.net/103658095/firmware-b43-installer_015-14_all.deb)
The latter link assumes you are running 12.10 and have a 32bit computer.

Download the .deb file (second link above) to your computer.
In your file manager right click on the .deb file and choose "open with Ubuntu Software Center".
Install.
Play :-)

---

### Post by matt_symes on 2013-04-19
Thread moved to **wireless and networking**

---

### Post by Hadaka on 2013-04-19
Hi, let's take a look and see which
dirver you need to get it working.
please COPY and paste the following.
```
lspi -nn | egrep '0200|0280'
rfkill list all
```
thanks.

---

