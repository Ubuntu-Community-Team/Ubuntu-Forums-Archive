---
title: "Neither Broadcom B43 nor STA driver is working."
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by Xephyrind on 2010-01-23
Hi I just deleted my windows XP and installed Ubuntu 9.10 earlier this morning. I used wired connection to get drivers for my wireless network card.

When I did lspci, the very last line states:

Network Controller: Broadcom Coporation BCM4311 902.11b/g WLAN(rev 01)

I used the System -> Administration -> Hardware Driver and found 2 drivers. I have tried them both to connect to my D-Link Router. Neither of which worked.

For Broadcom B43 Driver, the wireless is able to detect wireless networks. However, it fails to establish connection.

For Broadcom STA Driver, the wireless cannot even detect wireless networks available.

What is the issue here and how do I resolve it so that I am able to connect onto the internet wirelessly?

---

### Post by bkratz on 2010-01-23
Well the STA driver is supposed to be the right one. Don't know why it doesn't work for you, most people have had a lot of success.  Maybe it is time for a different approach. This seems to work well for most, of course so did the STA!

[http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318)

---

### Post by Xephyrind on 2010-01-23
yeah back in 2008 when ubuntu was still at version 8.xx, I tried it on this laptop with STA driver, things actually went along fine. I don't know why 2 years later this time, STA driver is failing me T_T... That's why I am seeking for assistance.

---

### Post by Kafubie on 2010-01-23
I got help with that once, i had the same drivers.  You just check for updates and install all of them.  Then you reboot, then activate the STA driver. Reboot again.
SUCCESS!  Easy as pie

---

### Post by Xephyrind on 2010-01-24
> **Kafubie said:**
> I got help with that once, i had the same drivers.  You just check for updates and install all of them.  Then you reboot, then activate the STA driver. Reboot again.
SUCCESS!  Easy as pie

what do you mean check for updates and install all of them?.... Here's what I did

With wired connection before I go into Hardware Driver and click activate on STA driver, I do an sudo apt-get update.

After that, I click activate on STA. Is that what you mean by installing all the updates then activate STA driver? If not, please enlighten me.

---

### Post by PRC09 on 2010-01-24
The following may give you some help with Broadcom cards if you havent already tried........

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Xephyrind on 2010-01-24
> **PRC09 said:**
> The following may give you some help with Broadcom cards if you havent already tried........

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

T_T didn't work... His step is pretty much the same as mine Thanks though. Any other ways?

---

### Post by pertti on 2010-01-24
I have been suffering this problem since I installed Karmic (it had been working perfectly with previous versions of Ubuntu), and I just solved it...

Try this: install the STA driver and then reboot (my GNOME session froze after installing the driver, by the way). After logging in, use your keyboard special shortcut to activate/deactivate the wireless card (there should be one on almost every laptop, mine is Fn + F2). After that, Network Manager showed me the available wireless networks.

I never thought of that, because after installing the STA driver I always saw the wireless LED light up, and I assumed that it was already on.

---

### Post by efflandt on 2010-01-25
Broadcom STA works for BCM4311 on a few year old Dell work laptop, but is apparently very weak (sometimes cannot get a signal where other laptops and wireless devices work fine).  So it might be a signal strength issue.  Disabling that and using Linksys USB54GSC works much better (stronger signal, supported by standard kernel modules).

The same 64-bit Ubuntu 9.10 booted from USB hard drive on a new Dell I was setting up for someone works much stronger using Broadcom STA with BCM4312.

---

### Post by Xephyrind on 2010-01-26
> **efflandt said:**
> Broadcom STA works for BCM4311 on a few year old Dell work laptop, but is apparently very weak (sometimes cannot get a signal where other laptops and wireless devices work fine).  So it might be a signal strength issue.  Disabling that and using Linksys USB54GSC works much better (stronger signal, supported by standard kernel modules).

The same 64-bit Ubuntu 9.10 booted from USB hard drive on a new Dell I was setting up for someone works much stronger using Broadcom STA with BCM4312.

Alrighty tried everything stated above still didn't work with STA. I guess you are saying that I should get a new network card or USB wireless called Linksys USB54GSC correct?

---

### Post by nwstephens on 2010-01-27
I guess I'll join the pity party here.  I have an old Dell E1505 (laptop) with Karmic.  The wireless networks appear, but fails to connect.  I've tried two drivers thus far.  Any tips would be greatly appreciated.  If not, I think I'll downgrade Ubuntu.

---

### Post by Xephyrind on 2010-01-27
> **nwstephens said:**
> I guess I'll join the pity party here.  I have an old Dell E1505 (laptop) with Karmic.  The wireless networks appear, but fails to connect.  I've tried two drivers thus far.  Any tips would be greatly appreciated.  If not, I think I'll downgrade Ubuntu.

mind teaching me how to downgrade? I don't know where I can get the older distribution, if that's what you meant by downgrade~

---

### Post by Xephyrind on 2010-01-28
T_T still not resolved.... help someone?

---

### Post by Xephyrind on 2010-01-29
problem solved thanks to ndiswrapper and linuxwireless.org driver and walkthrough what not....

---

