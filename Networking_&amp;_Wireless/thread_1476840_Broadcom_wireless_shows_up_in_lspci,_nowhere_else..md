---
title: "Broadcom wireless shows up in lspci, nowhere else."
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by brucewestfall on 2010-05-08
Ubuntu 10.04 fresh install 64bit

Wireless was working in 9.10, now does not even show up in restricted drivers.  Installed bcwl-kernel-source, and b43-fwcutter

ifconfig, iwconfig only show eth0 and lo - no wlan

Other restricted drivers show up - using NVIDIA driver with Compiz running better than ever on 2 screens :)

Here is the output from the collectNWData script found at [http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English)

I do notice that in the firmware section that both b43 and b43legacy are listed.  Somewhere I reads that I should be using b43 - not the legacy version.  Should it be blacklisted?

---

### Post by brucewestfall on 2010-05-10
Ubuntu is absolved again!

The whole problem was HARDWARE.  I was so worried about Linux messing up, but it looks like it is something on the motherboard, or perhaps the BIOS itself.

My apologies to all who tried to help me.

Unfortunately, I must go apologize in another section of the forum, since there were several problems going on at the same time.

Please forgive me.

---

