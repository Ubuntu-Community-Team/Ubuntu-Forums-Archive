---
title: "wireless connection established but no internet"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by #1 fisherman on 2010-09-24
Hi just got a new usb wireless adapter i set up connection to my home network.The network icon says connection established but i cant bring up the Internet i contacted belkin support.They said i need to change my static ip  address to 192.168.2.1 preferred dns server as 208.67.222.222 alternate dns server as 208.67.220.220 i ran the command ifconfig 
denver@denver-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Belkin.3FB1"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 7E:7E:22:61:0F:D6   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
denver@denver-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105532 (105.5 KB)  TX bytes:105532 (105.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:0e:3c:33  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::2a1:b0ff:fe0e:3c33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:12261 (12.2 KB)

denver@denver-laptop:~$ 
does anyone see my problem from this info your repy would be greatly appriciated
  Oh and by the way i hardly know what any of this means

---

### Post by linux-hack on 2010-09-24
I dont think thats the good config. Who told you to change your IP to 10.42.43.1 (this kind of ip with .1 to the end is a Default Gateway)

What is the IP range on your router ? Usualy its 192.168.0/1.2-254

---

### Post by #1 fisherman on 2010-09-24
I didnt change it thats what it is i want to change it to what it needs customerv support at belkin give me the one it needs

---

### Post by #1 fisherman on 2010-09-24
sorry if i didnt make myself clear the right ip address is in the first paragragh of my first post at least thats what he told me it was the # 192.168.2.1 i dont know how to change it and was wondering if that was the solution to having no internet  the  other # is what it is now without changing it 
I think it was 10 something

---

### Post by dineshs on 2010-09-24
If you are using Network manager set static IP as follows
Right-click on the NM icon(on top right of the panel) and then click on Edit Connections.
Select the tab, wireless
select the wireless connection you want and click edit
select ipv4
method-manual
address [COLOR="Purple"]192.168.2.100[/COLOR]
mask [COLOR="Purple"]255.255.255.0[/COLOR]
gateway [COLOR="Purple"]192.168.2.1[/COLOR]
then hit enter
DNS [COLOR="Purple"]4.2.2.1[/COLOR]
then click apply
note:You can also use  DNS  provided by ISP

---

### Post by #1 fisherman on 2010-09-24
thank you very much for the reply still said cant find server do i need to reboot or something

---

### Post by dineshs on 2010-09-24
You can stop  NM using
```
sudo service network-manager stop
```
and start again using```
sudo service network-manager start
```
If you still have problems pl post the result of```
ifconfig -a
```and```
cat /etc/network/interfaces
```

---

### Post by #1 fisherman on 2010-09-24
still says server not found here is results 
denver@denver-laptop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24192 (24.1 KB)  TX bytes:24192 (24.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:0e:3c:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

denver@denver-laptop:~$

---

### Post by #1 fisherman on 2010-09-24
here is results for the other 
denver@denver-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

denver@denver-laptop:~$

---

### Post by dineshs on 2010-09-24
Can you run```
sudo dhclient wlan0
```and post the result of ```
ifconfig -a
```and```
iwconfig
```

---

### Post by linux-hack on 2010-09-24
if you want to configure 'it manually you can do 

[http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/](http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/)

---

### Post by #1 fisherman on 2010-09-24
Sorry it took so long to post it was 4 am and i fell asleep here are the code results , and thanks again its been a headache 
denver@denver-laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:a1:b0:0e:3c:33
Sending on   LPF/wlan0/00:a1:b0:0e:3c:33
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
denver@denver-laptop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6784 (6.7 KB)  TX bytes:6784 (6.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:0e:3c:33  
          inet6 addr: fe80::2a1:b0ff:fe0e:3c33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:11588 (11.5 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:a1:b0:0e:3c:33  
          inet addr:169.254.5.27  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

denver@denver-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Belkin.3FB1"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 9E:61:78:21:40:CC   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
denver@denver-laptop:~$ 
.

---

