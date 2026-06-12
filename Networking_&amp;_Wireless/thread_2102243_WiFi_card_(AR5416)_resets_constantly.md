---
title: "WiFi card (AR5416) resets constantly"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by haleleonj on 2013-01-06
```
00:08.0 Network controller: Atheros Communications Inc. AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn] (rev 01)
```My Wireless connection works... for about 10 seconds then auto-magically shuts off and then reconnects in the circle of wireless life. How can my wireless card gain enlightenment to break the cycle of death and rebirth? Is there a seven-fold path? Are there any noble truths to be aware of? Or is some dark process in the way?

---

### Post by haleleonj on 2013-01-14
I looked at another thread and apparently Ubuntu does not support this card. The solution appears to be to use a more libertine open source OS, as I found this card to be reported to work on the FSF website. I'll let others know if I can get it to work with Fedora or Debian. I don't have the time to try much else.

---

### Post by haleleonj on 2013-02-01
Perhaps we will never know the true nature of this error. The card is listed as supported by all the versions of linux I have checked with an HCL. The FSF lists it as supported. I am now using Debian and the card works, but only after I moved the three antenna for greater than 50% connection strength. 

Perhaps there is a way to make the card more tolerant of low connectivity. For now Debian works, and it worked more than Ubuntu for unknown reasons, even when I neglected to adjust the antenna. At first install of Debian it would disconnect every 5 minutes not 30 seconds but the evidence suggests that the driver is simply intolerant of low connectivity around 40%.

---

### Post by haleleonj on 2013-02-23
I still have intermittent connectivity problems. I would like to know how to fix it or how to use a work around like a Windows driver. Anybody have an idea?

---

### Post by kurt18947 on 2013-02-23
> **haleleonj said:**
> I still have intermittent connectivity problems. I would like to know how to fix it or how to use a work around like a Windows driver. Anybody have an idea?

My experience with NDISwrapper hasn't been anything to brag about, spending time getting a native Linux solution working has been more productive for me.  You could possibly look at or post the output of this terminal command:

```
lsmod
```Some Atheros connectivity problems where the adapter is using the "ath9k" module are helped by adding this:

```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```

This tells the device to use software encryption rather than hardware encryption.  This won't work if the module that drives your device isn't "ath9k" of course.    The other thing you could check would be to look in the software center or Synaptic and see if there is a package with ' wireless backports' in the name.  If there is something that looks promising, you could try enabling that.  I think I'd look at the module first though.

---

### Post by haleleonj on 2013-03-10
Day one after using the fix and so far so good. I was able to update and upgrade with no difficulties. That fix seems to work with the lattest version of Ubuntu today. Unfortunately I have to try 12.04 because my new touch screen monitor doesn't seem to play well with this version of Ubuntu. I'll try this fix on the 12.04 version after I get it installed and after a few I'll report on if this is a consistent fix. Worse case scenario I use Debian again and loose the ability to use my touchscreen's full capabilities. Thank you for the help. I wish I knew hou you found it. I would never have thought there was a way to modify the basic functioning of the ath9k driver w/o advanced programming knowledge.

---

### Post by haleleonj on 2013-04-27
The problem seems to be fixed in the lattest version of Ubuntu LTS, 12.04 I think, as well.

---

### Post by nachwaal3ab on 2013-04-28
[COLOR=#000000]I looked at another thread and apparently Ubuntu does not support this card. The solution appears to be to use a more libertine open source OS, as I found this card to be reported to work on the FSF website. I'll let others know if I can get it to work with Fedora or Debian. I don't have the time to try much else.[/COLOR]

---

