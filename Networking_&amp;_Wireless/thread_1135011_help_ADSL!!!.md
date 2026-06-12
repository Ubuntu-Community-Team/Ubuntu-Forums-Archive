---
title: "help ADSL!!!"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by drjackal on 2009-04-24
help needed to setup adsl connection. for some reason my computer is not accessing my adsl connection when i access it from ubuntu 8.10 for amd 64...what are the required settings?

---

### Post by inobe on 2009-04-24
for the record' what is the make and model dsl modem ?

also include if it's hooked to your computer with usb.

---

### Post by Redhishan on 2009-04-24
What type of modem you have...

---

### Post by drjackal on 2009-05-21
its huawei wa1003a cpable of both wireless and wired...i have to rely on wired because wireless firmware isnt installed yet. 

my pci card is nVidia MCP51 Ethernet Controller

i am using ubuntu 9.10 cuz i got amdturion :P

---

### Post by drjackal on 2009-05-21
help please!!!!

---

### Post by superprash2003 on 2009-05-22
in your terminal type **ifconfig** and post output , you first need to get an ip from your router

---

### Post by drjackal on 2009-05-22
eth1     link encap:Ethernet HWaddr 00:1f:16:4f:b7:30
         UP BROADCAST MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
         Interrupt:17 Base address:0xe000

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  mask:255.0.0.0
         UP LOOPBACK RUNNING MTU:16436 Metric:1
         RX packets:18 errors:0 dropped:0 overruns:0 frame:0
         TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:1128 (1.1 KB) TX bytes:1128 (1.1 KB)

---

### Post by drjackal on 2009-05-22
sorry i am using another pc to log onto the internet now.. and so it takes time to type out the whole message...please bear with me :P

---

### Post by drjackal on 2009-05-22
bump!

---

### Post by drjackal on 2009-05-22
i took the liberty of reading through other similar sounding threads...so here are all the information u might ask for! 


lspci |grep Ethernet
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)


ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1f:16:4f:b7:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1128 (1.1 KB)  TX bytes:1128 (1.1 KB)



iwconfig
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by drjackal on 2009-05-22
bump!

---

### Post by drjackal on 2009-05-22
hey guys!! i found another problem!! i could not connect to my adsl modem because i am not able to set the options to connect through a modem on the network manager panel..

checking up on my user privileges i saw..i had none :P

so there..thanks anyways :)

---

### Post by superprash2003 on 2009-05-22
so your problem is solved?

---

### Post by drjackal on 2009-05-22
if i can sort out my user account issues i think the problem will be solved :P
by the way how do i lock up my user password file?

i can't seem to unlock my usser account . but it is set as administrator !!

---

