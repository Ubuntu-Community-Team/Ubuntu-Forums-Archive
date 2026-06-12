---
title: "Wireless Connectivity Problem in Ubuntu 11.04"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by arasan on 2011-04-29
Hi, 

I have installed Ubuntu 11.04 and i am using Linksys Wireless WUSB54GC Network Adapter.
Now the Problem is, when i am trying to connect wireless network, it is trying to authenticate WPA/WPA2 Personal password. but it is not authenticated.
I checked the password. it is correct

In my Access Point, i have enabled WPA/WPA2 security key. 


[COLOR=Sienna]But if i am connecting with other wireless modem which is configured by WEP security, it is working fine[/COLOR]


then why it is not authenticating with WPA/WPA2 Security:confused::confused::confused:

I am in trouble. i cannot access internet with my new Ubuntu OS

I don't know what to do? Please help

---

### Post by DaimonPl on 2011-05-02
Same problem here (also WUSB54GC)... It worked fine in older ubuntu.

Still searching for solution

---

### Post by Talon2 on 2011-05-02
This bug will provide a lot of information:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

---

### Post by DaimonPl on 2011-05-02
Thx for reply. There are some differences between this bug and our/mine case.

Bug is about Ubuntu 10.04 (worked fine for me) - current problem is with Ubuntu 11.04 (it seems to be regression).

Bug is about rt2870 Chipset - mine is rt17. I'll try to blacklist listed drivers and see what happens.

---

### Post by DaimonPl on 2011-05-03
The problem is not solved... i get DHCP timeout according to syslog

---

### Post by piggoy on 2011-05-03
Exact same problem here. I wish a solution is found to this issue soon. Appears to be a DHCP timeout.

---

### Post by piggoy on 2011-05-08
After a week of trawling the web I have found the solution :guitar:

```
sudo iwconfig wlan0 power off
```

To permanently activate this feature, you need to edit /etc/rc.local
Add the following line -

```
iwconfig wlan0 power off
```

I hope this helps

---

### Post by grahampositive on 2011-09-23
> **piggoy said:**
> 

```
sudo iwconfig wlan0 power off
```



I tried this and got the result 

```
 Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

```

I am using WUSB11v2.6 on Ubuntu 11.04 and WPA encryption. if encryption is turned off, I can connect fine. WEP64/128 bit encryption fails too. also seems to be a timeout error. I have wpasupplicant v 0.7.3 installed. what gives? I had to go through hell and back to get the drivers for this thing to work in the first place. I have been all over the web and I am on my last nerve :/ please help!

:edit:
IWconfig result
```
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Belkin Wireless 351013"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

ifconfig result 
```

eth0      Link encap:Ethernet  HWaddr 00:30:1b:80:14:0b  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:fe80:140b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29694481 (29.6 MB)  TX bytes:1650104 (1.6 MB)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0c:41:0d:10:b2  
          inet6 addr: fe80::20c:41ff:fe0d:10b2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:304 (304.0 B)  TX bytes:4839 (4.8 KB)

```

---

