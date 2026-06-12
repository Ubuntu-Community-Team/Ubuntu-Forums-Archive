---
title: "Wireless was detected, now its not"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by thenowherekid on 2006-06-26
yeah like it says on the title, my wireless was workin fine after i installed kubuntu. after a few goes at it,ons and offs, probably a days worth, the laptop cannot find the device. i can tell you that it is a intel pro/wireless 3945 and thats bout it. ive never messed withh kubuntu before, ive always used slackware, but i heard this was good for laptops so im giving it a go. thanks for any help you guys can give me.

---

### Post by thenowherekid on 2006-06-27
My laptop sees that it is there.

> lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0298 (rev a1)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0000:09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
**0000:0c:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)**


>  dmesg | grep ipw3945
[17179583.940000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.3m
[17179583.940000]** ipw3945: Copyright(c) 2003-2006 Intel Corporation**
[17179583.940000] **ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection**


and it doesnt make any since why i can use it. there is nothing under network setting bout wireless. ifconfig or iwconfig doesnt see it, and niegther does the wireless assissant.

>  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:F9:85:01
          inet addr:192.168.xx.xx  Bcast:192.168.xx.xx  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fef9:8501/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1034798 (1010.5 KiB)  TX bytes:136667 (133.4 KiB)
          Interrupt:185

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)


> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


I just dont know what the problem is. Seriously any advice would help. Thanks in advance.

---

### Post by stupidkid on 2006-06-27
O wow, unknown device? My best guess would be to try ndiswrapper and see if you can load your windows drivers.

---

### Post by thenowherekid on 2006-06-28
I did try ndiswrapper. it said hardware and driver present. i did the modprobe ndiswrapper deal. and it didn't show up on iwconfig or ifconfig. But i did find a solution. Re-installation. I did that and im running kubuntu for the first time and the wireless is working. its only a matter of time im sure that it will quit. oh and the wireless worked on the live cd when i booted it up to that which still is makin me wonder. Otherwise the only other solution i would know is stick to ethernet. always seems to be workin for me.

---

### Post by barna on 2006-06-28
I am having the same problem, and I am already several days after a re-installation (my last trial to solve this shit wireless problem). And the symptom is reproducible: for a few days I had wireless again, and now there is none, exactly with the same error messages, as in your case. 

I have a Toshiba Satellite SA60-185. The problem is surely a software issue, and not du to an unrecognized hardware, since the wireless worked with the LiveCD, even during the installation, and also for a few days after the installation.

---

### Post by barna on 2006-06-28
Hi,
I found something strange. According to a web search, my Atheros wlan card should be handled by the madwifi modules. 

Due to my very bad experience with any linux distro, I have two identical setups (Dapper) on two partitions (in case one of them breaks down, I can temporarily use the other). 

In the currently used setup (where my wireless card is NOT recognized), I have 
/lib/modules/2.6.15-23-386/madwifi, but NO /lib/modules/2.6.15-25-386/madwifi. That is, for the more recent kernel, these modules are missing. I checked the installed files in the package management system (with synaptic). madwifi is in the linux-restricted-modules-2.6.15 package, and this lists only /lib/modules/2.6.15-23-386/madwifi, but not /lib/modules/2.6.15-25-386/madwifi. 

If I boot up the other setup, there both /lib/modules/2.6.15-23-386/madwifi and /lib/modules/2.6.15-25-386/madwifi exist, and also, my wlan card is recognized, and works nicely. (Interestingly enough, the package management system in this setup also only lists /lib/modules/2.6.15-23-386/madwifi as an installed file, and not the other one, but it is still there)

So I think there is some problem with this package, or something similar. Instead of crying on each-other's shoulders about this problem, is it possible to complain at the developers? Or do they check these forums?

---

