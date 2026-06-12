---
title: "wireless conection dropping out but still showing it is still connected"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by pistolpoida on 2010-01-20
as the titles states my wireless is dropping out but the networks manager is still saying i have a connection. the only way i have been able to be on the network every minute or so i have to manauly disconnect and reconnect to my wifi. under my windows 7 and vista installs the wireless card works fine
now my card is a dlink dwa-547 and it uses the arthores chipset, it is encprtyed wifi, wpa2 aes on a n/g based network
```
peter@ubuntu:~$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:01:2f:e5:db
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.198 latency=168 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:fa100000-fa10ffff
peter@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"mccahon"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:21:91:15:36:F1   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

peter@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:50:c4:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12972 (12.9 KB)  TX bytes:12972 (12.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:01:2f:e5:db  
          inet addr:192.168.1.198  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1ff:fe2f:e5db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16573783 (16.5 MB)  TX bytes:1858398 (1.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-01-2F-E5-DB-32-66-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```does any one have any idea on how to get it working, i have tried using the windows drives by using the [B]ndisgtk and that just failed
[/B]

---

### Post by drpjkurian on 2010-01-20
Hi
 Please install the following packages by synaptic package manager
 They are linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic.
 
 This might help you. This solution was given by coffeecat

---

### Post by pistolpoida on 2010-01-22
OK i have tried what you suggested and that has failed too unfortunately, btw this is using the ath9k drivers.

---

### Post by drpjkurian on 2010-01-24
Hi Pistolpodia

Please visit my thread especially from page 2 onwards. A forum member Bac522 has mentioned some tips on ath9. The URL is [http://ubuntuforums.org/showthread.php?t=1309072&page=2](http://ubuntuforums.org/showthread.php?t=1309072&page=2)

---

### Post by fosschick on 2010-01-27
> **pistolpoida said:**
> OK i have tried what you suggested and that has failed too unfortunately, btw this is using the ath9k drivers.

Try again, and don't forget to reboot afterwards.  ;)

I'm having no wireless problems with ath9k now at 2.6.31-17-generic.

---

### Post by ionicswing on 2010-01-27
I am having a very similar problem at home(laptop). With windows vista network seems to be fine occasionally have to reconnect. kubuntu 9.1 connection will work however it will loose connection very often. very similar to above, but I carry my laptop to work also and have no problems what so ever with windows or kubuntu. What could be the cause of this? The wireless network at work is unsecure, and at home was wpa/PPPoE for dsl. I have never paid attention to how the network at work is set up, but it is dsl also. Thinking it was a possible security issue I changed home network to unsecure, and still having problems, any idea's??

---

### Post by fosschick on 2010-01-28
> **ionicswing said:**
> I am having a very similar problem at home(laptop). With windows vista network seems to be fine occasionally have to reconnect. kubuntu 9.1 connection will work however it will loose connection very often. very similar to above, but I carry my laptop to work also and have no problems what so ever with windows or kubuntu. What could be the cause of this? The wireless network at work is unsecure, and at home was wpa/PPPoE for dsl. I have never paid attention to how the network at work is set up, but it is dsl also. Thinking it was a possible security issue I changed home network to unsecure, and still having problems, any idea's??

Have you followed the advice given above yet?  You should try installing linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic:

sudo apt-get install linux-backports-modules-karmic-generic
sudo apt-get install linux-backports-modules-wireless-karmic-generic

Then reboot, and let us know if the connection is better, worse, or if your house catches fire.

---

### Post by ionicswing on 2010-01-30
ok, tried that and still same problem, not sure if it helped at all, but did not harm from what i can tell. but for a large portion of tonight i have been on my "works" network, and have absolutely zero problems. which im not an linux expert what so ever, but that leads me to think its a problem with my network rather than linux itself, but i cant think of anything that would be causing it. again "work" network is unsecure, and i changed home network to unsecure..same problem

---

### Post by ionicswing on 2010-01-31
bump

---

