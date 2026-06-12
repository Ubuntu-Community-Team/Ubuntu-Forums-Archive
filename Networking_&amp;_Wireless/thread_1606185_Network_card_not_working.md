---
title: "Network card not working"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by abhimohpra on 2010-10-26
Hello all,
I have installed the network drivers as instructed in .txt file on Broadcom site. My WIFI network gets switched ON. It does not detect any networks. Initially i used to get it properly but when i tried to attach one more adapter card to usb everything changed.

I have Dell 3400 Laptop i3 processor.
1. My Brand and model of Wireless card is: 
12:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
2. Below command does not show any output to me:
[COLOR=DarkRed][FONT=Courier New]lspci -n | grep '14e4:43' [/FONT][/COLOR]
3. I am using Ubuntu 9.10 having kernel 2.6.31-22-generic i686
4. I am not using NdisWrapper 
5. Its also showing:
 *-network **UNCLAIMED **    
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbd00000-fbd03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 03
       serial: f0:4d:a2:82:96:e0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:34 ioport:d000(size=256) memory:d2c04000-d2c04fff(prefetchable) memory:d2c00000-d2c03fff(prefetchable) memory:fbc00000-fbc1ffff(prefetchable)
6. Ifconfig shows:
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:82:96:e0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f24d:a2ff:fe82:96e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:167688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:241846016 (241.8 MB)  TX bytes:11868871 (11.8 MB)
          Interrupt:34 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:499378 (499.3 KB)  TX bytes:499378 (499.3 KB)

6. Iwconfig shows:
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


7. 
Earlier i used to get errors as:
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
sudo insmod wl.ko
insmod: error inserting 'wl.ko': -1 File exists
but i can see my file into that folder

then i tried with,
I even copied drivers wl.ko in /lib/modules/2.6.31-22-generic/kernel/net/wireless
and tried modprobe lib80211 and insmode wl.ko 
and then modprobe wl which went without errors.

My blacklist.conf shows:
blacklist amd76x_edac
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

I tried to search for simmilar errors and applied several solution. But finally CLUELESS!
Any solution to activate my card properly and detect network??

- Prasad

---

### Post by abhimohpra on 2010-10-26
This thread solved my problem
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1480671&page=4](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1480671&page=4)
very well written.
Kudos to helpers.
- Prasad

---

