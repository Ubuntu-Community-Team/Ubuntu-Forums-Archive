---
title: "Problem with Intel 82578DC ethernet card"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by jllb on 2010-01-14
Hi everybody,

I am an absolutely ignorant about linux who have get rid of windows 7 and installed a brand new ubuntu instead. Everything worked well but the ethernet card, which is an Intel 82578DC. 

It happens that the card works for a while when I boot the computer but then the connection is lost. Previously it worked well using windows 7.

Fortunately the wireless connection works well, but it would be nice to make the card to work. Any help will be greatly appreciated!

Antonio

---

### Post by barnex on 2010-01-14
can you give the output of:

```
ifconfig
```

?

---

### Post by jllb on 2010-01-14
> **barnex said:**
> can you give the output of:

```
ifconfig
```?

Thank you, here it is:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1979 (1.9 KB)  TX bytes:1979 (1.9 KB)

ra0       Link encap:Ethernet  HWaddr 70:1a:04:2f:ee:f1  
          inet addr:147.96.122.173  Bcast:147.96.127.255  Mask:255.255.248.0
          inet6 addr: fe80::721a:4ff:fe2f:eef1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:580015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:197876834 (197.8 MB)  TX bytes:6348145 (6.3 MB)
          Interrupt:19

---

### Post by barnex on 2010-01-14
You seem to have a public IP address. Are you by any chance trying to simultaneously connect to the wireless and wired network of the same router with NAT disabled?
edit: nevermind, this should still list eth0

---

### Post by jllb on 2010-01-14
> **barnex said:**
> You seem to have a public IP address. Are you by any chance trying to simultaneously connect to the wireless and wired network of the same router with NAT disabled?

I don't know. When the ethernet card stops working I use the wireless connection. 
When the computer boots -like right now- I can use eth0 and the output of ifconfig is different:

eth0      Link encap:Ethernet  HWaddr 00:01:6c:6f:72:79  
          inet addr:147.96.20.43  Bcast:147.96.20.255  Mask:255.255.255.0
          inet6 addr: fe80::201:6cff:fe6f:7279/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1533317 (1.5 MB)  TX bytes:5888 (5.8 KB)
          Memory:f9fc0000-f9fe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ra0       Link encap:Ethernet  HWaddr 70:1a:04:2f:ee:f1  
          inet addr:147.96.79.143  Bcast:147.96.79.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe2f:eef1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:521397 (521.3 KB)  TX bytes:4621 (4.6 KB)
          Interrupt:19

---

### Post by barnex on 2010-01-14
OK, when the wired goes down again, try:

```
sudo ifconfig eth0 up
```

---

### Post by jllb on 2010-01-14
> **barnex said:**
> OK, when the wired goes down again, try:

```
sudo ifconfig eth0 up
```

I tried it, but the wired keeps not working. Then I have to disconnect eth0 and connect to a wireless network to have internet access...

---

### Post by barnex on 2010-01-14
> **jllb said:**
> I tried it, but the wired keeps not working. Then I have to disconnect eth0 and connect to a wireless network to have internet access...

were any error messages printed in the terminal?

---

### Post by jllb on 2010-01-14
> **barnex said:**
> were any error messages printed in the terminal?

Sorry,  I use the NetworkManager Applet  so there is no terminal I can see when I disconnect eth0.

---

### Post by barnex on 2010-01-14
> **jllb said:**
> Sorry,  I use the NetworkManager Applet  so there is no terminal I can see when I disconnect eth0.

Errr, by my previous post I meant that you should actually open a terminal window and type the code:

```
sudo ifconfig eth0 up
```

Then see if any error messages are reported.

---

### Post by jllb on 2010-01-14
> **barnex said:**
> Errr, by my previous post I meant that you should actually open a terminal window and type the code:

```
sudo ifconfig eth0 up
```Then see if any error messages are reported.
No, there is no output.

---

### Post by barnex on 2010-01-14
> **jllb said:**
> No, there is no output.

