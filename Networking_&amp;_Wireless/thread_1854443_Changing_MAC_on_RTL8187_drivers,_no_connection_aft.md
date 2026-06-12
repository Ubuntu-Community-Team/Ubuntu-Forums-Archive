---
title: "Changing MAC on RTL8187 drivers, no connection afterwards"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by John Hackworth on 2011-10-04
Hello all,
To expand on the title topic: I'm having trouble with spoofing my MAC address when using the AWUS036H wireless card. The card works perfectly when the MAC address is the default one but as soon as I change it with macchanger, it has these problems:
a) can't connect to wpa/wpa2 secured networks at all
b) can connect to WEP secured network but then the connection is flaky 

I'm using Ubuntu 10.04 Lucid with the 2.6.32-33 kernel and I'm using patched compat-wireless drivers. I also tried vanilla plain compate-wireless drivers and the same thing happens. 
How do I know it's not the device itself? When I use BackTrack5 liveCD, and I repeat my experiment, I have full and perfect connectivity. Both distro's use rtl8187 drivers.

What could be the issue with Ubuntu? Could it be the kernel? I checked and BT5 runs 2.6.38 kernel, maybe the newer kernel has better wifi card support? Could it be something to do with the wpa_supplicant? Or maybe the network applet has problems? Or maybe it's actually something wrong with the driver module?

It's funny because my built-in card is an Atheros ar5007 and it has no problems at all with anything related to penetration testing, but I got the AWUS036H because of the better range and the ability to use my own antennas.

Now, I know this question will get asked, so I'll answer it before: Why? No, I don't plan to "hack" my neighbors network, however I'm majoring in CompSci and I just recently stumbled onto the whole network security branch of the field and it has me fascinated, so I set up my home lab with two routers and I've been experimenting. I'm thinking of pursuing a career in Communication Security because of this and maybe changing my major from CompSci to Network Engineering.

Any advice or tips would be greatly appreciated!

---

### Post by John Hackworth on 2011-10-04
I just wanted to give anyone interested a heads-up: I solved the problem.

After reinstalling the RTL8187 modules a few times with and without patches, after upgrading the kernel two times I found out it was... network-manager. 

I installed WICD and removed network-manager and suddenly everything works fine. It's mind boggling to me why network-manager would put up such a big fuss about a changed MAC but I'm not good enough to figure out why it's that.
Case closed.

---

