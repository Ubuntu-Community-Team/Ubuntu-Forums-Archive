---
title: "Maverick and Aircrack-ng RT2X00 problems"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by sulligogs on 2010-12-28
Hi,

I installed Ubuntu Maverick Meerkat onto an IBM T22 Laptop with an EDIMax EW-7108PCg wireless LAN card.  I installed and ran Aircrack-ng 1:1.1-1 and realised the following problems:-

**[SIZE="5"][COLOR="Red"]Problems[/COLOR][/SIZE]**

**1) **```
airdriver-ng installed
```would report **MODINFO** errors that the RT2X00 range of drivers could not be found.

**2) **```
airodump-ng wlan0 -c 6
```would show a message that the fixed channel, in this case 6, was at -1.

**3) **```
aireplay-ng -9 wlan0
```would not report **Packet Injection successful**

**4) **```
aireplay-ng -0 1 wlan0 ...
```would fail to produce a handshake between a client and its AP, no matter how much data was collected.  Related to problem 3, of course.

---

So, I found out that two fixes would have to be made.  These are:-

**[SIZE="5"][COLOR="Green"]Fixes[/COLOR][/SIZE]**

**[SIZE="6"]1) [/SIZE]** According to a forum post over at **[http://trac.aircrack-ng.org/ticket/702]("http://trac.aircrack-ng.org/ticket/702")** there is an incorrect modules reference at line 2659 in **/usr/sbin/airdriver-ng**.  Change that line to ```
if [ x"modinfo "$KMOD/$modfile" | grep "${DMODINFO[$1]}"" != x ]
```

**[SIZE="6"]2) [/SIZE]** Use a kernel between 2.6.30-x and 2.6.34-x.  I added the **Main** repository for Lucid Lynx to my system and installed **linux-image-2.6.32-21-generic**.  After a reboot and choosing that kernel to boot from, all of the above problems went away.

---

