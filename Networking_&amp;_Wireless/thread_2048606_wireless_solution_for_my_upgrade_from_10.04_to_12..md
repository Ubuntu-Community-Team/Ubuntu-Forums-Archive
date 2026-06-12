---
title: "wireless solution for my upgrade from 10.04 to 12.04.1, Ralink USB dongle"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by thumbsoup on 2012-08-26
Just recording this in case someone else out there has this same problem. In short, my old solution for getting my specific wireless usb device to work with Ubuntu 10.04 ended up blocking my wirless connection when I upgraded to 12.04.1. Removing part of that old solution solved it.

I have an ALFA brand 802.11n USB wireless dongle for my desktop.  Based on the Ralink 2870 aka rt2870 / 3070 / rt3070

I installed this wireless USB device back when I was running Ubuntu 10.04, and it required some additional work and drivers at the time.
The solution back then with 10.04 was in part to  add rt2800usb to the blacklist.conf file.

So in my etc\modprobe.d\blacklist.conf
I included the line (without the #):

# blacklist rt2800usb

Fast forward a few years, and now I have upgraded to Ubuntu 12.04.1.  Wireless stopped working immediately.

I read a lot of posts and tried a lot of different things.  To sum up, the solution seems to be  remove (or # out ) the blacklist for rt2800usb and reboot.

One other thing I tried earlier was to enter at the terminal command line:

# sudo modprobe rt2800usb

Which did, in the words of the old post which suggested it, cause my wireless connection to "spring to life." But it would fail again as soon as I rebooted.  Undoing the blacklist seems to be the solution.

---

