---
title: "Ethernet Card not recognized by Ubuntu"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by Campitor on 2006-03-05
hello all:

  I've installed UBUNTU on my mom's HP Vectra VL400 MT, she has a built in network card, which after some googling I think is a 3Com device, but don't know which version.  During installation of Ubuntu 5.10, the card was not detected.

  I've read some forums and it looks like there is a module I can load, which recognized the ethernet connection. 

  Are there many modules for different versions of 3Com cards, or just one?  Would you please point me to:

1.  How can I tell which specific card is on my mom's computer?
2.  Where can I get those modules?

Thanks for your help, I convinced my mom to switch to linux, and now I look like an idiot, not knowing what to do.  I've also praised the forums, so maybe I'll impress her with someone elses knowledge.

Camp

---

### Post by jamesr on 2006-03-05
Anything mentioned in dmesg

```
sudo dmesg |grep eth0
```

goto the HP website  and see if there are emulation references also do some googling. It is safe to assume that others will had a a similar problem. If you find the NIC reference, we should be able to help set it up manually.

---

### Post by Campitor on 2006-03-05
I typed the command and nothing came out.  I've been doing searches in google...but the computer is rather old, and nothing useful has shown up.  What is a NIC reference?  Is this something I can get from the hardware or from linux?

I've done ifconfig a couple of times and only the lo 127.0.0 address is there.

I'll keep working on it.  Thanks for your reply

camp

---

### Post by Monkeh on 2006-03-05
According to google, you have a 3Com 905C-TX 10/100 BT. As root, run modprobe 3c95x, and then ifconfig -a, see if it shows an eth0.

---

### Post by Campitor on 2006-03-05
[QUOTE=Monkeh]According to google, you have a 3Com 905C-TX 10/100 BT. As root, run modprobe 3c95x, and then ifconfig -a, see if it shows an eth0.[/QUOTE]

I get the following:

FATAL: Module 3c95x not found.

After ifconfig -a I only get the lo entry and a:

sit0    Link encap: IPv6-inIPv4
         NOARP MTU: 1480  Metric:1
         RX packets:0 errors:0 dropped:0 ....and so

Hope this output helps.  Maybe the module is on the install CD, or I can download it from somewhere.  I'll try to find it in google, but you probably figure out I'm not a good googler.  Thanks for all your help

---

### Post by Monkeh on 2006-03-05
Sorry, it's 3c59x, not 3c95x. That'll teach me for posting at 1am.

---

### Post by Campitor on 2006-03-05
That module I have...but nothing happens.  After ifconfig -a I still get only two entries: lo and sit0.  Thanks for your help...and sorry for keeping you up

camp

---

### Post by Monkeh on 2006-03-05
heh, I stay up late anyway. That's a little odd. Can you post the output of lspci please?

---

### Post by jamesr on 2006-03-07
I had no diffliculty finding the manual on the HP site, and the PC is not that old.

should it not be 
sudo modprobe 3c905

---

### Post by Monkeh on 2006-03-07
No, because no such module exists. The 905 uses the 59x driver.

---

