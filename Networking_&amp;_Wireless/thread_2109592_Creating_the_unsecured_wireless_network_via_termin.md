---
title: "Creating the unsecured wireless network via terminal?"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by rushikesh988 on 2013-01-28
I am **able to create a new wireless connection from network manager** with my wireless card  now I **want to do this by using command line** so  that i can use this on scripts. it should be unsecured network.

Please tell me How can I Create the unsecured wireless network via command line??

---

### Post by rushikesh988 on 2013-01-28
anyone ...??

---

### Post by matt_symes on 2013-01-28
Hi
 
Assuming wlan0 is your wireless interface....
 
```
 
sudo iwconfig wlan0 essid <your_ssid>
sudo dhclient wlan0

```
 
Kind regards

---

### Post by Warren Hill on 2013-01-28
Take a look here too
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

### Post by rushikesh988 on 2013-01-29
> **matt_symes said:**
> Hi
 
Assuming wlan0 is your wireless interface....
 
```
 
sudo iwconfig wlan0 essid <your_ssid>
sudo dhclient wlan0

```
 
Kind regards
will it automatically give the access to my ethernet network to user??
I mean I have an ethernet connnectivity  with internet access and I just want to share that internet via Wifi ..

---

### Post by rushikesh988 on 2013-01-29
matt_symes 
I have done this with your commands but it doesn't seem to work

---

### Post by matt_symes on 2013-01-31
Hi

Before we go any further please read these:

[https://help.ubuntu.com/community/GettingAnswers](https://help.ubuntu.com/community/GettingAnswers)

Please supply for more information, otherwise no-one on this forum will have a hope of helping you.

First open a terminal and type these commands and post back the results.

```
ifconfig
iwconfig
sudo iwlist wlan0 scan
lspci -nnk | grep -iA3 wireless
lsusb
```

> will it automatically give the access to my ethernet network to user??
I mean I have an ethernet connnectivity  with internet access and I just want to share that internet via Wifi ..

Can you please explain this more.
> 
matt_symes 
I have done this with your commands but it doesn't seem to work

You have given no diagnostic information here. What did you do ? What happened ?

Kind regards

---

### Post by rushikesh988 on 2013-01-31
Thanks for the reply sir ,
I have taken the output of the commands that you have told me after the reboot (no commands are executed before it). following are its output:

> sbpcoe@sbpcoe:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 44:87:fc:a5:6d:59  
          inet addr:172.16.3.8  Bcast:172.16.3.255  Mask:255.255.252.0
          inet6 addr: fe80::4687:fcff:fea5:6d59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4621 errors:0 dropped:120 overruns:0 frame:0
          TX packets:678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:896734 (896.7 KB)  TX bytes:104364 (104.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7462 (7.4 KB)  TX bytes:7462 (7.4 KB)

wlan0     Link encap:Ethernet  HWaddr 2c:b0:5d:70:0b:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


> sbpcoe@sbpcoe:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.


> sbpcoe@sbpcoe:~$ sudo iwlist wlan0 scan
[sudo] password for sbpcoe: 
wlan0     No scan results

sbpcoe@sbpcoe:~$ 


> sbpcoe@sbpcoe:~$ lspci -nnk | grep -iA3 wireless
sbpcoe@sbpcoe:~$ 

> sbpcoe@sbpcoe:~$ lsusb
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
sbpcoe@sbpcoe:~$ 


---

### Post by rushikesh988 on 2013-01-31
> will it automatically give the access to my ethernet network to user??
I mean I have an ethernet connnectivity with internet access and I just want to share that internet via Wifi ..
Can you please explain this more. 



I have the wired internet connection to my desktop and I want to share this internet connection via Wi-Fi to other devices like mobiles and laptops.

---

### Post by rushikesh988 on 2013-01-31
> You have given no diagnostic information here. What did you do ? What happened ?


Actually Sir I have tried to typing the commands  
> sudo iwconfig wlan0 essid rushikeshtade
sudo dhclient wlan0

It took some time to complete execute the second command.

When it get executed I tried to search the network on the mobile and my laptop but these devices were not showing the wireless network. So I came to decision that these commands are not wortking.


At the same Time I have tried typing the command > ifconfig
eth0      Link encap:Ethernet  HWaddr 44:87:fc:a5:6d:59  
          inet addr:172.16.3.8  Bcast:172.16.3.255  Mask:255.255.252.0
          inet6 addr: fe80::4687:fcff:fea5:6d59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37890 errors:0 dropped:2056 overruns:0 frame:0
          TX packets:1559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4082743 (4.0 MB)  TX bytes:238412 (238.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15024 (15.0 KB)  TX bytes:15024 (15.0 KB)

wlan0     Link encap:Ethernet  HWaddr 2c:b0:5d:70:0b:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 2c:b0:5d:70:0b:bc  
          inet addr:169.254.7.147  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1




Hope this will give idea of my problem . If I need to give more details please inform me .

Thank you !

---

