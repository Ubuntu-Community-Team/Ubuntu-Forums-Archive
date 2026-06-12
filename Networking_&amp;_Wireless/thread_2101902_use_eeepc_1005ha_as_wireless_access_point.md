---
title: "use eeepc 1005ha as wireless access point"
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by dieter-erich on 2013-01-05
Hi,
   sorry for posting twice but I understand that tutorials are not meat to add posts to any more (?). So, I repeat the post I appended at the end of the thread [http://ubuntuforums.org/showthread.php?t=1663788&page=2](http://ubuntuforums.org/showthread.php?t=1663788&page=2). I hope that this is not against the rules:


 I followed the tutorial above step by step for turning an eeePC 1005HA running   UBUNTU 10.04 into a wireless access point. However, when trying to  start all services with the script 'ap_ctl' I get the following error  message:

sudo ap_ctl  --start
Starting hostapd
    You can view the log at /var/log/hostapd.log 

(>>> I cannot  view the log because even with sudo I get ''Could not open configuration  file '/etc/hostapd/hostapd.conf' for reading.'<<<<)

Starting dnsmasq

dnsmasq: failed to bind DHCP server socket: Die Adresse wird bereits verwendet (i.e. in English: the address is already in use)

ifconfig -a yields the following:

eth0      Link encap:Ethernet  Hardware Adresse xxxxxxxxxxx  
          inet Adresse:10.70.145.4  Bcast:10.70.145.255  Maske:255.255.255.0
          inet6-Adresse: xxxxxxxxxxxx/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:58453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61981 errors:0 dropped:0 overruns:0 carrier:1
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:53887944 (53.8 MB)  TX bytes:9439886 (9.4 MB)
          Interrupt:28 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:3879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3879 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:5570857 (5.5 MB)  TX bytes:5570857 (5.5 MB)

wlan0     Link encap:Ethernet  Hardware Adresse xxxxxxxxxxx  
          inet Adresse:192.168.0.1  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6-Adresse: xxxxxxxxxxxx Gültigkeitsbereich:Verbindung
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:126 (126.0 B)  TX bytes:2036 (2.0 KB)

I do not see how the address would already be in use - what is wrong???????
also: when invoking:
 
sudo chkconfig  dnsmasq off
I get: /sbin/insserv: file or directory not found

so, something is damned wrong but I do not have any idea......
Thanks a lot for help, D-E

---

