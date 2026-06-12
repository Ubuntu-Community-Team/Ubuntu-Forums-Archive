---
title: "No wireless access with 9.10"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by dax029 on 2009-11-06
Hi
I just upgraded to 9.10 and now can't get my wireless connection to work.  It's showing no network connection. I have re input all the settings but still no luck.

My other PC's on the network are working ok, just my Ubuntu one isn't.

Any suggestions would be appreciated

Cheers

Dax

---

### Post by pastalavista on 2009-11-06
Check in System-> Administration-> Hardware Drivers. To activate any proprietary driver it finds, you may need to connect directly via ethernet cable to download them.

---

### Post by dax029 on 2009-11-06
Hi
Thanks for the quick feedback. I connected using an ethernet cable that doesn't let me connect either?

Cheers
Dax

---

### Post by dax029 on 2009-11-06
Hi
I did the check and it shows I have a Broadcom STA wirless driver, activated and in use.
Chers
Dax

---

### Post by pastalavista on 2009-11-06
What is the output of ```
lshw -C network && lspci
```

also check ```
ifconfig
```

these are commands to enter in terminal (Applications-> Accessories-> Terminal)

---

### Post by dax029 on 2009-11-06
Result for lshw -C network && lspci is

dax@dax-laptop:~$ lshw -C network && lspci 
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED      
       description: Network controller 
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
       resources: memory:f6cfc000-f6cfffff 
  *-network 
       description: Ethernet interface 
       product: NetLink BCM5784M Gigabit Ethernet PCIe 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 10 
       serial: 00:21:70:84:43:0a 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 multicast=yes 
       resources: irq:217 memory:f69f0000-f69fffff 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04) 
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04) 
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04) 
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series 
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] 
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12) 
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) 
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10) 
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01) 
0d:00.0 Multimedia controller: Philips Semiconductors Device 7160 (rev 03) 
dax@dax-laptop:~$  
 


and the result for the ifconfig is:

dax@dax-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:21:70:84:43:0a   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:678 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:678 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:39820 (39.8 KB)  TX bytes:39820 (39.8 KB) 
 
dax@dax-laptop:~$ ^C 
dax@dax-laptop:~$  
 
Cheers

Dax

---

### Post by pastalavista on 2009-11-06
Your problem may be with ipv6 which isn't entirely operatioal yet.

I have done this and it made my connection better.
```
gksu gedit /etc/sysctl.conf
```
Add this line to the bottom:```
net.ipv6.conf.all.disable_ipv6=1
```

...all I can think of now. It says your wireless is "Unclaimed" and besides ipv6 being enabled, I don't know why it won't connect.. sorry

---

### Post by dax029 on 2009-11-07
Hi pastalavista

Thanks for all your help, will give this a try later tonight

Thanks again

Cheers

Dax

---

### Post by amitkenny on 2009-11-07
I have the same problem. Wireless networks are detected, but connection always failing. Although other computer with ubuntu 9.10 at home with exactly the same setting (but different hardware is successfully connected.
I tried the change in the script of the ipv6  and it made no difference.

---

### Post by pastalavista on 2009-11-07
I just stumbled across [this solution]("http://ubuntuforums.org/showthread.php?t=1288865").

hope it helps :)

---

### Post by amitkenny on 2009-11-07
Guess what, I found it, tried it and it does not work yet.

---

### Post by nhanquy on 2009-11-07
For broadcom 43xx  (4306 for example) try to install **b43-fwcutter**

---

