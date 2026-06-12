---
title: "how to see if my network interface/card is supported?"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by janewayne on 2012-07-10
i recently purchased a gateway dx4870-ub21p desktop ([http://us.gateway.com/gw/en/US/content/model/DT.GDDAA.004](http://us.gateway.com/gw/en/US/content/model/DT.GDDAA.004)). it has an onboard lan network card. i am installing ubuntu 10.04 server (64 bit) following the instructions at [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall). this is a sandbox that i will use to learn UEC. (note, there is a wireless card too, but i have removed it from the motherboard).

the installation complained about not finding a network interface, however, i proceeded anyways with the installation and it completed. now i am at the console and need to get my network card working. 

when i type in: dmesg | grep eth, i get nothing.

when i type in: ifconfig, i see the following.
lo Link encap:Lcal Loopback
   inet addr:127.0.0.1 Mask: 255.0.0.0
   .... (omitted)
virbr0 Link encap:Ethernet HWaddr 8e:72:38:a9:dd:ec
       inet addr:192.168.122.1 Bcast:192.168.122.255 Mask: 255.255.255.0
       ... (omitted)

when i type in: lspci | greph -eth, i see the following.
00:19.0 Ethernet controller: Intel Corporation Device 1503 (rev 04)

i decided to just modify /etc/network/interfaces by adding:
auto eth0
iface eth0 inet static
address 192.168.2.6
netmask 255.255.255.0

then i typed in: sudo /etc/init.d/networking restart, and see the following
* Reconfiguring network interfaces...
SOICSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0

i also typed: sudo lshw -c network, and see the following
*-network UNCLAIMED
description: Ethernet controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
version: 04
width: 32 bits
clock: 33Mhz
capabilities: pm msi bus_master cap_list
configuration: latency=0
resources: memory:f7c00000-f7c1ffff memory:f7c39000-f7c39fff ioport:f080(size=32)


any ideas on how to proceed to get the network card working is appreciated.

---

### Post by Kirk Schnable on 2012-07-11
I think I had a card like this for awhile too. You need to install the e1000e drivers.

[http://sourceforge.net/projects/e1000/](http://sourceforge.net/projects/e1000/)

See this thread:
[http://ubuntuforums.org/showthread.php?t=1711388](http://ubuntuforums.org/showthread.php?t=1711388)

There are several other people there discussing this issue, and they solved it.

I'd be happy to assist if you get stuck.

Kirk

---

### Post by Cheesehead on 2012-07-11
Try the command [FONT="Courier New"]lspci -v[/FONT] to see the hardware details of all your PCI devices, which typically includes NICs. It will tell you manufacturer, model, and current kernel module assigned (if any). This alone will tell you if the device is supported and recognized.

Try the command [FONT="Courier New"]dmesg[/FONT] to see how your kernel handles the NIC, what kernel module (if any) gets assigned, and what eth* interface it gets assigned to.

Try the command [FONT="Courier New"]ifconfig -a[/FONT] to see all available interfaces, even the ones that are down.


For example, on my system:
```
$ lspci -v

---edited---
05:00.0 Ethernet controller: **Atheros Communications AR8132** Fast Ethernet (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 0213
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f0200000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at a000 [size=128]
	Capabilities: <access denied>
**	Kernel driver in use: atl1c**
**	Kernel modules: atl1c**


$ cat /var/log/dmesg.0 | grep atl
[    1.475366] atl1c 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.475399] atl1c 0000:05:00.0: setting latency timer to 64
[    1.596765] atl1c 0000:05:00.0: version 1.0.1.0-NAPI
[   32.445431] atl1c 0000:05:00.0: irq 42 for MSI/MSI-X


$ ifconfig -a eth
eth0      Link encap:Ethernet  HWaddr 00:23:5a:94:49:c3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 

```
You can see that PCI device 5:00.0 is an ethernet port that is used by the atl1c kernal module (driver). In this case, it's assigned to eth0, but it has no IP address (because nothing is plugged into it).

---

