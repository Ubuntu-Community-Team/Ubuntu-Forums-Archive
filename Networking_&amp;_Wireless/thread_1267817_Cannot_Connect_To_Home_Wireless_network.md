---
title: "Cannot Connect To Home Wireless network"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by Gidskid on 2009-09-16
Hi there, I have been using Ubuntu 9.04 since April. I have had no significant problems, until now. Since Monday, I have not been able to connect to the Wifi network at my house. I can connect to the network, and it shows 2 or 3 bars of strength, but when I open Firefox, Pidgin or Spotify, it says there is no connection. I really have no idea what to do. I typed ifconfig into the terminal and it gave me a write up but I don't understand it. 
I have a HP Pavilion ZE4900 with a 3com wifi card which has worked flawlessly since October last year. Please help.


G

---

### Post by lvlint67 on 2009-09-16
first: can other computers connect to the internet
second: is there a wired connection from the laptop to something?

Any chance you can give the output of ifconfig?
atleast the ip-address for each adapter listed?

my guess is that you are having a conflict with another network device in the computer (ie the wired network port) and firefox may be trying to us that for internet acess.

---

### Post by badger_fruit on 2009-09-16
I wonder if the user can PING the router's IP address or any other machines on his LAN?

```
ping 192.168.0.1
```
(replace 192.168.0.1 with the IP address of your router or another PC that's connected to the router)

If that works, can you then try
```
ping www.google.com
```

What do you get from that?

Please post the output of
```
sudo ifconfig
```

(although I've just noticed lvlint67 already asked for this lol!)

Has the WEP or WPA key changed on the router?  This is something you need to connect to the router and discover (or reset as it probably won't display it for security reasons).

Regards

---

### Post by Gidskid on 2009-09-16
In answer to Lvlint67's question, Yes other computers can connect to the internet. There is nothing else plugged into the laptop i.e no ethernet.


EDIT


Just tried with ethernet but no such luck, I'm now contemplating whether to do a fresh install instead?

---

### Post by Gidskid on 2009-09-17
Hi I'm connected to the internet now, this is by inserting a live cd. I don't know if it still relevant but when i type ifconfig i get the following :  Link encap:Ethernet  HWaddr 00:c0:9f:57:82:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0f:cb:b2:b9:d4  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:cbff:feb2:b9d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3324992 (3.3 MB)  TX bytes:358592 (358.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-CB-B2-B9-D4-39-64-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Iowan on 2009-09-17
Armed with the info from the LiveCD, check IP address, etc. when booted normally. If you are using Network Manager, verify that there is no configuration for the interfaces in */etc/network/interfaces*.

---

### Post by wilee-nilee on 2009-09-17
I ran into a similiar problem about a week ago no network manger even showing but I was getting wireless anyway. I installed wicd then everything worked again, just for kicks I reinstalled the network manager and everything was back to normal
 
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by MaindotC on 2009-09-18
Are you dual-booting with XP or Vista and if so, did you properly shut down the machine in Windows?  Do you have the windows driver installed on the other partition?

---

### Post by Gidskid on 2009-09-21
NO i am not dual booting. Ubuntu only!

---

### Post by MaindotC on 2009-09-21
> **Gidskid said:**
> Ubuntu only!

Good to read that :D

Did you at any time have Windows on this machine and was it operating the wireless card, and if so was it properly shut down?

---

