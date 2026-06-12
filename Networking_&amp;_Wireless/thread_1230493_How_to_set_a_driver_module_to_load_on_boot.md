---
title: "How to set a driver module to load on boot"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by rogerdean on 2009-08-03
Hello all - need a little help please...

I'm trying to get wired networking up on my Acer Aspire Revo, but the Nvidia ethernet chipset is not yet supported in the kernel or Ubuntu. See here...

[http://manpages.ubuntu.com/manpages/jaunty/man4/nfe.4freebsd.html](http://manpages.ubuntu.com/manpages/jaunty/man4/nfe.4freebsd.html)

So I've downloaded the driver module (nfe.4freebsd.gz) available from that page, and now need to make it run at boot time. How do I do this? Should I unzip the file first? Where should I put it and does it need to be referenced in any files?

Any advice appreciated! Many thanks
Roger

---

### Post by chili555 on 2009-08-03
I have a suspicion that the driver is already included. The link you gave us appears to be for FreeBSD, although why it would be listed on an Ubuntu page is mystifying. Please open a terminal and type:```
lspci | grep MCP
```Post the result here. We can then assist you further.

---

### Post by rogerdean on 2009-08-04
Thanks for helping out on this - brilliant! Output is

```
valery@valery-desktop:~$ lspci | grep MCP
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
valery@valery-desktop:~$ 

```

---

### Post by chili555 on 2009-08-04
The MCP79 chipset is supposed to be supported by the module *forcedeth*. I don't believe nVidia releases chipset details, considering them trade secrets. So, some brave souls reverse-engineered a driver. Some report it works well, some not so much. Please do:```
sudo modprobe forcedeth
ifconfig
```Do you now have an ethernet interface, *eth0*? If not, please run:```
sudo cat /var/log/messages | grep eth
```In this way, we will get kernel message for both *forcedeth* and *eth0*.

I have my hopes high.

---

### Post by rogerdean on 2009-08-05
Yes! I have ethernet following your first bit of code above. Can't claim I understand what we did, but Chili thank you so very much for the help, research work etc. Much appreciated

Very best
Roger

---

