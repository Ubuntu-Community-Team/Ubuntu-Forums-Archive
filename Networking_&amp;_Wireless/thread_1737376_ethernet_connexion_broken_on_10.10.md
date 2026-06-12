---
title: "ethernet connexion broken on 10.10"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by domv on 2011-04-23
Hello,
I have broken my ethernet connectivity on ubuntu 10.10 x64 when i tried to install wifi access using SMCWUSB-N2 device which is supposed to be supported out of the box.
I mesed up with network paramters following ubuntu documentation and now I have to post this thread using an other PC with windows XP connected to my ADSL box.
 
I tried to setup the connexion using network manager, but it seems that the application does not modify anything
 
Could someone help me solving this ethernet issue before trying to set up again the wifi network (I tested the USB wifi with XP and it works fine...=> no HW problem).
The led attached to the ethernet input is active on my ADSL box, but no led (yellow or green) is active on the ethernet connector of motherboard of my Ubuntu PC. Seems that the ethernet interface is inhibited on the PC.
 
CPU:I3 2100
mobo: ASUS P8H67 -M Pro
RAM: 4G
HDD: 64G SSD
LAN: realtek 8111E Gigabit ethernet
 
Below extract of the network configuration when the USB wifi is not connected and ethernet & internet not working.
 
[EMAIL="domi@salon:~$"]domi@salon:~$[/EMAIL] ifconfig -a
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:e3:2f:38  
          inet adr:192.168.27.1  Bcast:192.168.27.15  Masque:255.255.255.240
          adr inet6: fe80::beae:c5ff:fee3:2f38/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:36 erreurs:0 :0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:4410 (4.4 KB) Octets transmis:14577 (14.5 KB)
          Interruption:45 Adresse de base:0xa000 
lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:2142 erreurs:0 :0 overruns:0 frame:0
          TX packets:2142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:168276 (168.2 KB) Octets transmis:168276 (168.2 KB)
[EMAIL="domi@salon:~$"]domi@salon:~$[/EMAIL] cat /etc/network/interfaces
auto eth0
iface eth0 inet dhcp
auto lo
iface lo inet loopback
[EMAIL="domi@salon:~$"]domi@salon:~$[/EMAIL] nm-tool
NetworkManager Tool
State: connected
- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        BC:AE:C5:E3:2F:38
  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s
  Wired Properties
    Carrier:         on
  IPv4 Settings:
    Address:         192.168.27.1
    Prefix:          28 (255.255.255.240)
    Gateway:         192.168.27.14
 
Thanks for any help

---

### Post by domv on 2011-04-24
was a configuration problem on my ADSL box: Ethernet link allocated to my ubuntu computer was configured for TV box interface not for ethernet.
 
Now works ok with eth0
 
Trying now to setup wifi connexion

---

