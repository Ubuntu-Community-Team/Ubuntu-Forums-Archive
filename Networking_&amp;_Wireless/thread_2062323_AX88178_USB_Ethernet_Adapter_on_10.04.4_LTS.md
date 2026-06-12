---
title: "AX88178 USB Ethernet Adapter on 10.04.4 LTS"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by bigd0g on 2012-09-24
Hi,

I'm trying to use a Trendnet TU2-ETG USB Ethernet Adapter to share my laptop's wired Internet connection.  The device uses the Asix AX88178 chipset and is correctly identified via 'lsusb' when connected.  The device properly registers a new Ethernet adapter, eth2, which I can modify using the Network Manager.  I have configured it in the following manner...

auto eth2
iface eth2 inet static
    address 192.168.1.1
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255

I can't, however, get any packets to travel over the device.  When doing an 'ifconfig', all packets (both RX and TX) show 0, despite attempts to ping another machine with a similar configuration (address of 192.168.1.2).  Pings are saying the destination is unreachable.

I have dropped all config of 'iptables' on both machines to make sure it's not a firewall issue.

I have made sure the machine doing the pinging is pingable from other resources (connected to its other wired Ethernet adapter).

Lots of searching on the web pointed me to trying to update the kernel module manually.  Upgrading to v4.4.0 of the AX8772B_772A_760_772_178_LINUX_Driver fails to even recognize the eth2 adapter in 'ifconfig'.  It is still shown with 'lsusb', though.

I followed the directions shown here: [http://plugable.com/2010/10/18/howto-asix-88178-usb-ethernet-adapter-on-ubuntu-10-10-linux/](http://plugable.com/2010/10/18/howto-asix-88178-usb-ethernet-adapter-on-ubuntu-10-10-linux/)

I'm running the latest kernel: 2.6.32-43-generic #97-Ubuntu SMP x86_64 GNU/Linux

I have reverted back to the stock 10.04.4 LTS drivers for Axis.

I'm at my wit's end.  Anyone have ideas as to what's wrong?

---

### Post by allanchou on 2012-10-03
> **bigd0g said:**
> Hi,
 
I'm trying to use a Trendnet TU2-ETG USB Ethernet Adapter to share my laptop's wired Internet connection. The device uses the Asix AX88178 chipset and is correctly identified via 'lsusb' when connected. The device properly registers a new Ethernet adapter, eth2, which I can modify using the Network Manager. I have configured it in the following manner...
 
auto eth2
iface eth2 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
 
I can't, however, get any packets to travel over the device. When doing an 'ifconfig', all packets (both RX and TX) show 0, despite attempts to ping another machine with a similar configuration (address of 192.168.1.2). Pings are saying the destination is unreachable.
 
I have dropped all config of 'iptables' on both machines to make sure it's not a firewall issue.
 
I have made sure the machine doing the pinging is pingable from other resources (connected to its other wired Ethernet adapter).
 
Lots of searching on the web pointed me to trying to update the kernel module manually. Upgrading to v4.4.0 of the AX8772B_772A_760_772_178_LINUX_Driver fails to even recognize the eth2 adapter in 'ifconfig'. It is still shown with 'lsusb', though.
 
I followed the directions shown here: [http://plugable.com/2010/10/18/howto-asix-88178-usb-ethernet-adapter-on-ubuntu-10-10-linux/](http://plugable.com/2010/10/18/howto-asix-88178-usb-ethernet-adapter-on-ubuntu-10-10-linux/)
 
I'm running the latest kernel: 2.6.32-43-generic #97-Ubuntu SMP x86_64 GNU/Linux
 
I have reverted back to the stock 10.04.4 LTS drivers for Axis.
 
I'm at my wit's end. Anyone have ideas as to what's wrong?
 
You might need to check if your AX88178 dongle can work fine with ASIX's standard AX88178 Windows drivers ([http://www.asix.com.tw/download.php?sub=driverdetail&PItemID=84](http://www.asix.com.tw/download.php?sub=driverdetail&PItemID=84)) to isolate if your AX88178 dongle is good one or not first? If no, you should contact the manufacturer's support guys for further support; if yes, you can try to set a static IP address for AX88178 dongle on your Linux system and verify the network functionality again to narrow down the root cause of your issue.

---

