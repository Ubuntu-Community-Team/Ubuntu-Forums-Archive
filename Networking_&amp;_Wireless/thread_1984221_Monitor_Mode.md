---
title: "Monitor Mode"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by JonatasVT on 2012-05-21
Hi, I am trying to read packets from my wireless interface but I cannot...
That is what I get:
> 
padrao@Wall-E:~$ sudo airmon-ng start eth2


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
815    avahi-daemon
816    avahi-daemon
848    NetworkManager
874    wpa_supplicant


Interface    Chipset        Driver

eth2        Unknown         wl (monitor mode enabled)

padrao@Wall-E:~$ sudo airodump-ng eth2
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth2 <#>'
Sysfs injection support was not found either.

padrao@Wall-E:~$ sudo airodump-ng mon2
Interface mon2: 
ioctl(SIOCGIFINDEX) failed: No such device
padrao@Wall-E:~$ sudo airodump-ng mon0
Interface mon0: 
ioctl(SIOCGIFINDEX) failed: No such device
padrao@Wall-E:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

padrao@Wall-E:~$ ifconfig
eth0      Link encap:Ethernet  Endereço de HW 70:5a:b6:11:a3:37  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:43 

eth2      Link encap:Ethernet  Endereço de HW c4:17:fe:73:aa:04  
          endereço inet6: fe80::c617:feff:fe73:aa04/64 Escopo:Link
          UP BROADCAST  MTU:1500  Métrica:1
          pacotes RX:141 erros:0 descartados:0 excesso:0 quadro:6162
          Pacotes TX:140 erros:24 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:15933 (15.9 KB) TX bytes:20020 (20.0 KB)
          IRQ:16 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:48 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:48 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:3904 (3.9 KB) TX bytes:3904 (3.9 KB)


I just have reinstalled the driver by running :
What might be the problem?
sudo apt-get install --reinstall bcmwl-kernel-source

---

