---
title: "wireless issues also"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by Pilot22 on 2011-05-25
I have n HP DV4 with a Broadcom BCM4322 wireless card. 
When I have the Ubuntu Live CD in, the wireless works. When I install and reboot, it does not. I do not have a Windows install disk, but I have downloaded a windows driver but am unable to get that working. I have tried many of the fixes listed on this forum, and none has worked. 
Does the 4322 use different firmware than the other BCM 43XXX cards? Also, I am in the middle of reinstalling, as one of the "fixes" made my system unstable, so I can not do any commands right now to test the card. But during installation, the wireless is working fine, using the Live CD. Is there a file I can take from the CD to make my card work once I have installed?

---

### Post by TBABill on 2011-05-25
Yes check [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) in the section for STA- no internet access. You can do it right from the LiveCD using it as a repo.

---

### Post by Pilot22 on 2011-05-25
Here is what I get when I check my card...

~$ lspci -vvnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

When I am using Live CD, I can go to "Additional Drivers"  -> Broadcom STA wireless driver -> Activate and it runs and asks me to reboot to finish the install... But once I have Ubuntu 11.04 installed and activate the driver, I get the message that it can not install. I checked the /var/log/jokey.log I get this message:
2011-05-25 12:36:34,695 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

I found a thread earlier on how to remove drivers from blacklist, but can not find it again right now. 

I have the windows driver, but it will not load. I tried using Wine to run it, but that did not work, and I have re-installed since then, to clear up problems that this may have had a part in creating. I am somewhat of a Linux noob, but I can follow instructions well and learn fast.

---

### Post by Pilot22 on 2011-05-26
Got the issue fixed, although not elegantly. 
I went back to a previous distro I had on disk (9.10) and that one was able to install my broadcom drivers. Then I went through 4 hours of upgrades and the wireless has worked since.

---

