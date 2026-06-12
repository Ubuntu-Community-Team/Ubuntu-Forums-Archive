---
title: "Wired Ethernet in Jaunty Jackalope"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by Sollus on 2009-04-25
I've only done this on Ibex/Jaunty Ubuntu howver I'm assuming it is probably applicable elsewhere. Upon upgrading, my wired connection would not work (specifically for my nVidia MCP55 (rev a2) ). I remembered a fix I had found from Ibex for the same issue, and trying it, it works. 

```
user@user:~$ lspci | grep Ethernet
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
user@user:~$ modprobe -l | grep forcedeth
kernel/drivers/net/forcedeth.ko
user@user:~$ dmesg | grep forcedeth
[   11.820109] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   11.820446] forcedeth 0000:00:11.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[   11.820450] forcedeth 0000:00:11.0: setting latency timer to 64
[   12.340563] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 19, 00:00:00:00:00:00
[   12.340566] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim desc-v3
[   12.340855] forcedeth 0000:00:12.0: PCI INT A -> Link[AMC1] -> GSI 21 (level, low) -> IRQ 21
[   12.340858] forcedeth 0000:00:12.0: setting latency timer to 64
[   12.860567] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 19, addr 00:00:00:00:00
[   12.860570] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim desc-v3
[   21.906979] Modules linked in: ck804xrom(+) mtd x_tables soundcore chipreg usbhid(+) usblp snd_page_alloc map_funcs i2c_nforce2 nvidia(P) psmouse serio_raw pcspkr ohci1394 forcedeth ieee1394 floppy vesafb fbcon tileblit font bitblit softcursor
```This is what I did to fix it: 

Add the following to: */etc/modprobe.d/options*

 ```
options forcedeth msi=0 msix=0
``` Then [POTENTIALLY DANGEROUS COMMAND, BE CAREFUL]:
```
sudo update-initramfs -u
``` REBOOT
 

However, I have three questions about it. 

--What exactly do the commands above do?
--Where does this line actually belong? Jaunty is reporting that the lines should be in a conf file because the options file will be ignored in the future.
--Is there a better way to do this?

Thanks.

---

### Post by Sollus on 2009-04-25
One more thing, the network interface does seem a little sluggish when loading web pages and such, that's why I'm not sure this is the best solution albeit functioning.

---

### Post by Sollus on 2009-04-27
Anyone?

---

