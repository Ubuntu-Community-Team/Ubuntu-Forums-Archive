---
title: "Keebox wireless adapter no longer working after 11.10 upgrade"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by fishcadet on 2011-10-31
Hello.  I am using a keebox w150nu wireless network adapter.  I followed these instructions and it worked fine:
[http://ubuntuforums.org/showthread.php?t=1811605](http://ubuntuforums.org/showthread.php?t=1811605)
However, after upgrading to Ubuntu 11.10, it no longer works.  I started from scratch and followed all of the instructions that were presented in the thread, but it still doesn't work.  Any advice will be greatly appreciated.

---

### Post by IanEdwardPearson on 2011-11-20
On a fresh install of 11.10 the Keebox USB now works perfectly for me out of box with no terminal commands.  Even on the Lubuntu alternate install it was able to connect and download updates during the install.  I believe the driver being used has changed from rt2780sta to rt2800usb.  It sounds like you upgraded vs a clean install, I'm guessing that the two are conflicting somehow.  

See if they are both loaded by typing lsmod from a terminal.  I would suggest removing or blacklisting one of them.  Or if possible just do a clean install of 11.10 and it will work perfectly out of the box.  I'm pretty much a noob though so anyone please correct me if I'm way off.

If only I could get it to work in a lighter distro like Lupu 528 though. Lubuntu is still to slow for this old piii i'm playing with but that's another story.

Ian

---

