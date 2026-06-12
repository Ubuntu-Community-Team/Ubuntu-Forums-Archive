---
title: "Intel iw2200 on Hardy 8.04.2 - Compaq 6120 wifi issues"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by fatalbert on 2009-01-26
Hi,

I was hoping someone could help me get on line using wifi. I have attached the following info. I've checed the BIOS setting and the only option is to have the card enabled or disabled. I've also tried some thing on the boards here, but nothing seems to work. 

Thanks a bunch!

I think the "Detected Intel PRO/Wireless 2200BG Network Connection
[   28.348605] ipw2200: Radio Frequency Kill Switch is On:" messages is not allowing me to move forward.

Machine Brand and Mode - Compaq nc6120

piglet@piglet-laptop:/etc$ lspci | grep Network
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

root@piglet-laptop:/etc# ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:16:6f:65:ec:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Memory:d0000000-d0000fff 

root@piglet-laptop:/etc# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"66string"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


root@piglet-laptop:/etc# lshw -C network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:65:ec:f3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

root@piglet-laptop:/etc# uname -mr
2.6.24-23-386 i686

---

### Post by fatalbert on 2009-01-28
To give a quick update: I was never able to get a light to go on the wireless card and since this was a new install, I decided to punt and install Windows Vista and sure enough the light did not work either, so I need to have laptop looked at.


Do I marked this as Solved?

---

