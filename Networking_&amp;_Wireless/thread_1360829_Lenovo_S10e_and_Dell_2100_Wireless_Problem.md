---
title: "Lenovo S10e and Dell 2100 Wireless Problem"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by sobrien on 2009-12-21
I have had a problem with wireless networking with Ubuntu 9.10 (Karmic Koala) on the Lenovo S10e and the Dell 2100 netbook computers.  Both appear to use the Broadcom 43xx chipset.  This is what finally worked for me:

1)  Connect the machine to a hard wired Ethernet connection.  Be sure the connection is working by browsing to a web site or something like that.

2) Click on System/Administration/Hardware Drivers and Activate the "Broadcom B43 Wireless Driver".

3)  Open a terminal window by clicking on Applications/Accessories/Terminal
In the terminal window, enter:
sudo apt-get install bcmwl-kernel-source

4)  Reboot the machine.  When mine came back up it saw the wireless networks in my area AND I was able to connect to a hidden wireless network that uses WPA security, something I have not been able to do for quite some time.

Note that this solution worked on the standard desktop install of Karmic, and also on the Netbook remix.

---

