---
title: "Cannot connect to internet (with decent speeds) via any method"
date: 2012-06-09
forum: Networking &amp; Wireless
---

### Post by WeasuhL on 2012-06-09
Been working on this problem for over 7 hours straight and I've viewed hundreds of forum threads from multiple forums, nothing will work for me.

The story is: I used to have Vista. I tried going into BIOS to increase my fan speed but I accidentally hit F9 and went into system restore. I attempted to cancel the restore but it was already at 5% and somehow wiped my boot partition. So then I had the "BOOTMGR IS MISSING" error. I hated Vista anyway so I was like alright, clean install Ubuntu (after spending hours trying to fix the Vista error..)!

So, I clean installed Ubuntu. Everything was fantastic. Then my Internet randomly dropped. No connection whatsoever. I've tried many things;

wlan power off (Some problem with the wireless adapter not receiving enough power) - no effect at all

Some problem with the network manager malfunctioning after an interruption or a suspend; disabled and enabled..no effect.

Tried a different cable.

etc

I BELIEVE it is a driver issue. This is the result of lspci

```
 00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce G 100] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
04:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

```

I believe the problem is somewhere within

"02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
04:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)"

If you google that with a +ubuntu or something, apparently many people that that hardware have problems. When I go to realtek however..ugh, basically I can't find out how to update my drivers.

My wired internet won't work at all. Whether I plug into the router or directly into the modem, whether I do DHCP or static..it won't connect at all. Wireless peaks at 2MB/S speeds (I'm expected 15-25, AT LEAST 10) 2MB/S is ridiculous and unbearable. 

I'm willing to run any test just let me know the commands. I'm not sure what is important here so here is the result of some other diagnostic tests..

To clarify; I want my Internet to work properly. Whether it's wired or wireless. My wired should just be a plug and play sort of deal but it never manages to connect. My wireless is a WEP key, and I occasionally have the problem of it attempting to connect and every 30 seconds it will ask me for my encryption key again although it has already been entered. When wireless does connect, its far too slow. Please help!

"iwconfig"

```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"3L8P0"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:90:E5:27:EA   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/70  Signal level=-86 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2619  Invalid misc:5313   Missed beacon:0

eth0      no wireless extensions.

```


"ifconfig"

```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:e8:5e:67  
          inet6 addr: fe80::224:8cff:fee8:5e67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:198 (198.0 B)  TX bytes:209889 (209.8 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:337306 (337.3 KB)  TX bytes:337306 (337.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:64:a1:dc  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe64:a1dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50587052 (50.5 MB)  TX bytes:4903253 (4.9 MB)

```

---

### Post by WeasuhL on 2012-06-09
lshw -C network

```
 *-network               
       description: Wireless interface
       product: RT2790 Wireless 802.11n 1T/2R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:43:64:a1:dc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-23-generic firmware=0.34 ip=192.168.1.7 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:24:8c:e8:5e:67
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:fe9ff000-fe9fffff memory:fe9c0000-fe9dffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: memory:febf0000-febfffff memory:febe0000-febeffff

```

Some unclaimed issues perhaps?

---

### Post by sanderj on 2012-06-09
What is the result of:

```
wget ftp://ftp.xs4all.nl/pub/test/100mb.bin

```

Post full output here ...


And: when you boot a Ubuntu live-CD, with the ethernet cable plugged in your router, and Wifi not connected ... can you post ifconfig, and "mtr -n 8.8.8.8"

---

### Post by WeasuhL on 2012-06-09
Doing this in two different bits..i'm very afraid that when I disconnect my wifi I won't be able to connect up again. That's why this reply is so late, I lost connection when attempting to get my wired to work. I small update on that (and other things I've discovered);

Wireless:
Even if EVERYTHING is entered correctly, I cannot connect with wireless under any settings if I enter it in manually.

If my computer automatically detects my network I can enter the key and it will connect (occasionally) at a under 5 MB/S speed.

