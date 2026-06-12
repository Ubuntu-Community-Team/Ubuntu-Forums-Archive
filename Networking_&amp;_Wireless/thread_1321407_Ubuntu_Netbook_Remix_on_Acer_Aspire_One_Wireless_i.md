---
title: "Ubuntu Netbook Remix on Acer Aspire One Wireless isn't working"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by tricky2511 on 2009-11-10
First of all I am a mostly newbie with Linux and second I installed the ubuntu remix last night.

I was really looking forward to the fact that it has Firefox 3.5 (previously I had the Linpus Linux on it and couldn't update the Firefox but back to my problem) I had fully installed the OS and found that the Wireless wasn't working been looking everywhere and can't find anything to help found some walkthrough's but they don't work.

All I know is it is an Acer Aspire One ZG5 with wireless Atheros AR5BXB63. If anyone can help me I would appreciate it. Did I mention I am not great when it comes to advanced stuff like the commands it took me 20mins to locate the terminal.

Also I went into the System Testing and tested the Networking and it reported this AR5001 I hope this helps a little more.

Thanks again

---

### Post by AntiEgo on 2009-11-10
I'm interested in this one as well. 9.10 and 9.4 detected that NIC on my ACER ONE just fine, but a week or two after installing, the card has just stopped working. (I can see it if i boot from the thumb drive i installed it with though.) It no longer shows up in the list of adapters in ifconfig. I'm not sure what is causing this. My kids use the laptop (without sudo/wheel perms) vut i can't think of how the system might have changed.
I upgraded to 9.10 nbr hoping it would fix the issue, but it has reappered. My linux hardware troubleshooting experience is like 5/10, so thanks in advance to any good souls who can shed light on this.

---

### Post by pdc on 2009-11-11
try this guide

[http://www.hpminiguide.com/forums/viewtopic.php?t=1507](http://www.hpminiguide.com/forums/viewtopic.php?t=1507)

by choosing to install 9.10, you installed new software: new software is new; that means some of the unknowns are unknown; by installing new software, you help to discover the unknown; it may even have problems; I'm not sure everyone realises that ..............

---

### Post by virtigo311 on 2009-11-11
I was searching for the same thing and came across this thread:
[http://ubuntuforums.org/showthread.php?t=1305812&highlight=atheros+ar5bxb63](http://ubuntuforums.org/showthread.php?t=1305812&highlight=atheros+ar5bxb63) 

Essentially you open terminal > *sudo gedit /etc/modprobe.d/blacklist-ath.pci.conf *
Then you find where it says blacklist ath5k (however in mine it actually said *blacklist ath_pci*
(forgive me for using Gedit, i'm still a n00b)

I put the # in front of the *blacklist ath_pci* then saved and rebooted and was able to connect to my wireless.


Hope this helps, if not I suggest hitting the other thread as they are much more knowledgeable about this than I am.

---

### Post by kmartinson on 2009-11-19
My wireless was not recognized after upgrading to 9.10 UNR on my AAO ZG5.  Tried a number of fixes with no luck.  Did a fresh install of 9.10 UNR this morning and the wireless was recognized and working by default.  Just sayin'

---

