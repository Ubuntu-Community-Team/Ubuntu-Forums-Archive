---
title: "Installing Wireless - Compaq Evo N610c"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Sniperfish on 2009-01-25
Hello,

I am a linux newbie.  I have installed Ubuntu 8.04 on a Compaq Evo N610c laptop to have a play and learn how to use the OS.  I've been working through the following instructions on the below site to try to install the Wireless adapter.

[http://wiki.ubuntu.org.cn/UbuntuHelp:WifiDocs/Device/CompaqW200]("http://wiki.ubuntu.org.cn/UbuntuHelp:WifiDocs/Device/CompaqW200")

I had done everything that it said, I thought successfully, however when I came to the final item to load the driver to the kernel
[INDENT][/INDENT]sudo modprobe -v orinoco_usb

I receive the following error from Terminal:
[INDENT][/INDENT]bev@bev-laptop:~/usb/firmware$ sudo modprobe -v orinoco_usb
[INDENT][/INDENT]FATAL: Module orinoco_usb not found.

Could anyone please advise why this would be the case?

---

### Post by Sam Lars on 2009-01-25
If you haven't, I'd try the part about adding to the /etc/modules and restarting.
Otherwise, I think the sudo make install line didn't work like it should have...

---

