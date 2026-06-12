---
title: "D-Link AirPlus DWL-520+ Configuration Problems"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by Ghostcool on 2006-06-30
Hello.

My problem is the following:

I'm using a DWL-520+ Wireless board, in my Ubuntu 6.06 (ACX100 Chipset.
It identifies my wireless board, captures the signal of my city's wireless networks, and use the correct DNS Server, but it can't do any connection with the internet. I've already configured the correct ESSID, have seen that the DNS Server that the board identifies is the same my Windows XP uses, and have disabled the IPv6, but I still can't use my internet connection.
I've not configured any encryption key, since my connection doesn't uses any key.
I'd like to share this doubt with the Ubuntu community, and I'm lookin' for a solution. I'm crazy for use Ubuntu all my time, but I can't do this without a internet connection.

Waiting some kind of help.

---

### Post by Ghostcool on 2006-07-01
UP.

C'mon people. I need this.

---

### Post by Neky on 2006-10-26
Can you write how you have configured wifi card and all that? My ISP uses PPPoE with username and pass. Does that make any diference in configuration steps? I have the same card ( and chipset ofcourse ) and the same Ubuntu version.

Thanks in advance, Neky, Serbia.

---

### Post by jpeddicord on 2006-10-26
I reported a bug on this some time ago; it is confirmed and awaiting a fix.

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/66176](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/66176)

Try right-clicking on the panel, and adding "Network Monitor" to it. Watch it closely for a few minues, and then you will notice that a little red X pops up on it every few seconds. It seems to disconnect whenever it wants.

---

