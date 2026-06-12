---
title: "support for both new Atheros card and nvidia? NIGHTMARE!"
date: 2006-05-25
forum: Multimedia &amp; Video
---

### Post by SqRt7744 on 2006-05-25
Hello,

I have recently replaced the aging Intel 2100 wifi card in my laptop with a new Atheros card which is awsome and has great reception and speed.  The exact info from lspci (after update-pciids):

0000:02:0a.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)

and 

0000:02:0a.0 0200: 168c:001b (rev 01)

I could only get the card to work by compiling the latest madwifi-ng from source... my gripe, however, is that I had to uninstall the restricted modules package.  So no nvidia.  I fixed this by installing the nvidia driver from their install script (d/l from [http://www.nvidia.com/page/home.html](http://www.nvidia.com/page/home.html)), but now:

-every kernel update requires reinstall of nvidia driver package + recompilation of madwifi-ng
-version of NetworkManager included in the repos doesn't work with this card and/or latest madwifi-ng driver
-to get gdm to start at all (i.e. after EVERY reboot, luckily this is only a weekly occurance, but still sucks) I have to:
a) log in to terminal, since gdm falls on its face with
Major opcode of failed request: 143 (GLX) as printed in /var/log/gdm/:0.log
b) REINSTALL the blasted nvidia driver (the one from their page) to fix above error
c) /etc/init.d/gdm restart, and once logged in:
d) thefuture command flops out taking metacity with it printing
"GLX_EXT_texture_from_pixmap is missing", so i have to open a terminal and type
metacity&
sudo dpkg-reconfigure libgl1-mesa
e) run thefuture again.

and all that after every reboot!

So not to be a whiner, but when can I expect the included version of the restricted modules to support my atheros card?  This would fix EVERYTHING!

If there is a better way to get my computer up, can someone please point it out to me?  Thanks!

---

### Post by SqRt7744 on 2006-05-31
ok, if anybody is having the same problems as me, I have found a work around.  I've reinstalled the linux-restricted and nvidia-glx packages, and then installed madwifi-ng from source, leaving the restricted packages in place.  During the install of madwifi-ng "make clean", "make", "make install", you are asked if it should replace the madwifi driver it finds.  "YES" is the answer I chose.  To manage the wifi network, I find that wlassistant works very well.  If anyone would like more detailed instructions, just post here!

---

