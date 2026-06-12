---
title: "Broke my network settings, how do I restore them?"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by Xavier Oddmon on 2009-07-04
Hello! I was trying to configure internet connection sharing with my xbox 360, following this guide: [http://onlyubuntu.blogspot.com/2008/08/howto-share-internet-connections-in.html](http://onlyubuntu.blogspot.com/2008/08/howto-share-internet-connections-in.html).

When restarting networking, I was unable to connect to the internet. So, I restored /etc/network/interfaces to its original contents, 
```
auto lo
iface lo inet loopback
```

Still no luck. I have restarted my machine, i've tried changing the file to read 
```
auto eth0
iface eth0 inet dhcp
```
And I have tried the same with wlan0. (It's back to the initial state at the moment.) 

Network manager shows that I'm currently connected to my local wifi ("Good Old Internet") I'm also wired to the router. 

ifconfig returns this:
```

eth0      Link encap:Ethernet  HWaddr 00:1d:92:4d:40:41  
          inet addr:10.0.0.12  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fe4d:4041/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75288 (75.2 KB)  TX bytes:3148 (3.1 KB)
          Interrupt:249 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2919083 (2.9 MB)  TX bytes:2919083 (2.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:b7:b9:cf  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:feb7:b9cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:209776 (209.7 KB)  TX bytes:4246 (4.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-B7-B9-CF-39-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

Yet still, I cannot connect to the internet. 

(Also, not sure if it's relevant, but I have installed bridge-utils, but haven't used it. brctl show returns one network with no interfaces, "pan0".)

---

### Post by Iowan on 2009-07-04
"pan0" is usually Personal Area Network (ie, bluetooth).
Have you checked the settings under Network Manager applet? The */etc/network/interfaces* settings will bypass Network Manager, but you may need to manually edit */etc/resolv.conf*.
Having eth0 and wlan0 in the same subnet normally doesn't work... but I haven't used bridging, either.

---

### Post by Xavier Oddmon on 2009-07-05
I checked /etc/resolv.conf, all it says is
```

nameserver 10.0.0.1

```
which is my router's IP address. Is there supposed to be something else here?

---

### Post by Xavier Oddmon on 2009-07-05
> The /etc/network/interfaces settings will bypass Network Manager, but you may need to manually edit /etc/resolv.conf.

Is there some way I can make it *stop* bypassing the network manager? The network manager is acting as if i'm connected to my router, and it properly reports signal strength.

---

### Post by Iowan on 2009-07-05
> **Xavier Oddmon said:**
> Is there some way I can make it *stop* bypassing the network manager?  Delete (or comment out) the eth0 settings in */etc/network/interfaces* and set up the configuration via the Network manager applet.

---

### Post by Xavier Oddmon on 2009-07-07
Okay, I think I may be making some progress. /etc/network/interfaces is just an empty file now. And I can connect to the internet, but not normally. When I boot up, my programs cannot access the internet. But, if I run wvdial, and then disconnect from my phone, my programs start using the wireless network again! But I have to do this every time I reboot. Is there some way I can check and see what is changing when wvdial is run? 
Thanks in advance.

---

### Post by Iowan on 2009-07-07
> **Xavier Oddmon said:**
>  /etc/network/interfaces is just an empty file now.*/etc/network/interfaces* should still have the definition for the loopback device: ```
auto lo
iface lo inet loopback

```Check **ifconfig -a** before/after **wvdial** to see what (if anything) is changing there.  You can also see if something in **route -n** is changing.

---

### Post by Xavier Oddmon on 2009-07-07
Alright, thanks again. I tried gave it a shot, here's what happened:

```

chris@chris-laptop:~$ cd Desktop/
chris@chris-laptop:~/Desktop$ ifconfig -a > ifconfig1
chris@chris-laptop:~/Desktop$ route -n > route1
chris@chris-laptop:~/Desktop$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory
--> Cannot open /dev/rfcomm0: No such file or directory
chris@chris-laptop:~/Desktop$ sudo ../Scripts/bluetoothModem 
[sudo] password for chris: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99 ***1#
--> Waiting for carrier.
ATDT*99 ***1#
CONNECT
~[7f]}#@!}!}!} }4}(}"}'}"}"}&} } } } }%}&y9'[02][17]8~
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}"} }4}(}"}'}"}"}&} } } } }%}&y9'[02]][05]~
--> PPP negotiation detected.
--> Starting pppd at Tue Jul  7 20:26:29 2009
--> Pid of pppd: 4196
--> Using interface ppp0
--> pppd: &#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]
--> local  IP address 10.146.167.70
--> pppd: &#65533;&#65533;&#65533;[08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;&#65533;[08]
--> primary   DNS address 172.16.145.103
--> pppd: &#65533;&#65533;&#65533;[08]
--> secondary DNS address 172.16.145.103
--> pppd: &#65533;&#65533;&#65533;[08]
^CCaught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: &#65533;&#65533;&#65533;[08]
--> Connect time 0.3 minutes.
--> pppd: &#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]
--> Disconnecting at Tue Jul  7 20:26:46 2009

chris@chris-laptop:~/Desktop$ ifconfig -a > ifconfig2
chris@chris-laptop:~/Desktop$ route -n > re
reinstate  reject     
chris@chris-laptop:~/Desktop$ route -n > route2
chris@chris-laptop:~/Desktop$ diff ifconfig1 ifconfig2
13,14c13,14
<           RX packets:4271 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:4271 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:5333 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:5333 errors:0 dropped:0 overruns:0 carrier:0
16c16
<           RX bytes:1762586 (1.7 MB)  TX bytes:1762586 (1.7 MB)
---
>           RX bytes:2069475 (2.0 MB)  TX bytes:2069475 (2.0 MB)
29,30c29,30
<           RX packets:27 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:379 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
32c32
<           RX bytes:5673 (5.6 KB)  TX bytes:834 (834.0 B)
---
>           RX bytes:238740 (238.7 KB)  TX bytes:68498 (68.4 KB)
chris@chris-laptop:~/Desktop$ diff route1 route2
chris@chris-laptop:~/Desktop$ 

```

This doesn't look like useful information to me. But I attached the files anyway (appending the .txt extension for the forum software.)




Man, I don't want to have to re-install. Although I could use this as an excuse to try out 64 bit again...

PS. Just thought it would be worth mentioning, for reading the attached files: my router is configured to assign IP addresses such as 10.0.0.*, not 192.168.1.*. my laptop is fixed at 10.0.0.3.

---

