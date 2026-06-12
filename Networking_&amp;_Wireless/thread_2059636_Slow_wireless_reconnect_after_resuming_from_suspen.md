---
title: "Slow wireless reconnect after resuming from suspend [12.04]"
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by frankadelic on 2012-09-18
I am running Ubuntu 12.04 on a Dell Inspiron 1420.

When resuming from sleep/suspend, it takes ~30 seconds for my preferred wireless connection to reconnect. It used to reconnect almost immediately after wakeup.

Please note: during the 30 seconds it takes to reconnect, the wireless icon in the top menubar is an empty quarter-circle. There are no wavy lines indicating that it is even trying to connect. What is it waiting for?

I read somewhere that using a different window manager might help -- so I installed gnome-session-fallback (Gnome Classic). To my great happiness, it worked! Again, I had a wireless connection almost immediately after resuming.
However, after a day or two, Gnome Classic began having the delay also. No idea what changed.

---

### Post by irv on 2012-09-18
When it starts to slow, open a terminal and run the command:
```
top
```
This will show you how much memory you are using and also how much swap is used. It also tells you what is running and what is using most memory. It is a nice utility. It will give you an idea on what is going on.

---

### Post by frankadelic on 2012-09-18
Additional info about the problem:
If the laptop was asleep for less than 60 seconds when it's woken up, the wireless connection remains active. So, to replicate the issue, the machine needs to be suspended for at least a minute.

After wakeup/login, top shows these processes (among others) for root:
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                    
 2258 root      20   0 75220  25m 7492 S    6  0.8  33:02.06 Xorg                                                                       
 1478 root      20   0 28484 4052 3192 S    1  0.1   0:06.99 upowerd                                                                    
    3 root      20   0     0    0    0 S    0  0.0   2:10.95 ksoftirqd/0                                                                
  818 root      20   0  7204 2796 2204 S    0  0.1   0:00.42 modem-manager                                                                    
  911 root      20   0 27576 4680 2912 S    0  0.2   0:40.14 polkitd                                                                    

```

These processes remain for at least 15 seconds, and then something kicks in and additional processes appear.

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                      
 2258 root      20   0 72584  25m 7492 S    3  0.9  33:11.73 Xorg                                         
  987 root      20   0  5940 2172 1784 S    1  0.1   0:06.24 wpa_supplicant                               
 1044 root      20   0     0    0    0 S    0  0.0   0:00.03 kworker/1:1                                  
29400 root      20   0     0    0    0 S    0  0.0   0:01.54 kworker/0:1                                  
    1 root      20   0  3648 2084 1352 S    0  0.1   0:01.85 init                                         
    2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                     
    3 root      20   0     0    0    0 S    0  0.0   2:11.23 ksoftirqd/0     

```

Also:                                                                                                    
```
  903 root      20   0 31260 5476 4284 S    3  0.2   0:22.76 NetworkManager     
```


At this point in time, I can see the network icon in the menubar show that a connection is being made. I get the onscreen popup almost immediately thereafter that my preferred wireless connection has been restored.

My uneducated guess is that "wpa_supplicant" or "NetworkManager" are the processes which initiate the reconnect. It seems they do not start immediately when the laptop has been asleep for more than 60 seconds, and (apparently) a certain timeout period must pass before they are started.

Any ideas how I can fix this?

---

### Post by irv on 2012-09-18
I have a question on askubuntu on how to suspend without shutting down the network manager.
[http://askubuntu.com/questions/190340/is-there-a-way-to-suspend-12-04-without-turning-off-network]("http://askubuntu.com/questions/190340/is-there-a-way-to-suspend-12-04-without-turning-off-network")
Of course this will use some battery if you are unplugged.

---

### Post by frankadelic on 2012-09-18
My issue appears to be this bug:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405)

I followed the workaround in this comment (74) and it appears to fix the problem. The preferred network connection is refreshed on resume:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405/comments/74](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405/comments/74)

BTW, elsewhere I've read comments which suggested to install wicd -- have not tried that, but it may work for some.

---

### Post by irv on 2012-09-19
I copied comment 74 here so you can mark the thread solved.
[ATTACH]224370[/ATTACH]
> 

most solutions failed here, however:

changing the last part in /usr/lib/pm-utils/sleep.d/55NetworkManager

from
  thaw|resume)¶
     resume_nm¶

to
  thaw|resume)¶
    resume_nm¶
    sleep 2 && iwlist eth1 scanning &

forces a wifi scan and network manager connects almost immediately after resume.


---

### Post by frankadelic on 2012-09-19
> **irv said:**
> I copied comment 74 here so you can mark the thread solved.

I spoke too soon... this doesn't always work either. Trying wicd next...

---

### Post by hitime on 2012-09-19
Have you looked to see if your network adapter is in power saving mode?  iwconfig can show you some info and /etc/network/interfaces can be modified to turn it off, search the forums.....

---

### Post by frankadelic on 2012-09-20
> **hitime said:**
> Have you looked to see if your network adapter is in power saving mode? 

I tried disabling power saving mode as described in this post:

[http://ubuntuforums.org/showpost.php?p=10453079&postcount=2](http://ubuntuforums.org/showpost.php?p=10453079&postcount=2)

Not clear if it helped or not. Sometimes wireless connects immediately in resume, other times it takes > 15 seconds.

Also, I am skeptical that my change above had any effect. I get this result when running it manually:


```
$ iwlist scan
eth3      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```

---

### Post by irv on 2012-09-20
I thought I would give 
```
iwlist scan
```
a try and this was my output:
> scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:96:62:70
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:off
                    ESSID:"Acoustic Cafe Customer WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c5cbfa997
                    Extra: Last beacon: 864ms ago
                    IE: Unknown: 001B41636F7573746963204361666520437573746F6D65722057694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6C1803FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000300000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C1803FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000300000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


---

### Post by frankadelic on 2012-09-20
Maybe you have a different wireless card?

My output from lspci -v:

```
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Wireless 1395 WLAN Mini-Card
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb


```

---

### Post by irv on 2012-09-20
> **frankadelic said:**
> Maybe you have a different wireless card?

My output from lspci -v:

```
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Wireless 1395 WLAN Mini-Card
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb


```

We can't compare apples with apples because you have a BCM4312 where I have a BCM4311 which is different. And your Wireless card is a 1395 WLAN while mine is a 1390 WLAN card. I also have to use a different driver. b43 and not the wl. It would be great to get someone out here with the same hardware.
> 0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb


---

### Post by frankadelic on 2012-09-24
BTW, I tried wicd. It did not work -- not only did wireless not reconnect on resume, the connection was dropped periodically. I reverted to network-manager.

---

