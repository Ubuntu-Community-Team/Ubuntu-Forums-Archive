---
title: "no Wifi"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by reacol on 2009-03-26
Dear All,

What am I doing wrong? here is some information  that I hope will help resolve the issue.  Thank you all in advance!

mattia@mattia-desktop:~$ lsusb 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 006: ID 0864:4102 NetGear, Inc. MA101 802.11b Adapter 
Bus 001 Device 004: ID 047d:1032 Kensington 
Bus 001 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 


mattia@mattia-desktop:~$ lspci 
00:00.0 Host bridge: nVidia Corporation Device 0071 (rev a3) 
00:00.1 RAM memory: nVidia Corporation Device 007f (rev a1) 
00:00.2 RAM memory: nVidia Corporation Device 0075 (rev a1) 
00:00.3 RAM memory: nVidia Corporation Device 006f (rev a1) 
00:00.4 RAM memory: nVidia Corporation Device 00b4 (rev a1) 
00:01.0 RAM memory: nVidia Corporation Device 0076 (rev a1) 
00:01.1 RAM memory: nVidia Corporation Device 0078 (rev a1) 
00:01.2 RAM memory: nVidia Corporation Device 0079 (rev a1) 
00:01.3 RAM memory: nVidia Corporation Device 007a (rev a1) 
00:01.4 RAM memory: nVidia Corporation Device 007b (rev a1) 
00:01.5 RAM memory: nVidia Corporation Device 007c (rev a1) 
00:01.6 RAM memory: nVidia Corporation Device 007d (rev a1) 
00:02.0 PCI bridge: nVidia Corporation Device 007e (rev a2) 
00:04.0 PCI bridge: nVidia Corporation Device 007e (rev a2) 
00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4) 
00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4) 
00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2) 
00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) 
00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4) 
00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2) 
00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3) 
00:10.0 RAID bus controller: nVidia Corporation CK804 Serial ATA Controller (rev f3) 
00:11.0 RAID bus controller: nVidia Corporation CK804 Serial ATA Controller (rev f4) 
00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) 
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3) 
00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) 
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1) 
03:03.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04) 
03:03.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04) 
03:03.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) 
03:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) 


mattia@mattia-desktop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0             
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:09:5b:46:b4:e1 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=1.101.2-84 ip=192.168.2.5 wireless=IEEE 802.11b 
  *-network:1 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: ae:a1:33:64:26:4e 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 


mattia@mattia-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:14:22:34:ca:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:265000 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:265000 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:12385728 (12.3 MB)  TX bytes:12385728 (12.3 MB) 

pan0      Link encap:Ethernet  HWaddr ae:a1:33:64:26:4e  
          inet6 addr: fe80::aca1:33ff:fe64:264e/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:936 (936.0 B) 

wlan0     Link encap:Ethernet  HWaddr 00:09:5b:46:b4:e1  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::209:5bff:fe46:b4e1/64 Scope:Link 
          UP BROADCAST  MTU:1500  Metric:1 
          RX packets:8732 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:5689 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1698419 (1.6 MB)  TX bytes:40998 (40.9 KB) 

mattia@mattia-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11b  ESSID:"belkin54g"  Nickname:"" 
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:59:D9:FE   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off 
          Link Quality=63/100  Signal level=66/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions.

---

### Post by damis648 on 2009-03-26
From what you posted, it seems that WiFi should be working fine. You're sure nothing comes up when you click the network manager applet in the upper right hand corner of your panel?

---

### Post by reacol on 2009-03-26
> **damis648 said:**
> From what you posted, it seems that WiFi should be working fine. You're sure nothing comes up when you click the network manager applet in the upper right hand corner of your panel?

Actually I see the network just fine when I click on the NM applet, reception is good signal strength 50-70%. the problem is when I try (with NM) to ping anything but the 192.168.2.5 which is the ubuntu box but when I try to ping the 192.168.2.1 which is the router I get all packets sent but none received and when I ping 74.125.91.147 ([www.google.com](www.google.com)) I get 0 packs transmitted. 

I must be doing something horribly wrong but not sure what....

thanks for the help you can offer.

---

### Post by sgosnell on 2009-03-26
Can you reach any internet sites?  If not, are you sure the modem is working properly?  Can you reach sites with other computers?

---

### Post by reacol on 2009-03-26
Yes, as I am writing this, I can connect WiFi and reach other sites with three other boxes, a Wii, a win XP (from where I writing this) and a PS3. They are on  DHCP while the ubuntu box is on static IP as I could not get it connected with DHCP no matter what.

???


> **sgosnell said:**
> Can you reach any internet sites?  If not, are you sure the modem is working properly?  Can you reach sites with other computers?

---

### Post by sgosnell on 2009-03-26
What issues were you having with DHCP?  Are you using MAC filtering?

---

### Post by reacol on 2009-03-26
Yes I use MAC filtering as well as WEP-128. I disabled both to no avail. 

> **sgosnell said:**
> What issues were you having with DHCP?  Are you using MAC filtering?

---

### Post by sgosnell on 2009-03-26
Well, your posts show your wireless to be working.  I'm out of ideas for now, and would suggest looking at the router settings, since they're different for your Ubuntu machine.

---

### Post by reacol on 2009-03-31
thank you for the help, I am going to try again with a new wireless card. I will post my results, and any further assistance would be appreciated :o

---

