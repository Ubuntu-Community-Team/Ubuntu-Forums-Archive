---
title: "help with sitecom usb network card after upgrade 10.04 -&gt;12.04"
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by Hetepeperfan on 2012-10-26
Hello,

I would like some information about this network card:

```
ID 0df6:0062 Sitecom Europe B.V.

```It's a wireless usb network card. I used this card with Ubuntu 10.04 and this night I upgraded to 12.04. Under 10.04 I used to compile the 2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO driver each time the updates renewed the kernel. And then I run some script when i boot into the computer. that ran modprobe, wpa_supplicant and dhclient to get the device up and running. I got a bit tired and hoped that an upgrade to 12.04 would solve this driver issues. Unforunately this only made my problems worse, since the network-manager can't enumerate my eth0 device and I ve to run dhclient eth0 to get my network wired up and running.
Als at boot time ubutu shows messages that it is trying to configure my networksettings and then wait another 60 seconds to do so, and the login screen appears.

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:74:e1:be  
          inet addr:192.168.2.19  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe74:e1be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3009399 (3.0 MB)  TX bytes:290107 (290.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32120 (32.1 KB)  TX bytes:32120 (32.1 KB)

```Under 10.04 after modprobing the driver there also was a ra0 network device. And here eth0 is connected because I have run ```
sudo dhclient eth0
``` manually .

Does anyone know what might be wrong?
any help is most welcome

maarten

---

### Post by Hetepeperfan on 2012-10-30
Dear community, 

I didn't get any replies yet so please allow me to rephrase my question. There are actually two questions in post above.  

The first is why isn't my wireless network card found?
The second is why does Precise Pangolin does also not connect my eth0 a wired connection?

The first might be obvious, the driver is not installed since I used to compile it myself from source in Ubuntu 10.04 LTS.

The second is a bit more strange though. Why does do my eth0 device noting after boot and when I run dhclient as root on it, it connects straight away?

well I hope for a bit more responses this time.

Kind regards,

Maarten

---

### Post by Hetepeperfan on 2012-10-31
Well I'm a bit further with my 2 problems the bes part is that running

```
sudo service network-manager start
```

solves both my problems, but why do I have to run it? Shouldn't the network-manager service be started at boottime?

1 the wired eth0 seems connected
2 I get a wlan device that is connected to my WIFI.

Can anyone please help what to do to start the network manager on boot?

kind regards,

maarten

---

