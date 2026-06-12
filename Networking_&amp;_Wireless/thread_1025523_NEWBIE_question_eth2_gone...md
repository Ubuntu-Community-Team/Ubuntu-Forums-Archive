---
title: "NEWBIE question: eth2 gone..?"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by skier66 on 2008-12-30
Hello,

i'm pretty new to ubuntu as to linux.
I have ubuntu installed on my dell d610 latitude.

Everything worked fine, i even have the wireless card working.

But i don't know what went wrong, but i have update my system (8.10) and since then my wired network card isn't reconized anymore.

I might have done other things wrong before i rebooted and noticed this problem.

Is there a way too let ubuntu scan the hardware again soo he can install the right drivers again? (it worked in the initial install).

Hope somebody have a solution or a pointer too a link where i can find the info. I have searched for it myself but haven't found it.

Thanks in advanced!!

Kees.

---

### Post by swamytk on 2008-12-30
can u post the following diagnosis results?

$ lspci

$ sudo ifconfig -a

---

### Post by skier66 on 2008-12-30
Thenx for your quick responce..
hope this helps:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4304 (4.3 KB)  TX bytes:4304 (4.3 KB)

pan0      Link encap:Ethernet  HWaddr 86:fc:7a:9f:5a:a0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:87:2a:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:dfcfe000-dfd00000

---

### Post by swamytk on 2008-12-30
Your Ethernet controller is "Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express" as per lspci output.

The MTU (Max.Transmission Unit) of your controller should be limited to 1500 to solve the problem.

Please follow the links below for the solution (command by command):
[https://bugs.launchpad.net/ubuntu/+bug/298896](https://bugs.launchpad.net/ubuntu/+bug/298896)
[http://ubuntuforums.org/showthread.php?t=984675](http://ubuntuforums.org/showthread.php?t=984675)

Cheers!

---

