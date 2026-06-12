---
title: "Use Broadcom proprietary again after ndiswrapper uninstall"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by slovy88 on 2008-12-04
Heloo 
Im using 6735s notebook from HP. I had a little problem connecting to the wifi with the proprietary driver for broadcom so i uninstalled it and tried to install a driver with ndiswrapper but that one wasnt working so i removed first the driver with ndiswrapper and then i uninstalled ndiswrapper with synaptic. Installed the proprietary broadcom driver it was showing that it is activated and in use but after reboot it is activated but not in use. I cant find out how to keep it in use after reboot.
Pls help.
Thank you

the card is a BCM4322
ubuntu 8.10

---

### Post by Ayuthia on 2008-12-04
Can you post the results of:
```
cat /etc/modules|grep -e ndiswrapper -e b43 -e ssb -e wl
cat /etc/modprobe.d/blacklist|grep -e ndiswrapper -e b43 -e ssb -e wl
```
There are most likely some modules here that are in the wrong place since you are no longer using ndiswrapper.

---

### Post by slovy88 on 2008-12-04
Thx for your reply 
Ok so here it goes

For the first line of code you send me I get no result.
For the second one I get this ```
# replaced by b43 and ssb.

```

---

### Post by slovy88 on 2008-12-05
please help i cant figure it out.
googled everything i could think of but i didnt find a thing concerning a similar case to mine

---

### Post by Ayuthia on 2008-12-05
> **slovy88 said:**
> please help i cant figure it out.
googled everything i could think of but i didnt find a thing concerning a similar case to mine

Sorry.  I have been building Gentoo on my laptop during the past few days.  Since you don't have anything in those files that are adding or removing wireless modules for you, let try:
```
echo wl | sudo tee -a /etc/modules
```
That will add the wl module to the load list when the system boots up.  That should hopefully do it for you.

---

### Post by slovy88 on 2008-12-05
thank you very much it actualy worked
:-)

---

