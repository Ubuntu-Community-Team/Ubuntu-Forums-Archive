---
title: "Wifi Ad Hoc network problem"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by betete on 2009-04-21
Hello guys, probably I'm not the first to write about this problem, but I have already read most of the posts and I haven't found the answer.

I have a desktop PC, running Ubuntu 8.04 connected to ADSL Ethernet Modem to access internet, which is working. The PC also has a Realtek 8185 wifi pci card. I loaded the Windows driver using ndiswraper and had no problem, the card is working.

I also have a laptop running Windows XP, with wifi access. It works perfectly well.

I tried to establish and Ad Hoc network in order to share the internet connection between the PC and the Laptop. I followed all the steps in:
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

I can see the network from my laptop, and I can even connect, but once it gets connected I cannot ping to the Ubuntu machine and of course I have no internet access.

The wired thing is that I've been trying for a couple of days and this morning I made it work. I connected both machines, the laptop could ping the desktop machine and the pc could ping the laptop, and I also had internet access on my laptop. I also try mounting some folders from my laptop and it worked.

The problem came when I restarted the desktop PC. Again, I went back to the beginning. I can see the network from my laptop and I can connect, but once it connects I try to ping from one to the other and nothing happens.

Here is the result of ifconfig 
eth0      Link encap:Ethernet  direcciónHW 00:13:d4:79:e0:64  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:20 

eth1      Link encap:Ethernet  direcciónHW 00:08:54:28:73:60  
          dirección inet6: fe80::208:54ff:fe28:7360/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:6871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7194 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:4578634 (4.3 MB)  TX bytes:986997 (963.8 KB)
          Interrupción:21 Dirección base: 0xd400 

eth0:avahi Link encap:Ethernet  direcciónHW 00:13:d4:79:e0:64  
          inet dirección:169.254.8.155  Difusión:169.254.255.255  Máscara:255.255.0.0
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Interrupción:20 

eth1:avahi Link encap:Ethernet  direcciónHW 00:08:54:28:73:60  
          inet dirección:169.254.4.213  Difusión:169.254.255.255  Máscara:255.255.0.0
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          Interrupción:21 Dirección base: 0xd400 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1725 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:85204 (83.2 KB)  TX bytes:85204 (83.2 KB)

ppp0      Link encap:Protocolo punto a punto  
          inet dirección:190.179.210.142  P-t-P:200.63.148.77  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1492  Métrica:1
          RX packets:4103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4150 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:3051487 (2.9 MB)  TX bytes:477529 (466.3 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:e0:4c:f1:4c:d4  
          inet dirección:192.168.0.1  Difusión:192.168.0.255  Máscara:255.255.255.0
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:168 (168.0 B)
          Interrupción:19 Memoria:efefb800-efefb825 

And here it is the result of iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"'Ubuntu'"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:E0:B3:16:32:00   
          Bit Rate=11 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.


Please, can you help me.

---

### Post by betete on 2009-04-21
IT'S WORKING.

I don't know why, but it's working now. I have internet access on my laptop, again.

The only thing I did was to uninstall firestarter. Could that be the problem? The last time it worked firestarter whas running.

Does anyone have an idea of what should I look in order to see what's different now that the network is working?

I don't know if next time I boot, it will still be working.

Thank you.

---

### Post by betete on 2009-04-22
Here I am again. I think I know what the problem is. I think that Ubuntu doesn't "connect" actually to the ad hoc network. Does anyone know if connection is established automatically with ifup? Or there is another way of connectiong?

---