Wired:
Cannot connect via DHCP whatsoever. If I enter the information in manually, I can connect. Connection info shows 100 MB/S but I cannot resolve any domains nor ping anything. I've tried using my own DNS (my router) and google DNS, problem persists. I have a orange light on the back of my pc, which my manufacturer states should indicate sub-par speeds. (green fast, orange mid, red malfunctioning)

Any ideas on any of that?

Now, for your tests.

the ftp..

```

--2012-06-09 18:43:47--  ftp://ftp.xs4all.nl/pub/text/100mb.bin
           => `100mb.bin'
Resolving ftp.xs4all.nl (ftp.xs4all.nl)... 194.109.21.27
Connecting to ftp.xs4all.nl (ftp.xs4all.nl)|194.109.21.27|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/text ... 
No such directory `pub/text'.

```

Thankfully disabling/enabling my wireless didn't totally kick me off. :P

the ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:24:8c:e8:5e:67  
          inet6 addr: fe80::224:8cff:fee8:5e67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:173522 (173.5 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67925 (67.9 KB)  TX bytes:67925 (67.9 KB)

```

The other command you advised entered me into some sort of an editor My Traceroute V.0.8 or something, there was really nothing to copy and paste. What exactly were you looking for there...?

---

### Post by WeasuhL on 2012-06-09
The only way that my internet will currently work.

Detected wireless automatically, inputted key and connected.

Wired is disabled.

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:24:8c:e8:5e:67  
          inet6 addr: fe80::224:8cff:fee8:5e67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:356729 (356.7 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:302750 (302.7 KB)  TX bytes:302750 (302.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:64:a1:dc  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe64:a1dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:280715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:413164503 (413.1 MB)  TX bytes:15777129 (15.7 MB)

```

Noticed something that could be a hint to my problem..I'm not able to enter the command

"ifconfig eth0 up"

is that strange? I get a permissions error. Denied.

---

### Post by sanderj on 2012-06-09
Please read my post carefully. There are three commands. You did one correct, one incorrect and one not at all.

---

### Post by WeasuhL on 2012-06-09
> **sanderj said:**
> Please read my post carefully. There are three commands. You did one correct, one incorrect and one not at all.

Not sure why this didn't work before..

mtr

```

Ping Bit Pattern: ^[[B^[[B~Z~Z
Pattern Range: 0(0x00)-255(0xff), <0 random.
 Host                                Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. 192.168.1.1                       2.6%    39    1.8   3.4   1.1  24.6   4.0
 2. 173.64.99.1                       2.6%    39    7.0  13.2   5.3  84.3  13.9
 3. 130.81.185.232                    7.9%    39    9.4  12.7   7.1  69.6  10.8
 4. 130.81.199.4                      2.6%    39   11.1  19.0  10.7  90.9  16.6
 5. 152.63.3.69                       7.7%    39   19.4  24.3  14.8  90.0  17.2
    152.63.3.57
    152.63.3.249
 6. 152.63.1.218                      7.7%    39   44.2  30.9  18.7 107.4  22.2
    152.63.0.153
 7. 152.63.21.73                      2.6%    39   24.4  23.6  17.7  52.3   6.4
    152.63.22.45
    152.63.21.129
    152.63.18.206
    152.63.21.133
    152.63.16.125
    152.63.21.125
    152.63.21.65
 8. 152.179.72.66                     7.7%    39   28.6  25.9  18.6 120.1  16.6
 9. 72.14.232.244                     2.6%    38   26.0  26.2  20.1 114.6  15.6


```

which command did I do incorrectly?

---

### Post by WeasuhL on 2012-06-09
As for the wired connection: [http://askubuntu.com/questions/79346/how-can-i-install-the-realtek-rtl8111e-version-8168-driver](http://askubuntu.com/questions/79346/how-can-i-install-the-realtek-rtl8111e-version-8168-driver)

I believe that relates to me, doesn't it? I tried following tutorials on multiple sites but I can't get the driver correction to work..could that be the fix I need?

---

### Post by sanderj on 2012-06-09
wget [ftp://ftp.xs4all.nl/pub/test/100mb.bin](ftp://ftp.xs4all.nl/pub/test/100mb.bin)

(you changed 'test' to 'text')

---

### Post by WeasuhL on 2012-06-09
> **sanderj said:**
> wget [ftp://ftp.xs4all.nl/pub/test/100mb.bin](ftp://ftp.xs4all.nl/pub/test/100mb.bin)

(you changed 'test' to 'text')

Ah, nice catch. My apologies.

```

--2012-06-09 22:45:05--  ftp://ftp.xs4all.nl/pub/test/100mb.bin
           => `100mb.bin'
Resolving ftp.xs4all.nl (ftp.xs4all.nl)... 194.109.21.27
Connecting to ftp.xs4all.nl (ftp.xs4all.nl)|194.109.21.27|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/test ... done.
==> SIZE 100mb.bin ... 104857600
==> PASV ... done.    ==> RETR 100mb.bin ... done.
Length: 104857600 (100M) (unauthoritative)

 2% [                                       ] 2,409,472   43.4K/s  eta 56m 6s  

```

Did you need it to run through all the way for some reason or will that suffice? I can't even move around on my browser while that is downloading so..

---

### Post by sanderj on 2012-06-09
It would be better to keep the wget running, and press ENTER each few minutes. That way you can see the speeds at different moments.

In my post, I asked to run the tests with wireless disconnected and wired connected. I've the feeling this is done with wireless 'connceted', right? What do the same tests show via wired-only?

If so, what kind of connection have you got: DSL, Internet, fiber, 3G, ... ? You now get 50 kB/s which is the same as 500 kbps or 0.5 Mbps. That's the speed of a slow ADSL connection or a not-too fast 3G connection.

---

### Post by WeasuhL on 2012-06-09
> **sanderj said:**
> It would be better to keep the wget running, and press ENTER each few minutes. That way you can see the speeds at different moments.

In my post, I asked to run the tests with wireless disconnected and wired connected. I've the feeling this is done with wireless 'connceted', right? What do the same tests show via wired-only?

If so, what kind of connection have you got: DSL, Internet, fiber, 3G, ... ? You now get 50 kB/s which is the same as 500 kbps or 0.5 Mbps. That's the speed of a slow ADSL connection or a not-too fast 3G connection.

I have Verizon FioS (Fiber optics; in case you're from elsewhere)

I expected at least 15 MB/S. Under 1 is intolerable. I had an average of 20-25 with Windows Vista.

Will try the test with wired only in a moment, as I said though, when I hook up wired I can't resolve anything with my DNS or with google's public ones. So I'm guessing I'll get a destination host unreachable but we shall see..

---

### Post by WeasuhL on 2012-06-09
--2012-06-09 23:25:31--  [ftp://ftp.xs4all.nl/pub/test/100mb.bin](ftp://ftp.xs4all.nl/pub/test/100mb.bin)
           => `100mb.bin.1'
Resolving ftp.xs4all.nl (ftp.xs4all.nl)... failed: Name or service not known.
wget: unable to resolve host address `ftp.xs4all.nl'

---

### Post by sanderj on 2012-06-09
If it's a DNS problem (please post wget, ifconfig, mtr), as a second step use the wget as below.


```

sander@toverdoos:~$ wget ftp://194.109.21.27/pub/test/100mb.bin
--2012-06-10 05:29:59--  ftp://194.109.21.27/pub/test/100mb.bin
           => `100mb.bin.4'
Connecting to 194.109.21.27:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/test ... done.
==> SIZE 100mb.bin ... 104857600
==> PASV ... done.    ==> RETR 100mb.bin ... done.
Length: 104857600 (100M) (unauthoritative)

19% [======>                                ] 20,794,728  11.0M/s
53% [===================>                   ] 56,056,424  11.2M/s  eta 5s
84% [===============================>       ] 88,671,176  11.1M/s  eta 2s
100%[======================================>] 104,857,600 11.1M/s   in 9.0s

2012-06-10 05:30:08 (11.1 MB/s) - `100mb.bin.4' saved [104857600]

sander@toverdoos:~$

```

---

### Post by WeasuhL on 2012-06-09
> **sanderj said:**
> If it's a DNS problem (please post wget, ifconfig, mtr), as a second step use the wget as below.


```

sander@toverdoos:~$ wget ftp://194.109.21.27/pub/test/100mb.bin
--2012-06-10 05:29:59--  ftp://194.109.21.27/pub/test/100mb.bin
           => `100mb.bin.4'
Connecting to 194.109.21.27:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/test ... done.
==> SIZE 100mb.bin ... 104857600
==> PASV ... done.    ==> RETR 100mb.bin ... done.
Length: 104857600 (100M) (unauthoritative)

19% [======>                                ] 20,794,728  11.0M/s
53% [===================>                   ] 56,056,424  11.2M/s  eta 5s
84% [===============================>       ] 88,671,176  11.1M/s  eta 2s
100%[======================================>] 104,857,600 11.1M/s   in 9.0s

2012-06-10 05:30:08 (11.1 MB/s) - `100mb.bin.4' saved [104857600]

sander@toverdoos:~$

```

Are you no longer attempting to troubleshoot my wireless at this point?

If these commands were directed at my wired..

```

cody@cody-CM5570:~$ wget ftp://194.109.21.27/pub/test/100mb.bin
--2012-06-09 23:45:56--  ftp://194.109.21.27/pub/test/100mb.bin
           => `100mb.bin.2'
Connecting to 194.109.21.27:21... failed: No route to host.
cody@cody-CM5570:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:e8:5e:67  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fee8:5e67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:421468 (421.4 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18511438 (18.5 MB)  TX bytes:18511438 (18.5 MB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:64:a1:dc  
          inet6 addr: fe80::222:43ff:fe64:a1dc/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1716311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1331391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1909084222 (1.9 GB)  TX bytes:238503653 (238.5 MB)

```

the mtr command hangs with no data whatsoever.

---

### Post by sanderj on 2012-06-10
```
cody@cody-CM5570:~$ wget ftp://194.109.21.27/pub/test/100mb.bin
--2012-06-09 23:45:56--  ftp://194.109.21.27/pub/test/100mb.bin
           => `100mb.bin.2'
Connecting to 194.109.21.27:21... failed: No route to host.
cody@cody-CM5570:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:e8:5e:67  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0

```

So you have an IP address (good), but no route? What's the output of "ip route show"?

EDIT: you're connected to your router, right? Not to your fiber modem?

---

### Post by WeasuhL on 2012-06-10
default via 192.168.1.1 dev wlan0  proto static 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.7  metric 2 


Yes I am. I've tried connecting straight to the modem  and to the router..it still doesn't work. This is all with wireless internet.

---

### Post by WeasuhL on 2012-06-10
Someone please help me. My wireless speed is less than 1 MB/S and my wired Internet says destination host unreachable for EVERYTHING.

---

### Post by sanderj on 2012-06-10
> **WeasuhL said:**
> default via 192.168.1.1 dev wlan0  proto static 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.7  metric 2 


Yes I am. I've tried connecting straight to the modem  and to the router..it still doesn't work. This is all with wireless internet.

I don't understand this: your route table only shows routes for wlan0, not for eth0, but your WLAN is disconnected and your ETH connected?

Last try: Boot a Ubuntu live-CD, with ethernet connected, WLAN switched off (or WLAN password not filled out), then what's the output of:
- the wget command
- the route command
- the ifconfig command
- the mtr command

---

