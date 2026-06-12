---
title: "GSM modem takes too long to be detected"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by Amyas on 2011-08-08
Hello all.. I have a USB GSM modem... It takes too long for it to be detected after plugged in... Is there anything I can do to make this process faster???
I'm using Ubuntu 11.04 natty, and the modem is ZTE AC2746 ...

---

### Post by pdc on 2011-08-09
If you type in a terminal

> lsusb 

do you see 

> 19d2:fff5 

or do you see

> 19d2:fff1

the reason I ask is you may benefit from usb_modeswitch

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=222&sid=08b78179e448400b3c07f6a41b4efe23](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=222&sid=08b78179e448400b3c07f6a41b4efe23)

---

### Post by Amyas on 2011-08-09
I get this (among others):

```
Bus 004 Device 002: ID 19d2:fff1 ONDA Communication S.p.A.
```

---

### Post by pdc on 2011-08-09
so it is detected as a modem;

this process does take time; you usually have to whistle for a minute or so

I find sakis 3g is quicker; 

[http://www.sakis3g.org/](http://www.sakis3g.org/)

but if you choose to install that, you need to look to sakis for support

---

### Post by Amyas on 2011-08-10
I'll give it a try.. Thank you :)

---

### Post by Amyas on 2011-08-10
Tried sakis3g ,, it takes the same amount of time... In the waiting time when I try to connect using sakis it gives an error:

```
Port /dev/ttyUSB0 is currently occupied by 859 modem-manager.
```

---

### Post by pdc on 2011-08-10
two options to pursue

go to sakis website

[http://www.sakis3g.org/](http://www.sakis3g.org/)

and go to the troubleshooting page

[http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_troubleshooting](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_troubleshooting)

read about it

he suggests

> # sakis3g --debug

which for Ubuntu to me means

> sudo sakis3g --debug

also: join his forum; he will help you;

if he does, come back and tell us the answer

---

### Post by Amyas on 2011-08-12
Ok, I will follow through with him and tell post the result... Thanks a lot :)

---

### Post by Amyas on 2011-08-12
Ok, I will follow through with him and post the result... Thanks a lot :)

---

