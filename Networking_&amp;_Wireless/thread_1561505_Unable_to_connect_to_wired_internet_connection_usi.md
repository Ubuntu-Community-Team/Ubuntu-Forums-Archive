---
title: "Unable to connect to wired internet connection using Ubuntu"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by srini46@gmail.com on 2010-08-26
Hello I am unable to connect to the Internet using a wired connection. I  was able to use the wired network yesterday. But I had problems with  the flash player, so had to reinstall Ubuntu again. I am able to connect  to Internet using wireless connection. But I need to connect to the  wired connection. I am using Ubuntu 10. In my IPv4 settings, it is  automatically set to DHCP, using which, I was earlier able to connect.  But now it doesn't seem to be happening. Can somebody help me with this.

---

### Post by dineshs on 2010-08-26
Connect your cable and run ```
sudo dhclient
```
If it is not working pl post the results of
```
ifconfig -a
```

---

### Post by srini46@gmail.com on 2010-08-26
response for sudo dhclient

Listening on LPF/wlan0/00:26:82:3c:ac:27
Sending on   LPF/wlan0/00:26:82:3c:ac:27
Listening on LPF/eth0/18:a9:05:22:cd:f9
Sending on   LPF/eth0/18:a9:05:22:cd:f9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPREQUEST of 192.168.1.105 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPREQUEST of 192.168.1.105 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14


response for ifconfig 

eth0      Link encap:Ethernet  HWaddr 18:a9:05:22:cd:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 18:a9:05:22:cd:f9  
          inet addr:169.254.10.43  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:28 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64016 (64.0 KB)  TX bytes:64016 (64.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:82:3c:ac:27  
          inet6 addr: fe80::226:82ff:fe3c:ac27/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:52142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60816983 (60.8 MB)  TX bytes:4160159 (4.1 MB)

Thanks

---

### Post by Vishal Agarwal on 2010-08-26
> **srini46@gmail.com said:**
> 

eth0:avahi Link encap:Ethernet  HWaddr 18:a9:05:22:cd:f9  
          inet addr:169.254.10.43  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:28 Base address:0x4000 



You need to delete this. after that you will be able to get connected through the wired network.

---

### Post by srini46@gmail.com on 2010-08-26
how can I delete that?? I am a complete newbie too Ubuntu's networking!

---

### Post by dineshs on 2010-08-27
Can you post the contents of
```
 sudo gedit /etc/network/interfaces
```
You may also copy the contents and save it in a file for ref
Now if you are using Network manager,edit the same file so that it contain only
```
auto lo
iface lo inet loopback

```

---

### Post by soundofbread on 2010-08-28
> **Vishal Agarwal said:**
> You need to delete this. after that you will be able to get connected through the wired network.

I am also having this same exact issue, terminal is saying the same thing for me here.. like wise I am also a noob, and do not know how to delete this...

---

### Post by soundofbread on 2010-08-29
when I type sudo iwconfig

   lo       no wireless extentions.
 eth0       no wireless extentions.
 eth1       no wireless extentions.
wlan0       IEEE 802.11abgn   ESSID: "Sealab 2021"
            Mode:Managed Frequency:2.457 GHz Access point: 00:14:51:and so on
            Bit Rate=18 Mb/s    Tx-Power=6 dBm                                                                 Retry  long limit: 7    Rts thr:off Fragment thr:off 
            Encryption key:off
            Power Management : on
            Link Quality=70/70 Signal level=39 dBm
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
            Tx Excessive retries:0 Invalid misc:0 Missed beacon:0

Here, and in WICD it tells me I am connected to one of my routers (sealab 2021), but I also have it wired in.. 

I can not get an IP address when I try to connect with the wire.

AND even though it shows me I am connected to a network that has internet, I can't use the internet.. 

(Its really strange, it will load like half of the [www.google.com](www.google.com) page) (and it will preform searches on the google page, but I cannot go to any other websites at all, and it will not load any of the links from the google searches)


when I type this code:

cat /etc/resolv.conf

I get

nameserver 10.0.1.1

I really have no idea what to do to try and get either the wired connection or wireless going... preferably both

Any help is GREATLY appreciated
-soundofbread

---

### Post by dineshs on 2010-08-30
soundofbread,
What do you get for this?post results
```
sudo gedit /etc/network/interfaces
```

---

