---
title: "Ubuntu 10.04 LTS kaffeine no device"
date: 2010-05-02
forum: Multimedia Software
---

### Post by Micky1307 on 2010-05-02
Dear Forum,

I'm more or less a newbei in ubuntu, anyway I can't get my SAT card to work anymore for I'm installed 10.04.
It worked fine under 9.10.

Any idea how I can debug or solve the issue.

Thank you for your help in advance.

---

### Post by marcellux on 2010-05-04
> **Micky1307 said:**
> Dear Forum,

I'm more or less a newbei in ubuntu, anyway I can't get my SAT card to work anymore for I'm installed 10.04.
It worked fine under 9.10.

Any idea how I can debug or solve the issue.

Thank you for your help in advance.

Got the same problem here! Third party software was disabled during upgrade and it need to be re-enabled! 
The problem is, I don't know how to do that! 

Does anybody know how or where to enable this back?

Thanks in advance

---

### Post by marcellux on 2010-05-04
Hi! I got it running again!

Go to the main menu > system > administration > hardware drivers. click on it and wait until it scans your machine for devices. If it finds the DVB-T card, then click on "activate". This will automatically look for the proper driver and will install it!

Now Kaffeine is working like before!

---

### Post by Micky1307 on 2010-05-06
> **marcellux said:**
> Hi! I got it running again!

Go to the main menu > system > administration > hardware drivers. click on it and wait until it scans your machine for devices. If it finds the DVB-T card, then click on "activate". This will automatically look for the proper driver and will install it!

Now Kaffeine is working like before!
Unfortunately this doesn't apply to me, because I have DVB-S2.
In  addition my  DVB-S2 device  is not listed in the hardware driver  section. :-(

---

### Post by xc3RnbFO8P on 2010-05-06
In Terminal(Application> Accessories) , show the output of:
> dmesg

---

