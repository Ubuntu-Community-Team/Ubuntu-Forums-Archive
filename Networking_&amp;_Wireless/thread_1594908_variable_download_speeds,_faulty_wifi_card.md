---
title: "variable download speeds, faulty wifi card?"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2010-10-12
I'm having a variety of problems getting a new PC working properly, getting a reliable wifi connection is one of them. Earlier today I upgraded to 10.10 using my wife's account and download speeds were frequently at a reasonable 800kbps at times. This evening my son complains about the slow speed and a test shows 133kbps download with 616kbps upload. My own PC connected by wire to the router works OK.

A couple of days ago this problem seemed resolved when I installed Wicd but didn't configure it. I thought Network-Manager would have been removed but was still present. However, a downloads test showed 6Mbps. After today's upgrade slow downloads have returned.

I'm currently using this PC with a wifi link to the router and am connected to the Forum. If I hover the mouse pointer over the N-M toolbar symbol a window opens saying-

Wireless network connection 'Auto MYESSID'active:MYESSID(67%)

If I right mouse click on the N-M symbol and select Edit connection... the wireless window reports that I was last connected 3 days ago. My own PC's wired connection window says against Auto eth0 that I've never used this. Both these are untrue. I wondered if having a hidden ESSID doesn't help?

I'm left thinking that the rt2500 based wifi card needs replacing. We're some distance from other houses.

Any other explanation?

---

### Post by Handssolow on 2010-10-12
I've installed Wicd and removed Network Manager. I've connected to the wifi router but I've no broadband speed test results to report because I'm having to wait too long. I've managed to get onto the Forum at least.

---

### Post by Handssolow on 2010-10-13
It's no better this morning, speeds are so slow I can hardly log into the Forum. I noticed the following in the messages log.

DDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
type=1400 audit(1286957799.031:16): apparmor="DENIED" operation="open" parent=1554 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=1582 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

Edit:

I'd had enough of my Belkin rt2500 pci wifi card and bought a new one. It's a Micronet and cost less than £18
"sudo lshw -C network" gives this
RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
driver=rtl8180

Download speeds are 6472 kbps upload 644 kbps

I notice the link quality is about 14/100 and signal level 14/100 whilst the old Belkin was higher, perhaps 40/100 at times. If I change the aerial stick for a desktop aerial the link quality and strength are still 14/100. If I remove the aerial all together I lose connection to my router so the aerial socket isn't isolated. Anyway connection speeds are acceptable even though the link quality and strength seem low.

Edit 2
The low link quality and signal are a known issue. Launchpad Bug #275230

---

