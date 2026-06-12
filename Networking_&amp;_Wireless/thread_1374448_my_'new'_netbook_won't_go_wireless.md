---
title: "my 'new' netbook won't go wireless"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by linuxhippy on 2010-01-06
I just bought an almost new netbook with the Ubuntu 9.10 netbook remix on it.  It's made by System76 and was designed to work with Ubuntu.  I downloaded Xubuntu-desktop and wicd and it now has a lot of software on it.  It connects to the internet easily with a wired connection, but I cannot get it to find an ip address on my unencrypted home wireless network...it does see my network, though.

I don't see the name of the hardware when I type sudo lspci.  How can I find what chipset I have for my wireless device?  Any ideas of how to get online wirelessly?

---

### Post by linuxhippy on 2010-01-07
got it working.  The ubuntu netbook remix I had did not have dhcpcd installed and this is what was needed.  I did this:

sudo aptitude install dhcpcd

Once installed I set the preferences in wicd (which I also installed with aptitude) to use dhcpcd instead of automatic.

---

