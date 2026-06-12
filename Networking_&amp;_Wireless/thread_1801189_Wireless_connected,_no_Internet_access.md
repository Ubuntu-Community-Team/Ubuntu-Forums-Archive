---
title: "Wireless connected, no Internet access"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by Fibonacci on 2011-07-10
Hello.

I've got a Broadcom 4311 wireless card on my laptop, which has almost always worked with Ubuntu &#8211; that is, except for a [brief while after upgrading to Natty]("http://ubuntuforums.org/showthread.php?t=1786705").
Yesterday I noticed, even though I could connect to my wireless network as usual, I just cannot access the Internet. I cannot even ping my own router:
```
ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms
```

Pinging from somewhere else in the network to my laptop gets the same results.

I'm pretty sure it's not a hardware issue, either on the router or on my laptop, because under Windows I can (and do) access the Internet without a single problem on this regard. Also, the router reports my laptop as the only device connected to the wireless network; the only other device on the whole network is my desktop PC from which I'm posting.

I've tried booting an old kernel (Maverick-old), but I still get the same problem there.

Here's some apparently relevant output from dmesg:

```
[   19.858944] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.319555] slamr: module license 'Smart Link Ltd.' taints kernel.
[   20.319560] Disabling lock debugging due to kernel taint
[   20.335507] slamr: SmartLink AMRMO modem.
[   20.870603] [drm] Setting GART location based on new memory map
[   20.873109] [drm] Loading R500 Microcode
[   20.876410] [drm] Num pipes: 1
[   20.876419] [drm] writeback test succeeded in 1 usecs
[   21.907105] psmouse serio5: ID: 10 00 64
[   24.188390] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   24.753438] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input9
[   81.584567] wlan0: authenticate with 34:08:04:0d:77:14 (try 1)
[   81.592209] wlan0: authenticated
[   81.592623] wlan0: associate with 34:08:04:0d:77:14 (try 1)
[   81.618744] wlan0: RX AssocResp from 34:08:04:0d:77:14 (capab=0x411 status=0 aid=1)
[   81.618749] wlan0: associated
[   81.619473] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   81.619533] cfg80211: Calling CRDA for country: US
[   81.625929] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   81.625933] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625935] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   81.625938] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625941] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   81.625943] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625946] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   81.625948] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625951] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   81.625953] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625956] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   81.625958] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625960] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   81.625963] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625965] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   81.625968] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625970] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   81.625973] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625975] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   81.625978] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625980] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   81.625983] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625985] cfg80211: Disabling freq 2467 MHz
[   81.625987] cfg80211: Disabling freq 2472 MHz
[   81.625988] cfg80211: Disabling freq 2484 MHz
[   81.625991] cfg80211: Regulatory domain changed to country: US
[   81.625992] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   81.625995] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   81.625998] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   81.626000] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   81.626003] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   81.626005] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   81.626008] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   82.207916] Intel AES-NI instructions are not detected.
[   82.291984] padlock_aes: VIA PadLock not detected.
[   92.400040] wlan0: no IPv6 routers present
```

What else can I do?

---

### Post by westie457 on 2011-07-10
> **Fibonacci said:**
> Hello.

I've got a Broadcom 4311 wireless card on my laptop, which has almost always worked with Ubuntu – that is, except for a [brief while after upgrading to Natty]("http://ubuntuforums.org/showthread.php?t=1786705").
Yesterday I noticed, even though I could connect to my wireless network as usual, I just cannot access the Internet. I cannot even ping my own router:
```
ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms
```

Pinging from somewhere else in the network to my laptop gets the same results.

I'm pretty sure it's not a hardware issue, either on the router or on my laptop, because under Windows I can (and do) access the Internet without a single problem on this regard. Also, the router reports my laptop as the only device connected to the wireless network; the only other device on the whole network is my desktop PC from which I'm posting.

I've tried booting an old kernel (Maverick-old), but I still get the same problem there.

Here's some apparently relevant output from dmesg:

```
[   19.858944] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.319555] slamr: module license 'Smart Link Ltd.' taints kernel.
[   20.319560] Disabling lock debugging due to kernel taint
[   20.335507] slamr: SmartLink AMRMO modem.
[   20.870603] [drm] Setting GART location based on new memory map
[   20.873109] [drm] Loading R500 Microcode
[   20.876410] [drm] Num pipes: 1
[   20.876419] [drm] writeback test succeeded in 1 usecs
[   21.907105] psmouse serio5: ID: 10 00 64
[   24.188390] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   24.753438] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input9
[   81.584567] wlan0: authenticate with 34:08:04:0d:77:14 (try 1)
[   81.592209] wlan0: authenticated
[   81.592623] wlan0: associate with 34:08:04:0d:77:14 (try 1)
[   81.618744] wlan0: RX AssocResp from 34:08:04:0d:77:14 (capab=0x411 status=0 aid=1)
[   81.618749] wlan0: associated
[   81.619473] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   81.619533] cfg80211: Calling CRDA for country: US
[   81.625929] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   81.625933] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625935] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   81.625938] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625941] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   81.625943] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625946] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   81.625948] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625951] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   81.625953] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625956] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   81.625958] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625960] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   81.625963] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625965] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   81.625968] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625970] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   81.625973] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625975] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   81.625978] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625980] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   81.625983] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   81.625985] cfg80211: Disabling freq 2467 MHz
[   81.625987] cfg80211: Disabling freq 2472 MHz
[   81.625988] cfg80211: Disabling freq 2484 MHz
[   81.625991] cfg80211: Regulatory domain changed to country: US
[   81.625992] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   81.625995] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   81.625998] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   81.626000] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   81.626003] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   81.626005] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   81.626008] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   82.207916] Intel AES-NI instructions are not detected.
[   82.291984] padlock_aes: VIA PadLock not detected.
[   92.400040] wlan0: no IPv6 routers present
```

