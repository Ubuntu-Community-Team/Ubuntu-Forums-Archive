---
title: "Netgear WN311B freezes computer"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by Aryding on 2010-03-04
I have been using 64-bit 9.10 and 10.04 (alpha 3) and have had no luck in getting my WN311B to work.  I have attempted to use Ndiswrapper, b43, and Broadcom STA drivers with no luck.  The only drivers that did work, momentarily, was Broadcom STA.  However, the STA drivers freeze the computer after 5-30 mins of use.

Any ideas?  I'm very frustrated and have followed numerous tutorials on the WN311B, but since I'm using a 64-bit OS I don't think my drivers are correct?

Thank you for your help,
aryding

---

### Post by Aryding on 2010-03-08
Bump, any ideas?  Is there anyone else out there in the same situation?  I might have to buy a new wireless card, does anyone recommend a good N-card?

---

### Post by elderly_punk on 2010-03-14
Hi.   I'm having the exact same problem.   Using 64 bit Ubuntu 9.10 with the WN311B.  Tried all the same things as you, I'm sure.   Took the drivers from a Windows7 64 bit system, but couldn't get them to work with ndiswrapper.   Broadcom STA restricted drivers do work sort of reliably, but I do get system freezes anywhere between 15mins and 2-3hrs after boot.   It seems like whenever I try to upload or download a large batch of files to my NAS it triggers the problem.   Up until the freezes, everything seems ok.    If I manage to resolve it, I'll post back here...  Please do the same if you find anything.  I have a feeling we may be out on an island with this one...

---

### Post by elderly_punk on 2010-03-16
Hi again....    I reverted to Ubuntu 32bit, and everything is working fine with the Broadcom STA drivers.   No freezing or anything.   I hate to go back to 32, but it's my wife's machine and all that matters is stability and reliability....  Hopefully when Ubuntu 64 is more ready for prime-time we can move back.   Since the WN311B is such a good wireless card (the only one that has worked in my metal-frame condo building), the downgrade is probably worth it...

---

### Post by B.C. on 2010-04-30
Elderly, it's not Ubuntu's fault that the hardware manufacturer refuses to release a stable driver for 64-bit Linux. Blame Broadcom  for not releasing drivers and Netgear for using Broadcom chipsets, not 64-bit Ubuntu.

---

### Post by tgalati4 on 2010-04-30
Right after a freeze, quickly pull the card and feel it.  If it is quite warm, then it's possible that the 64-bit drivers are causing an overheat condition.  This would cause random shutdowns when moving a lot of files.

Send an email to broadcom and to netgear describing your experiences.

---

### Post by B.C. on 2010-04-30
I forgot to mention that I installed Kubuntu 10.04 64-bit on my workstation today and both my Nvidia video card and WN311B wireless card are detected. The proprietary Broadcom STA driver downloads and installs without issue. It seems to work just fine on my 802.11n network, which is secured by WPA2 encryption.

I have a fan in my case which provides ample airflow to my PCI cards, so perhaps the issue is truly one of overheating as the previous poster suggests.

Note: to download the drivers for the respective cards, I had to initially plug the machine into a wired network, but everything worked as intended and I can work in my home office without a 50-foot cable strung across the living room.

---

### Post by mrdoob on 2010-05-01
Same problem here. With a WPN311 after 5-30 min of internet connection the system freezes. It didn't do that on 9.10 64-bit :(

I'll try 10.04 32-bit...

---

### Post by mrdoob on 2010-05-01
So far 32-bit seems to be the solution.
Big pheew!

---

### Post by mrdoob on 2010-05-01
No. It still hangs. Reverting to 9.10 64-bit (or something...)

---

### Post by tgalati4 on 2010-05-01
Put your finger on the network card chip during use (if you can).  If you can't keep your finger on it for 30 seconds then it is running too hot.  This could either be a driver issue or a defective card.  When transisters turn into resistors they give off more heat and tend to lock up your system.

---

### Post by VeeDubb on 2011-08-22
I hate to resurect and ancient thread here, but I didn't find this before buying a WN311B last week, and I'm getting the same thing.  Were you ever able to find a solution?

---

### Post by mikewhatever on 2011-10-10
> **VeeDubb said:**
> I hate to resurect and ancient thread here, but I didn't find this before buying a WN311B last week, and I'm getting the same thing.  Were you ever able to find a solution?

That appears to be a long standing bug, apparently, very hard to diagnose, cause nothing is logged. The Broadcom STA driver seems to be the cause, and it being closed source probably doesn't help.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/292450](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/292450)

[https://bugzilla.redhat.com/show_bug.cgi?id=624212](https://bugzilla.redhat.com/show_bug.cgi?id=624212)

I guess the best you can do is file another bug report:
```
ubuntu-bug bcmwl-kernel-source
```

Another option is to try the latest driver from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Update: Here is another bit of info that might help:
[http://bigbrovar.aoizora.org/index.php/2011/04/30/turning-wireless-on-causes-laptop-to-freeze-on-ubuntu-11-04-natty-narwhal-my-work-around/](http://bigbrovar.aoizora.org/index.php/2011/04/30/turning-wireless-on-causes-laptop-to-freeze-on-ubuntu-11-04-natty-narwhal-my-work-around/)

---

