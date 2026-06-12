---
title: "Need some help with Internet Connection Sharing"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by youoh on 2010-03-30
First my Network:

ADSLModem < --ppp0-- >  eth0|Ubuntu Maschine|eth1 <----> AcessPoint < --WiFi-- > Windows Maschines

Using networkmanager and firestarter.
eth0: not configured in nm
eth1: ipv4 settings on sharing mode(ip set to 10.42.43.1 automaticly)
ppp0: configured

Internet on the Ubuntu Maschine is working.
Acesspoint on 10.42.43.227 pingable
all windows maschines have fix ip adresses 10.42.43.100-200 and gateway/dns 10.42.43.1

firestarter is set to internet connection ppp0 and LAN connection eth1

samba is working fine also but no internet for the Windows maschines.

i hope someone can help me.

Mfg youoh

---

### Post by 98cwitr on 2010-03-30
can you ping the gateway from the windows ***machines***, what does a traceroute to the outside yield?

how is your DNS configured on the ubuntu ***machine***?

please post ifconfig from ubuntu ***machine***

---

### Post by youoh on 2010-03-30
windows maschines can ping access point, gateway(ubuntu) and ip of google.

don't know where to finde DNS config on the ubuntu maschine

```
youoh@dreamland:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:24:21:0c:a3:71  
          inet6-Adresse: fe80::224:21ff:fe0c:a371/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:916 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:628572 (628.5 KB)  TX bytes:143784 (143.7 KB)
          Interrupt:29 Basisadresse:0x4000 

eth1      Link encap:Ethernet  Hardware Adresse 00:e0:4c:d0:74:03  
          inet Adresse:10.42.43.1  Bcast:10.42.43.255  Maske:255.255.255.0
          inet6-Adresse: fe80::2e0:4cff:fed0:7403/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:41478 (41.4 KB)  TX bytes:4994 (4.9 KB)
          Interrupt:18 Basisadresse:0xc800 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ppp0      Link encap:Punkt-zu-Punkt-Verbindung  
          inet Adresse:89.245.219.79  P-z-P:62.214.64.191  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1492  Metrik:1
          RX packets:879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:893 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:3 
          RX bytes:608086 (608.0 KB)  TX bytes:123097 (123.0 KB)

```

tracert to google ip works. tracert to [www.google.de](www.google.de) brings : cannot resolve host.

---

### Post by youoh on 2010-03-30
setting DNS to googles 8.8.8.8 an the wiondows maschines does the trick. now it works

---

### Post by Iowan on 2010-03-30
If they were DHCP addresses, I'd suggest checking */etc/resolv.conf*... but I notice you got it working. 
If problem is fixed (might want to give it a couple of days), you can mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

