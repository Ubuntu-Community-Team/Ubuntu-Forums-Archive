---
title: "Wireless slow to connect"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by AllanP on 2010-02-23
I have a Dell 1747 laptop. Once I'm connected all works fine but, sometimes it takes forever to make connection. First I have to give Keyring password then I wait; some time goes by and the Wireless key with info filled out appears. I hit enter and it may come up again in a few minutes. I try disconnect and re-connect and eventually it connects and then it's great. Oh yeah it's fine on that other OS$$.
I'm wondering about this "ndiswrapper" thingy; would that help?
Here's a few bits of info:
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
allan@allan-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
allan@allan-laptop:~$ lspci | grep Broadcom
08:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
allan@allan-laptop:~$ lspci -n | grep '14e4:43'
08:00.0 0280: 14e4:4353 (rev 01)

---

### Post by johnrobert on 2010-05-14
AllanP, did you ever work out a solution to this problem? I have a very similar situation, same laptop and same Broadcom card.

---

### Post by AllanP on 2010-05-14
> **johnrobert said:**
> AllanP, did you ever work out a solution to this problem? I have a very similar situation, same laptop and same Broadcom card.
No I didn't and I've tried other distros. There are problems with every one I've tried either with wireless connectivity or boots to blank screen. I have pretty much accepted Win7 for my needs on the laptop (PC remains 75% Linux) which works just fine.
GLTY

---

### Post by johnrobert on 2010-05-16
I finally seem to have mine working, though it just seems to be a matter of luck and happenstance. 

Following instructions I found in some thread or other I opened /etc/NetworkManager/nm-system-settings.conf. Inside that file I edited the entry that read "managed=false" to be "managed=true", then rebooted.

That didn't work. It didn't seem to have any effect at all. So I changed the setting back to "managed=true" and rebooted. And what I found then was that after my home wireless network failed to auto connect, it would connect reliably when I just chose it out of the list of available networks. So I reset my preferences in Network Manager to not attempt an auto connect, and it has reliably connected manually ever since.

I have no idea if this will help you at all, but my Dell Studio 1557 with the Broadcom 4353 is now reliably connecting under Ubuntu 10.04.

---

### Post by AllanP on 2010-05-16
> **johnrobert said:**
> I finally seem to have mine working, though it just seems to be a matter of luck and happenstance. 

Following instructions I found in some thread or other I opened /etc/NetworkManager/nm-system-settings.conf. Inside that file I edited the entry that read "managed=false" to be "managed=true", then rebooted.

That didn't work. It didn't seem to have any effect at all. So I changed the setting back to "managed=true" and rebooted. And what I found then was that after my home wireless network failed to auto connect, it would connect reliably when I just chose it out of the list of available networks. So I reset my preferences in Network Manager to not attempt an auto connect, and it has reliably connected manually ever since.

I have no idea if this will help you at all, but my Dell Studio 1557 with the Broadcom 4353 is now reliably connecting under Ubuntu 10.04.

Thanks I'll give that a whirl. I loaded Suse on that partition and couldn't get wireless at all; so will try Ubuntu again.

---

### Post by AllanP on 2010-05-17
> **johnrobert said:**
> I finally seem to have mine working, though it just seems to be a matter of luck and happenstance. 

Following instructions I found in some thread or other I opened /etc/NetworkManager/nm-system-settings.conf. Inside that file I edited the entry that read "managed=false" to be "managed=true", then rebooted.

That didn't work. It didn't seem to have any effect at all. So I changed the setting back to "managed=true" and rebooted. And what I found then was that after my home wireless network failed to auto connect, it would connect reliably when I just chose it out of the list of available networks. So I reset my preferences in Network Manager to not attempt an auto connect, and it has reliably connected manually ever since.

I have no idea if this will help you at all, but my Dell Studio 1557 with the Broadcom 4353 is now reliably connecting under Ubuntu 10.04.

OK installed 10.04 and all went well. I did as you and it is much faster; not as fast as Win7 connection, but a lot faster than before.  It took about 45 seconds to connect. Thanks, Allna

---

