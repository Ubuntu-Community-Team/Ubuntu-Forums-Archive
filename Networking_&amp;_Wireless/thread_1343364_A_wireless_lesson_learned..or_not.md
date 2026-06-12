---
title: "A wireless lesson learned..or not"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by vwbusnut65 on 2009-12-01
I have been messing with various Ubuntu distros since Hoary 5.04. I have been tied up with work and have not had time for about a year to really mess with Ubuntu. I decided to resurrect a 3 year old laptop and Install 9.10 on it. I had nothing but problems trying to get the wireless to work. In fact I never did get it to even connect to my Linksys wireless WRT310N router. I decided to install 8.10, since I had backtrack 4 beta working on the same laptop and it is based on 8.10. I was able to get a wireless connection but not reliably, trying to get the wireless to work on a Toshiba A105 S4004. It runs the INTEL 3945abg wireless chipset. I tried searching the forums and following advice on several threads and help topics including the threads at the bottom of this post. I tried all sorts of things to make my connection work reliably to no avail until today. I think it is some sort of conflict with my other laptop running windows 7 with the Intel wireless 4965agn chipset. I noticed everytime I turn off the wireless to the windows 7 (4965) I all of a sudden have a good connection and can load webpages. My Ubuntu laptop with the 3945 chipset always sees my router, but does not reliably load pages unless I have my windows 7 laptop's wireless disabled. I checked my router to make sure everything seemed right. I am running WEP, and implementing mac address filtering for the time being. My router always assigns my Ubuntu laptop an IP address but I can not connect to the web unless my other windows 7 laptop wireless is disabled. The two laptops are next to each other. I am beginning to think it is a matter of actual RF interference and the wireless stream somehow not being fully decoded, or a problem with the different protocols (802.11G/N) and my router not being able to broadcast both reliably at the same time. I am hoping someone has an idea as to why I can not use both laptops at the same time. Thanks for taking the time to read this. The following is my system info as it runs right now:

[HTML]dennis@Computer:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:3d:8b:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.105 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:3c:8c:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ce:f8:3a:d3:16:e7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
dennis@Computer:~$ [/HTML]

[HTML]dennis@Computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"mylan65"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:7E:F3:AE:79   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=87/100  Signal level:-46 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missehttp://ubuntuforums.org/newthread.php?do=newthread&f=336d beacon:0

pan0      no wireless extensions.[/HTML]

[HTML]dennis@Computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:3c:8c:c5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:3d:8b:33  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16341616 (16.3 MB)  TX bytes:2520401 (2.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-3D-8B-33-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/HTML]









[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

[http://ubuntuforums.org/showthread.php?t=1150544](http://ubuntuforums.org/showthread.php?t=1150544)

[http://ubuntuforums.org/showthread.php?t=1326317&highlight=intel+3945+wireless+but+no+internet](http://ubuntuforums.org/showthread.php?t=1326317&highlight=intel+3945+wireless+but+no+internet)

[http://ubuntuforums.org/showthread.php?t=1261288&highlight=intel+3945+wireless+but+no+internet](http://ubuntuforums.org/showthread.php?t=1261288&highlight=intel+3945+wireless+but+no+internet)

---