This would suggest that eth0 should be in your ifconfig now. Do you have a wired connection for the moment? If not, please give the output of 
```

sudo ifconfig eth0 up
ifconfig

```

---

### Post by jllb on 2010-01-14
> **barnex said:**
> This would suggest that eth0 should be in your ifconfig now. Do you have a wired connection for the moment? If not, please give the output of 
```

sudo ifconfig eth0 up
ifconfig

```
OK, here it is. This is the output after shutting down eth0, connecting using wifi and writing your code:

eth0      Link encap:Ethernet  HWaddr 00:01:6c:6f:72:79  
          inet6 addr: fe80::201:6cff:fe6f:7279/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:504155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:917490 dropped:0 overruns:0 carrier:1376235
          collisions:458745 txqueuelen:100 
          RX bytes:46128067 (46.1 MB)  TX bytes:9117 (9.1 KB)
          Memory:f9fc0000-f9fe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:624 (624.0 B)  TX bytes:624 (624.0 B)

ra0       Link encap:Ethernet  HWaddr 70:1a:04:2f:ee:f1  
          inet addr:147.96.122.173  Bcast:147.96.127.255  Mask:255.255.248.0
          inet6 addr: fe80::721a:4ff:fe2f:eef1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:264870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48401822 (48.4 MB)  TX bytes:239531 (239.5 KB)
          Interrupt:19

---

### Post by barnex on 2010-01-14
OK, your wired connection did not obtain an IP(v4) addres. See this post: [http://ubuntuforums.org/showthread.php?t=1379937](http://ubuntuforums.org/showthread.php?t=1379937)

---

### Post by jllb on 2010-01-15
> **barnex said:**
> OK, your wired connection did not obtain an IP(v4) addres. See this post: [http://ubuntuforums.org/showthread.php?t=1379937](http://ubuntuforums.org/showthread.php?t=1379937)
OK, thank you.  I've tried to do so. Using "network settings" I forced the wired connection to DHCP. 
Magically, eth0 started to work again and I thought the problem was solved. 

However, after rebooting, eth0 seems to have disappeared. The NetworkManager Applet says about the wired network "device not managed", so I only can use wifi.

There is an additional problem. Randomly the computer freezes. I hope that it is due to this known issue [http://ubuntuforums.org/showthread.php?t=969887](http://ubuntuforums.org/showthread.php?t=969887), since caps lock and scroll lock are blinking too. I hope that the solution given will work (I suppose that "intrepid" must be substituted with "karmic" for this solution to work with ubuntu 9.10). 

Here is my ifconfig again:

eth0      Link encap:Ethernet  HWaddr 00:01:6c:6f:72:79  
          inet addr:147.96.20.43  Bcast:147.96.20.255  Mask:255.255.255.0
          inet6 addr: fe80::201:6cff:fe6f:7279/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:837336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:308 errors:655350 dropped:0 overruns:0 carrier:983025
          collisions:327675 txqueuelen:100 
          RX bytes:94636938 (94.6 MB)  TX bytes:53356 (53.3 KB)
          Memory:f9fc0000-f9fe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:752 (752.0 B)  TX bytes:752 (752.0 B)

ra0       Link encap:Ethernet  HWaddr 70:1a:04:2f:ee:f1  
          inet addr:147.96.126.143  Bcast:147.96.127.255  Mask:255.255.248.0
          inet6 addr: fe80::721a:4ff:fe2f:eef1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144108 errors:2 dropped:0 overruns:0 frame:0
          TX packets:6939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33696028 (33.6 MB)  TX bytes:1113522 (1.1 MB)
          Interrupt:19

---

### Post by jllb on 2010-03-17
OK, finally the problem was solved thanks to the fixed provided by Thomas in this thread:
[http://ubuntuforums.org/showthread.php?t=1390410](http://ubuntuforums.org/showthread.php?t=1390410)[U]

[/U]

---

