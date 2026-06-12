---
title: "Wireless encryption problem?"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by chocodum on 2012-01-22
I can't seem to establish a wireless Internet connection with my router. It seems my computer is avoiding it whenever possibly while trying to connect to it by automatically switching to a different network and then issuing a "Failed to connect to [different network name] report" a few times before finally giving up. Even selecting the network changes it to a different one.

Also, this never happens when I connect to a non-encrypted network.

---

### Post by UltimateCat on 2012-01-22
Depending on your case having a laptop or a desktop pc my network problem was similar to yours.  I could see my network and about 5 other peoples as well.
It didn't change to another user tho-

When your Authentication Required by Wireless Network manage comes up type in your key; click connect; shut down your computer and re-boot.  This solved my problem.

Also, go through your Network Manager and make sure your SSID, Key and etc. are all set up correctly.   I left one of the fields blank and couldn't get online. DHCP I set to automatic but when I changed it to manual and put the information in it helped. I had to blacklist a driver as well.(rt2800)
Also; I had to install a driver for my NIC that may be your case but I honestly do not know.
Open a terminal and post
```
ifconfig

```
Other member can read the output and tell you better than I can.
```
 iwconfig

```
Command " lspci " is a command for displaying information about all PCI buses in the system and all devices connected to them.  It's useful when you want to diagnose problems or when you want to report bugs related to PCI devices.
You can try:
[http://help.ubuntu.com/community](http://help.ubuntu.com/community)

[http://ubuntuforums.org?showthread.php=1464255](http://ubuntuforums.org?showthread.php=1464255)     (This helped me)

[www.linuxquestions.org](www.linuxquestions.org)

Hope this helps.

---

