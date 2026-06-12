---
title: "Toshiba Satellite A215 not seeing wifi networks"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by tristan8276 on 2010-05-03
Hello,

I'm using Ubuntu 10.04 - 64bit install with an A215.  The wifi was working fine until today.  Ubuntu seems to detect the hardware, and it shows the interface as being 'up', however no networks show up in either the network manager or 'sudo iwlist scan'.  I'm not sure if it's a driver issue, or if the hardware itself died.

Here is the output of lspci:

ubuntu@ubuntu:~$ lspci

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

And ifconfig:
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:13:24:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3072 (3.0 KB)  TX bytes:3072 (3.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:25:d2:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig:

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off

---

### Post by tristan8276 on 2010-05-04
Okay, somehow this problem has resolved itself.  :confused:

---

### Post by ajd79 on 2010-05-04
I am seeing the same out put that you were.  I have tried surfing the threads to see if there is a solution but to no avail, unlike yours though, mine is not fixing. I am using p205d-s7802. Any ideas?

---

### Post by tristan8276 on 2010-05-04
What I did today was I disconnected every other computer from my router and reconnected them.  After that, my Satellite A215 was able to connect to the router.  I couldn't tell you why that worked for me though... Hopefully it works for you.

---

### Post by tristan8276 on 2010-05-05
Ok, in the middle of browsing online today, the problem resurfaced.  The fix of disconnecting everything and reconnecting did not help.  I'm fairly certain this is a native driver issue, but I'm no expert.  Does anyone have any ideas on this issue?  I could install the windows driver with ndiswrapper, but then would I need to blacklist/disable the native driver?

---

### Post by tristan8276 on 2010-05-05
Sorry for all the posts, but the problem seem intermittent now.

---

### Post by darthmowzy on 2010-09-03
I have the same problem on my toshiba a215-s5822. My interface is up but "sudo iwlist scan" shows no netwroks. Mine seems to be related to the cpu speed. 

If I set the cpu scaling to "On demand" with the "CPU Frequency Scaling Monitor" applet then run "sudo rmmod ath9k; sudo modprobe ath9k" then my networks show up under "iwlist scan"

---

