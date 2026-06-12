---
title: "USB Wifi adapter / Wireless networking"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by Spasysheep on 2009-04-01
My wireless network was running fine until ~2 days ago - I got home from school, booted up my PC to XP x64 and the wireless network said it was working fine, the router responded to ping, but no internet. Reboot computer, all is fine, except I occasionally have to go through the "Repair Connection" process to kick it back to life. 

I installed Ubuntu 8.04, which I had been meaning to do for a while after a failed experiment with Linux Mint (Install always crashed with a disk IO error at 61%, no matter how many CDs I burned, or what write speed, etc. But that's a matter for a different thread). Similar problem in Ubuntu, except router doesn't respond do ping and there is no visible equivalent to the "Repair Connection" process.

I am writing this from my secondary computer, through the same physical adapter (I have to switch it between PCs as and when it's needed), and it's working fine

Any ideas?

P.S. This wifi adapter has always worked flawlessly in both ubuntu and windows before, and no other PCs on the network are having this problem

P.P.S The adapter is a TP-LINK TL-WN-321G

---

### Post by freonchill on 2009-04-01
if you are having the same problem with 2 different OS (especially with two different driver/driver methods)

perhaps that the card itself might be failing

since you have the same card in another machine, you might want to try swaping the hardware and seeing if you have the same problem in another machine. if you do not have the same problem on the second machine, try another USB port on the first machine.

---

### Post by kikykuang on 2009-04-01
agree with freonchill

You should to check your netcard on other computer, it seems the netcard some wrong

---

### Post by wkulecz on 2009-04-02
If it was working and then gets slow and/or flakey, change the channel on your access point and clients.  Wireless is in an unregulated frequency band, a new source of interference may have came on-line recently.

Unless the interferer is exceeding legal transmitter power, your only recourse is too find a different frequency.

I agree it could also be a partial hardware failure if changing channels doesn't help at all.  

--wally.

---

### Post by superprash2003 on 2009-04-02
in your terminal type **sudo dhclient eth0** where eth0 is the wireless interface

---

