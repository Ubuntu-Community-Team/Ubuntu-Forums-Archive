---
title: "BCM4312 just stopped reading my network"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by dante1982 on 2009-05-17
Hello all,  

I have a dell inspiron running 9.0.4 64 bit with a bcm4312 wireless card.  I just stopped locating my wireless network, or any other for that matter.  after searching a bit, I ran:

[FONT=Fixedsys]sudo lshw -C network[/FONT]

I am a bit of a noob, but the only thing that looked amiss was under [FONT=Fixedsys]eless[/FONT].  At the end of the description it had the following:

[FONT=Fixedsys]*-network DISABLED

[FONT=Verdana]based on what I saw here:

[https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-disabled](https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-disabled)

It seems that the card is disabled, but it didn't provide any ideas about how to enable the card.  I checked the hardware drivers and there is an STA driver that is enabled.  I tried disabling and re enabling it, to no avail.  

Any ideas would be greatly appreciated


[/FONT][/FONT]

---

### Post by superprash2003 on 2009-05-18
did this happen after a recent update??

---

