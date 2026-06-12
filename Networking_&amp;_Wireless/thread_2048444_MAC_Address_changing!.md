---
title: "MAC Address changing!"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by carrett on 2012-08-26
Hi all, I have an Edimax EW-7128G (uses the rt61pci driver).

My problem is that the card's MAC address changes on each reboot, therefore things like auto-connect don't work and also my interface changes every time (it's up to wlan12 now).

Here are some of the MAC addresses that have shown up:

00:0F:1F:C7:E4:39
00:1F:1F:CF:F4:39
00:1F:0F:CF:E6:39
00:1F:1F:8F:F0:3F
00:0F:0F:87:F0:1F
80:1F:0F:CF:F0:3F
80:1F:0F:CF:F0:3F
00:0F:0F:87:E6:3F

The "correct" MAC address, which shows up in Windows on every reboot, is 00:1F:1F:8F:E4:3B.

Any clues on how I can force a constant MAC for this card? Thanks!

---

### Post by carrett on 2012-08-27
Two new ones:

00:0F:9F:87:F0:3F
00:1F:9F:8F:F0:3F

I don't know how/why the system is generating a new one every reboot for this device. Any clues? Is it udev? The kernel? Which log should I check? Any help greatly appreciated!

---

### Post by carrett on 2012-08-28
Alright, last bump before I give up. Here is the address that shows up in Windows every time, even after reinstalling Windows:

00:1F:1F:8F:E4:3B

Any clues at all are appreciated. I want to keep using Ubuntu, but not if hardware doesn't work correctly.

---

### Post by redmk2 on 2012-08-28
> **carrett said:**
> Alright, last bump before I give up. Here is the address that shows up in Windows every time, even after reinstalling Windows:

00:1F:1F:8F:E4:3B

Any clues at all are appreciated. I want to keep using Ubuntu, but not if hardware doesn't work correctly.

I feel your pain.  Unfortunately I don't really have an answer.  I do, however, have a clue for you.  See [**_[COLOR="Blue"]here[/COLOR]_**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478297") for a bug report of this problem and a workaround that might help you.

---

