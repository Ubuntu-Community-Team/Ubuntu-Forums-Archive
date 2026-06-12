---
title: "laptop internet connection failure"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by mamboze on 2011-10-25
Hi,

I have a Samsung RV511 laptop which, for several days, has been unable to connect to the internet, either via ethernet or wifi. The laptop is about 6 months old and is running ubuntu 10.04 and both internet connections worked before. The laptop has a Broadcom BCM wifi chip. The surprising thing, for me at least, is that when the ethernet cable is plugged in, Skype works.

I've reinstalled the wifi network connection but it doesn't work. I remember updating software last week but I can't recall installing any kernel updates, but I may have. Anyhow, the current kernel is 2.6.32.34-generic. 

Any help much appreciated.

---

### Post by kc1di on 2011-10-25
> **mamboze said:**
> Hi,

I have a Samsung RV511 laptop which, for several days, has been unable to connect to the internet, either via ethernet or wifi. The laptop is about 6 months old and is running ubuntu 10.04 and both internet connections worked before. The laptop has a Broadcom BCM wifi chip. The surprising thing, for me at least, is that when the ethernet cable is plugged in, Skype works.

I've reinstalled the wifi network connection but it doesn't work. I remember updating software last week but I can't recall installing any kernel updates, but I may have. Anyhow, the current kernel is 2.6.32.34-generic. 
 
Any help much appreciated.

A few things worth trying. 

1. uninstall the broadcom drivers using system settings > Additional drivers and try re-installing them. 

2. have you changed any firewall setting?

3 have you checked system settings > network manager for any changes?

Just some suggestions.
dave

---

### Post by mamboze on 2011-10-25
> 1. uninstall the broadcom drivers using system settings > Additional drivers and try re-installing them.

2. have you changed any firewall setting?

3 have you checked system settings > network manager for any changes? 

Do you mean go to System>Administration>Hardware drivers and uninstall? 

And as there is no ethernet connection either, it won't be possible to reinstall the Broadcom drivers, will it?

No firewall changes. 

I reinstalled the wifi connection for the ASUS DSL-N11 router/modem, but that made no difference.

---

### Post by kc1di on 2011-10-25
yes that's what i was thinking but had forgotten you do not have wired connection. I'm out of Ideas at this point

---

### Post by mamboze on 2011-10-25
Hi Dave,

Thanks for your help. I think I'll reinstall 10.04. All my data is backed up so it's really no big deal. Still, I would like to know what happened.

---

