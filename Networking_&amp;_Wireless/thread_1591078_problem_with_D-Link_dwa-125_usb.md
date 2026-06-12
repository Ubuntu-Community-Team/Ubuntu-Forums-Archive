---
title: "problem with D-Link dwa-125 usb"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by linuxsawi on 2010-10-08
[B]hi, i am new to Linux world and i just installed ubuntu 10.4 on my desktop computer

(i used Wubi to install it inside windows) and every thing works great but the problem is that i can't connect to internet.
i have an adsl router in a room and in another room i have the desktop computer with 

D-Link dwa-125 usb adapter on it and it works perfectly on windows xp but on ubuntu

it's not, it's not  seeing any wireless network in range and it's not giving me a 

list of available wireless networks (counter to windows), now when i create a 

new wireless network it  says "Connection Established " but there is no internet activity.

now i searched over the internet for a solution but in vain.
so any help????[/B]

---

### Post by dineshs on 2010-10-08
> when i create a new wireless network it says "Connection Established " but there is no internet activity.
Can you post the output of```
ifconfig -a
``````
iwconfig
```and```
ping 4.2.2.1 -c5
```

---

### Post by linuxsawi on 2010-10-09
thanks for replay here is the output 

```
**ifconfig -a**

eth0      Link encap:Ethernet  HWaddr 00:25:22:2e:85:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12944 (12.9 KB)  TX bytes:12944 (12.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:5a:76:e6:08  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5aff:fe76:e608/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4292 (4.2 KB)


``````

**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:033A-642B-2B34-E55B-5B7A-79E8-8DE0-4338-4CA2-749C-33D7-C9BA-4CA2-749C-33D7-C9BA
          Power Management:on


``````

**ping 4.2.2.1 -c5**

connect: Network is unreachable



```

---

### Post by bkratz on 2010-10-09
[QUOTE=linuxsawi;9943343]thanks for replay here is the output 


wlan0     IEEE 802.11bgn  ESSID:"linksys"  
         [COLOR="Red"] Mode:Ad-Hoc[/COLOR]  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:033A-642B-2B34-E55B-5B7A-79E8-8DE0-4338-4CA2-749C-33D7-C9BA-4CA2-749C-33D7-C9BA
          Power Management:on


Ad-hoc is for connecting two computers together, try the following.

```
sudo iwconfig wlan0 mode managed

```

and retest

---

### Post by linuxsawi on 2010-10-09
hi this is the output
```

**sudo iwconfig wlan0 mode managed**

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.


```[B]
and when i disconnect from the network it accept the change

and the mode become "Manged" but when i connect to the network again 

the ESSID   is not "linksys". ](*,)](*,)](*,) what is happening, 

i think there is no solution for that right????????

[/B]

---

### Post by bkratz on 2010-10-09
> **linuxsawi said:**
> hi this is the output
```

**sudo iwconfig wlan0 mode managed**

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.


```[B]
and when i disconnect from the network it accept the change

and the mode become "Manged" but when i connect to the network again 

the ESSID   is not "linksys". ](*,)](*,)](*,) what is happening, 

i think there is no solution for that right????????

[/B]

Probably should have had you do

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up

```

and the mode should have been set without disconnecting, but I suspect it probably wouldn't make a difference in the final result.

Well, maybe worth a try again.

---

