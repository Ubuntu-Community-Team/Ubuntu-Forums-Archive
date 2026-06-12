---
title: "Atheros 802.11/ Ubuntu 8.10/ Compaq CQ50Z Laptop"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by giantsfan7791 on 2009-01-01
So I've tried just about everything and I can't get this wireless to work at all. When I plug in an ethernet cable, I can connect. However, when I click on the network button, it doesn't show any wireless networks, even though my laptop is next to my router. I have installed and enabled the hardware drivers via Ubuntu's built-in manager. I have also completely updated my system, but this is a fresh install otherwise. Here's what I get when I do lspci:

```
bryant@bryant-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation Device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation Device 0845 (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Please help, sorry I don't know much about this. I've tried a few guides from google searches but nothing's worked on my computer so far.

---

### Post by melojo on 2009-01-01
have you looked here?
[http://ubuntuforums.org/showthread.php?t=967654&page=4](http://ubuntuforums.org/showthread.php?t=967654&page=4)

---

### Post by giantsfan7791 on 2009-01-01
> **melojo said:**
> have you looked here?
[http://ubuntuforums.org/showthread.php?t=967654&page=4](http://ubuntuforums.org/showthread.php?t=967654&page=4)
Not that specific page, but I tried that method already from another guide and it hasn't worked. I think it makes it worse actually, since when I right-click on the network icon, it doesn't show the "Enable wireless" checkbox that was there before.

EDIT: I forgot to add that my Wifi button on the laptop is always red, it won't turn off nor does it ever turn blue.

---

### Post by melojo on 2009-01-01
double post

---

### Post by melojo on 2009-01-01
you might keep an eye on this page and see if the gentleman that is helping that person get his working.

[http://ubuntuforums.org/showthread.php?t=1024009&page=2](http://ubuntuforums.org/showthread.php?t=1024009&page=2)

---

### Post by giantsfan7791 on 2009-01-04
So I tried a few more things from what I read but nothing worked. I installed Ubuntu 8.04 and still couldn't get it to work there, so I went back to 8.10. Can't anyone help? I really need to enable wireless on this, and I think i've installed Ubuntu about 30 times already.

Now when I left-click on the network icon, I see "Wireless Networks" in gray but there are no networks visible under it. Under "Wired Networks" I see "Auto eth0." I see an option to connect to a hidden wireless network, but when I enter my network's details, it doesn't connect.

---

