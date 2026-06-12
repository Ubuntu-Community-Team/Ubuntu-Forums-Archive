---
title: "Solving Network interface id and mac address change on every boot"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by jwvdleest on 2009-12-15
Dear users,

An addition to Rosell's findings to stop ubuntu with automatic generation of interface ID and MAC address. I made these changes on Ubuntu 9.10.
This is in my case happening on a HP Pavilion DV9645ED with NVidia chipset.
The trick:
as root, go to /lib/udev/rules.d
make safecopy of 75-persistent-net-generator.rules
edit the file 75-persistent-net-generator.rules:
add the line:
GOTO=&quot;persistent_net_generator_end&quot; 
right after the SUBSYSTEM line, with this action the script is no longer doing anything.
Save the file.
go to /etc/udev/rules.d
make safecopy of the file 70-persistent-net.rules
edit the file 70-persistent-net.rules
remove all the unwanted eth devices. If you also have a wlan card, the last lines must be:

# PCI device 0x10de:0x0450 (forcedeth)
SUBSYSTEM==&quot;net&quot;, DRIVERS==&quot;?*&quot;, ATTR{address}==&quot;00:00:yo:ur:mac:addr&quot;, NAME=&quot;eth0&quot;

# PCI device 0x14e4:0x4312 (wl)
SUBSYSTEM==&quot;net&quot;, DRIVERS==&quot;?*&quot;, ATTR{address}==&quot;00:1a:73:your:mac:addr&quot;, NAME=&quot;wlan0

If you want to know the proper PCI device number, it is already written behind the #
This should do the trick.

If not: you could edit /etc/network/interfaces:
 the last part could look like:

auto eth0
iface eth0 inet dhcp
    hwaddress ether 00:00:6c:your:mac:addr

auto wlan0
iface wlan0 inet dhcp
    hwaddress ether 00:1a:73:your:mac:addr

Don't you know the MAC addresses? Boot with Windows. These drivers seem to fetch the MAC address from the BIOS EEPROM properly. (Why has there been no proper fix in ubuntu 9.10? I have this problem since version 8.04 when I bought the laptop)

Reboot you computer.

Of course there will be a better solution coming soon, but this is not known to me yet.
Good luck.

---

