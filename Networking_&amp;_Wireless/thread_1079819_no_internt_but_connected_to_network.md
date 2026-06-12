---
title: "no internt but connected to network"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by 50uth3rn on 2009-02-24
hi, the other day my internet jsut stopped working for no reason that i know of. one morning it just wouldnt work. i can connect to the network fine but it wont let me go online or ping any websites.
the strange thing is that my g/f's laptop running xp still work fine on the internet. so why does hers work fine and mine doesnt? im using a dell inspiron 1525n with ubuntu 8.04.
ive done a few searches but couldnt really find anything that helped.
any ideas on how to solve this problem would be very much appreciated. thanks.

---

### Post by darco on 2009-02-24
Post the output of ifconfig. Also right click the wired/wireless icon and click "connection information" and see all the info is present (ip addy,gateway,dns...)

darco

---

### Post by 50uth3rn on 2009-02-24
ok if config says:
adam@desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:ce:ef:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4643 (4.5 KB)  TX bytes:4643 (4.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:a3:72:08  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fea3:7208/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:641439 (626.4 KB)  TX bytes:178142 (173.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-A3-72-08-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


connection information is:
activ connection information
interface:802.11 WiFi (wlan0)
Speed: 24Mb/s
Driver: iwl3945

IP address: 192.168.0.102
Broadcast address: 192.168.0.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.0.1
Primary DNS: 192.168.0.1
Scondary DNS 0.0.0.0
Hardware address: 00:1F:3C:A3:72:08

im using roaming mode as well if that makes any difference.
all the dns etc match up with the working computer apart from the ip which is 1 number different
thanks

---

### Post by Hobgoblin on 2009-02-25
Try rebooting the router (switch it off, give it 20 seconds, switch it on).

---

### Post by 50uth3rn on 2009-02-25
rebooting the router didnt do anything but mysteriously when i got home from work tonight my internet is working fine. how strange. must be those gremlins!

---

### Post by sigmarhophi on 2009-02-27
I recently had the same issue.  I thought it was due to an upgrade from 8.04 to 8.10.  Did all types of searches, config changes, and suggested actions from the forums.  Here is what my issue was and how I resolved it.  On my laptop, running 8.04, I set up a static IP on my wired connection, always left wireless as DHCP do to hardly ever using it.  Life was good.  Then I upgraded to 8.10 and all was still good.  I then had the need to go wireless, so I fired up the card, and it connected to my local network as DHCP, no errors.  I could not however get on the net, or ping any local computers.  My solution was to open networkmanager, and delete both the wired connection and the wireless connection, thus clearing out my static IP and all other conenctions which the laptop may had made, or remembered.  performed a network restart: sudo /etc/init.d/network restart and then wirelessly reconnected to my local network as DHCP.  I was able to get on the net, ping local computers, etc.  I don't think this is a good solution as for I have now lost my settings for my static IP topology which I use for terminals, etc, but it fixed the wireless internet connection issue.

---