What else can I do?

Try doing what I did. The info is here [http://ubuntuforums.org/showpost.php?p=10764974&postcount=188](http://ubuntuforums.org/showpost.php?p=10764974&postcount=188)

---

### Post by Fibonacci on 2011-07-10
> **westie457 said:**
> Try doing what I did. The info is here [http://ubuntuforums.org/showpost.php?p=10764974&postcount=188](http://ubuntuforums.org/showpost.php?p=10764974&postcount=188)

I already did this, which includes your steps: [http://ubuntuforums.org/showthread.php?t=1786705](http://ubuntuforums.org/showthread.php?t=1786705)

---

### Post by westie457 on 2011-07-10
What are the results of ```
iwconfig
```
and if you plug a cable in ```
ifconfig
```

with a cable attached can you ping your router?

The link below is something I found that may or may not be the answer

[http://ubuntuforums.org/archive/index.php/t-353589.html](http://ubuntuforums.org/archive/index.php/t-353589.html)

The last post made me laugh (just my sense of humour)

---

### Post by Fibonacci on 2011-07-10
> **westie457 said:**
> What are the results of ```
iwconfig
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"A*******"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 34:08:04:0D:77:14   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

> **westie457 said:**
> and if you plug a cable in ```
ifconfig
```

```
eth0      Link encap:Ethernet  HWaddr 00:16:d4:9b:c8:66  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe9b:c866/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:488010 (488.0 KB)  TX bytes:38640 (38.6 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35400 (35.4 KB)  TX bytes:35400 (35.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:54:09:9b  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe54:99b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:186940 (186.9 KB)  TX bytes:280622 (280.6 KB)
```

> **westie457 said:**
> with a cable attached can you ping your router?

Yes I can.

> **westie457 said:**
> The link below is something I found that may or may not be the answer

[http://ubuntuforums.org/archive/index.php/t-353589.html](http://ubuntuforums.org/archive/index.php/t-353589.html)

The last post made me laugh (just my sense of humour)

MAC filtering is OFF according to the router.

---

### Post by westie457 on 2011-07-10
This has got me stumped. Apart from some minor differences in the output nothing stands out to be causing the problem. I have attached the output from my box to show you. The first running of ifconfig was my bad (forgot to plug the cable in)```
graham@graham-Aspire-3690:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"dlink"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:26:5A:2A:CE:1E   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

graham@graham-Aspire-3690:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:e4:75:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3168 (3.1 KB)  TX bytes:3168 (3.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:9f:c3:f0  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe9f:c3f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45333173 (45.3 MB)  TX bytes:5044008 (5.0 MB)

graham@graham-Aspire-3690:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:e4:75:dd  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fee4:75dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25837 (25.8 KB)  TX bytes:24449 (24.4 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3168 (3.1 KB)  TX bytes:3168 (3.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:9f:c3:f0  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe9f:c3f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45357746 (45.3 MB)  TX bytes:5053497 (5.0 MB)
```
What is the output of ```
route
```
It should look something like this```
graham@graham-Aspire-3690:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         dir-615         0.0.0.0         UG    0      0        0 eth0

```

---

### Post by westie457 on 2011-07-10
Another old thread that may or may not throw some light around.

[http://ubuntuforums.org/archive/index.php/t-1001532.html](http://ubuntuforums.org/archive/index.php/t-1001532.html)

No laughing this time.

---

### Post by Fibonacci on 2011-07-10
> **westie457 said:**
> What is the output of ```
route
```
It should look something like this```
graham@graham-Aspire-3690:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         dir-615         0.0.0.0         UG    0      0        0 eth0

```

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

> **westie457 said:**
> Another old thread that may or may not throw some light around.

[http://ubuntuforums.org/archive/index.php/t-1001532.html](http://ubuntuforums.org/archive/index.php/t-1001532.html)

No laughing this time.

Well, I can at least ping my router when switching to WEP. That at least gives me some hope.
Sadly there is no way to force WPA or WPA2 on a DIR-600 (that I know of).

---

### Post by westie457 on 2011-07-10
> Well, I can at least ping my router when switching to WEP. That at least gives me some hope.
Sadly there is no way to force WPA or WPA2 on a DIR-600 (that I know of)
Does this mean you can reach the internet now?

if not try this> Hi I had a similar problem a while ago with the router not accepting the WPA password. The work around I did was to connect a cable to enable me to access the home page of the router and reset it to factory default.

Then instead of doing an automatic set-up I did a manual one removing all security to get a working connection then I went through the pages of the router and set up 'MAC Address Filtering' only allowing access to my dual-booting pc's. Finally I changed the log in details from the default settings to stop others from piggy-backing off my connection. Have been using it that way for a year now.

PS I have tried a couple of times to use it with a password and one OS still refuses to accept it.

Hope this is helpful to you.

I know it is for a different issue however resetting the router to factory defaults usually works.

---

### Post by Fibonacci on 2011-07-24
> **westie457 said:**
> Does this mean you can reach the internet now?

Yes, but not for much.

After extensive testing, I've concluded that my wireless card supports WPA only half of the time. On Natty that is - I've never experienced any problems with it before Natty.
So I switch the router to WEP, I can reach the internet fine, then I switch it back to WPA and the problem is (temporarily) solved. But, if I e.g. have to reset the router, I'm once again locked out of the internet.

I don't like that kind of hacks, but it seems it's the only solution here.

---

