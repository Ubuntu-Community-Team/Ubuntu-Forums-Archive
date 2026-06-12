---
title: "Telnet question to an AP"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by getintanked on 2009-04-01
Hey guys, my question is really regarding telnet not so much the networking aspect, so hopefully this is an easy one.

I have a cisco aironet 350. and in windows i can connect to it no problem - simply because I know how :)

How do I go about connecting to this via com port in ubuntu??

I need to set the baud rate and other settings before connecting and I just can't find these settings when i type "telnet' in term.

Help, please :-/

thanks,
_matt

---

### Post by jonobr on 2009-04-01
Hey,

Your post is a bit confusing, mayhap Im not understanding.

Telnet is an IP application, connecting via a serial connection uses a physical connection to the device using a comm port.

IN windows if you are connecting via terminal you would use hyperterm , CRT , procomm or some such package where you set the hardware rate, flow control etc. however if Ubuntu if you are doing the same, you would need to use minicom

If you type in minicom you will see the connections details at the bottom.
To see the options, hit control A and then Z to get a help menu.

---

### Post by getintanked on 2009-04-01
Awesome, yea thats the one ;)

cutecom is the one i'm using now - very simple and does the job.

cheers,
-Matt

---

### Post by jonobr on 2009-04-01
Rock on :guitar:

---

