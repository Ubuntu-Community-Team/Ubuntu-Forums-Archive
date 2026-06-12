---
title: "Network Adapter not working after HW upgrade"
date: 2013-04-08
forum: Networking &amp; Wireless
---

### Post by VingInMedina on 2013-04-08
[COLOR=#333333][FONT=Ubuntu]I am running Ubuntu 12.04 LTS. I upgraded the hardware of my machine (i.e. I took the hard drives out of my old machine, which no longer works and put them into a new machine). I am having a problem getting the Network Adapter to function.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I have a Gigabyte 990FXA-UD3 motherboard and I have read that Ubuntu has a problen with the Realtek chip on board. I downloaded the r8186-8.035.00 driver from the Realtek website and installed it into the kernel. I can see that the module is loaded and the system now sees the network adapter.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I edited the /etc/udev/rules.d/70-persistent-net.rules file and removed the eth0 line (from the old hardware) and renamed the eth1 entry to eth0.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Here is my /etc/network/interfaces file:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]```
auto lo
iface lo inet loopback[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]auto eth0
iface eth0 inet static
 address 192.168.1.2
 netmask 255.255.255.0
 gateway 192.168.1.1
```[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I have my DNS servers set up in the /etc/resolvconf/resolv.conf.d/base file:
```
nameserver 24.154.1.6
nameserver 24.154.1.7
```
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]after rebooting here is the output of ifconfig -a[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Ubuntu]eth0 Link encap:Ethernet HWaddr 94:de:80:0b:93:2a
          inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
          inet6 addr: fe80::96de:80ff:fe0b:932a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1006 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1929 (1.9 KB) TX bytes:0 (0.0 B)
          Interrupt:75 Base address:0xa000
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]lo Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:63975 (63.9 KB) TX bytes:63975 (63.9 KB)[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Ubuntu]Here is the output from lshw, lsb_release and uname -a:[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Ubuntu]matrix# lshw -C network; lsb_release -a; uname -a
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: 94:de:80:0b:93:2a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.035.00-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:75 ioport:b000(size=256) memory:dc104000-dc104fff memory:dc100000-dc103fff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
Linux matrix 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Ubuntu]When I unplug the ethernet cable, I get the message (from dmesg):[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Ubuntu][ 3240.514246] r8168: eth0: link down
[ 3241.120081] r8168: eth0: link down[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Ubuntu]Then after I plug the cable back in:[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Ubuntu][ 3244.385740] r8168: eth0: link up
[ 3245.121022] r8168: eth0: link up[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Ubuntu]So, It would appear that the driver (r8168) in the kernel is able to see the hardware and is able to detect the link level.[/FONT][/COLOR]
[FONT=Ubuntu][COLOR=#333333]But, I can't ping anything outside of the machine. I can ping the loopback and the ipaddress of the machine itself, but any other address (e.g. the router at 192.168.1.1) just gives me [/COLOR][/FONT][COLOR=#333333][FONT=Ubuntu]Destination Host Unreachable when I try.[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]Thinking that perhaps the Realtek chip on the motherboard might be the problem, I put in a seperate PCI 10/100 Enternet card. It's a Hynix Semiconductor NC100 Network Everywhere Fast Enternet (Linksys) card using the tulip driver.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]The system recognized it as eth1 and I modified the /etc/network/interfaces and changed my entry for eth0 to eth1 and rebooted.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]The same thing is happening with this new interface as the one on the motherboard. The link level is up, but nothing more.[/FONT][/COLOR]
[FONT=Ubuntu][COLOR=#333333]I even tried booting off a 12.10 live CD and the eth1 interface was not able to set up using DCHP.[/COLOR][/FONT]

[FONT=Ubuntu][COLOR=#333333]I have also removed the r8168 driver and put back the r8169 and tried everything again.[/COLOR][/FONT]

[FONT=Ubuntu][COLOR=#333333]Any suggestions?

Thanks in advanced for any and all help.[/COLOR][/FONT]

---

### Post by praseodym on 2013-04-08
Change "false" to "true" in the /etc/NetworkManager/NetworkManager.conf and reboot. Otherwise the network-manager can not handle the manual config.

---

### Post by VingInMedina on 2013-04-08
I updated the /etc/NetworkManager/NetworkManager.conf file and it now looks like this;

```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=94:DE:80:0B:93:2A,

[ifupdown]
managed=true
```

And rebooted, but I still get the "Destination Host Unreachable" error when I try to ping my router at 192.168.1.1.

---

### Post by praseodym on 2013-04-08
Try to shutdown any component for 10 minutes, completely currentless. Then try it again

---

### Post by VingInMedina on 2013-04-08
I shut down the machine and completely disconnected it from power and removed the ethernet cable. I waited for over 10 minutes before starting it back up. There was no change after bringing the machine back up. Still not able to ping.

---

### Post by VingInMedina on 2013-04-10
[COLOR=#333333][FONT=Ubuntu]Well, it would appear that the problem was hardware.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I went into the BIOS as disabled the onboard ethernet adapter. I was then able to boot up with the separate PCI card in the machine and after updating the /etc/udev/rules.d/70-persistent-net.rules file the network came up and worked fine. If I enabled the onboard ethernet again, I could not get the network to come up.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I took the motherboard back to Microcenter (they are really good about exchanging things) and got another one. The onboard ethernet adapter is working fine on this new one.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Thanks for helping me out.[/FONT][/COLOR]

---

