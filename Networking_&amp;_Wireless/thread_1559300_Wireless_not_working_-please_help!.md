---
title: "Wireless not working -please help!"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by slainte001 on 2010-08-23
Hello,

I have a new installation of Ubuntu 10.04 on an old Dell Inspiron 710m laptop. The wireless network is not working at all or showing up in the network icon. Please help. I'm an intermediate newbie to Ubuntu.

My lspci output:

Broadcom BCM4401-B0

PCID: 14e4:170c


slainte001

---

### Post by e79 on 2010-08-23
You may want to give a look at :
 
[http://www.linlap.com/wiki/dell+inspiron+710m](http://www.linlap.com/wiki/dell+inspiron+710m)
 
They say that by using the '[ipw2200]("http://ipw2200.sourceforge.net")' module, it works (though it seems to be related to Intel WiFi cards not Broadcom - I suspect that this lscpi command only returned the detected Ethernet controller,not the WIFi - I might be wrong though).
 
Hope this helps
 
e79

---

### Post by TBABill on 2010-08-23
Any possibility of plugging into your router (via ethernet) and letting the system update and possibly offer proprietary drivers? I have to do so with my Broadcom, but it's a newer model I believe.

---

### Post by slainte001 on 2010-08-23
Well, thanks for the early suggestions. I actually got it to work using the bcmwl5 windows driver (inf file). There might be multiple ways to do this, but for me, the ndisgtk app worked well, a graphical version of ndiswrapper. Thanks again for the quick replies. Hopefully, this solution will help someone else with this laptop.

See next message...

slainte001

---

### Post by slainte001 on 2010-08-23
So, I was online and connected using the process above, but after rebooting I can't connect again. Case not solved yet, I guess.

---

### Post by slainte001 on 2010-08-23
Thanks, TBABill. After connecting by wire to the router, I went to hardware drivers under administration, and there were proprietary drivers for this network card. It installed them, and they worked, even after a few reboots! Thanks, again.

slainte001:p

---

