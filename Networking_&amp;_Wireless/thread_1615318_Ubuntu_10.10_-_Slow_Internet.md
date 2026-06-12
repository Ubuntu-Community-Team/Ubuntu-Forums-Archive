---
title: "Ubuntu 10.10 - Slow Internet"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by DanPaulCiocan on 2010-11-06
Hi, my internet speed is slow on Ubuntu 10.10. On both wireless connection and Ethernet connection I get 120 kb/s. With Ubuntu 10.04 and Windows I get 850 kb/s.

I tried to disable ipv6 but i doesn't change anything. Please tell me what can I do to find the problem? Thanks.

---

### Post by voodoo_doctor on 2010-11-07
Same problem here. Any ideas why?

---

### Post by DanPaulCiocan on 2010-11-07
I forgot to tell that I use the 64 bit version, and here is my lspci and ifconfig:
```
danpaul@danpaul-msi:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
danpaul@danpaul-msi:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:16:15:6d  
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:2745 errors:53 dropped:0 overruns:0 frame:53
          TX packets:2318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3240941 (3.2 MB)  TX bytes:505878 (505.8 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2748 (2.7 KB)  TX bytes:2748 (2.7 KB)

ra0       Link encap:Ethernet  HWaddr 00:24:21:cd:54:e3  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97692040 (97.6 MB)  TX bytes:8234217 (8.2 MB)
          Interrupt:16 

danpaul@danpaul-msi:~$ 

```Please help us.

EDIT: Also, here is route -n:
```
danpaul@danpaul-msi:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 ra0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ra0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ra0

```

---

### Post by wiseguy12851 on 2010-11-09
Hey,

I'm only an intermediate Ubuntu user but I had the same problem, everything was ridiculously slow. I finally did 2 things:


[LIST]
[*]Disable IPv6
[*]Disable IPv4 via Automatic DHCP, I assigned it a manual IP address, now it works faster than my other computer.
[/LIST]
I can't confirm this but I think Ubuntu is getting hung up on the DNS servers because Mozilla says it's "Looking up ..." for like 5 minutes before it actually starts to download the web page & process it.

I don't know your expertise level so excuse me if you already know this but setting a manual IP is very easy to do if you don't know how and it will solve many problems like this - it's always best to cut down on anything dynamic if possible

EDIT:
If you are using the desktop version of ubuntu or kubuntu then assign the manual ip through System > Preferences > Network Connections, ubuntu seems to not like editing it through the file like some tutorials will explain

---

### Post by DanPaulCiocan on 2010-11-09
Thanks for your answer, but I don't think we have the same problem because I don't see the "Looking up ..." in Mozilla. In fact, it starts to load the page very quickly, but it takes to much time to load it. And if I download a file, the pages don't load at all.

Also, I used the manual IP address assignment and my IPv6 is disabled.

I have no clue about what can this problem be. It can't be related with my drivers because I have the same problem both on Ethernet and wireless and it can't be the router because it works well on my other computers.

Again, thank you very much because you tried to help me.

Maybe this is related to MTU, because sometimes I have MTU problem on Ethernet? How can I know if it MTU?

---

### Post by wiseguy12851 on 2010-11-09
It actually could be related to your drivers, or Ubuntu itself, if I read correctly you had Ubuntu 64-bit. Although I haven't used Ubuntu 64-bit in a while the last time I used it a lot of things didn't work correctly that normally would on Ubuntu 32-bit - as a result I'm waiting until they work out all the glitches.

If you have some spare time you might want to try out the 32-bit live CD and see if there's any improvement. I just remember a lot of bizarre errors/glitches on the 64-bit version and networking was definitely one of them...

Hope this helps

---

### Post by rudi246 on 2010-11-12
I've been having this same problem. I was wondering if installing the windows drivers with ndiswrapper would help?

EDIT: Also, if I have to install the 32 bit you said there won't be any issues, so it should not delete any of my files or programs? Will it reset my settings such as themes and such? I'm just wondering what I would need to back up if it came down to this.

---

### Post by dineshs on 2010-11-12
> Maybe this is related to MTU, because sometimes I have MTU problem on Ethernet? How can I know if it MTU?Try
[http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346)
Also see if [this]("http://ubuntuforums.org/showthread.php?t=1619527") helps

---

### Post by krizanand on 2010-11-12
I've the same problem as well, connection is very slow and page loading times are worse compared to Lucid 10.04. I think there is some problem with the network manager in10.10. In addition to that the system freezes momentarily, it just now did while I was typing this, then by just moving the trackpad it works, at times even the trackpad doesn't work and the cursor isn't moving, hitting Alt-Tab makes it active again. These are just nagging issues but nothing serious going on. Hope they iron out all these annoyances in the future updates. 

Rest all works fine as usual..........

---

### Post by wiseguy12851 on 2010-11-12
In response to rudi246:

> Also, if I have to install the 32 bit you said there won't be any  issues, so it should not delete any of my files or programs? Will it  reset my settings such as themes and such? I'm just wondering what I  would need to back up if it came down to this.     I still suggest the live 32-bit CD, however, I suggested live CD because you don't need to install anything, Live CD boots Ubuntu into the RAM without installing anything on your Hard Drive and is meant for testing it out before actually installing it.

If Ubuntu is any faster or more stable in the 32-bit version then you can install it, currently you have the 64-bit version which means there will be major redecorating in your current system if you do decide to make a conversion over to 32-bit, as a strong precaution I would backup anything needing backup before conversion.

That's why the Live CD comes to the rescue and allows you fully start Ubuntu completely in your RAM, I would suggest using it on your next spare time for about 10 minutes to see if you like it better, I certainly did, if you don't simply power off Ubuntu & remove the CD and you'll discover nothings changed.

---

### Post by TBABill on 2010-11-12
My Ralink is a different model and I could not connect at all, however I wonder if the fix will be similar to mine here [http://ubuntuforums.org/showthread.php?t=1617290](http://ubuntuforums.org/showthread.php?t=1617290). I am NOT suggesting you do the same to fix yours, but rather wondering if it is possible you have a conflict in /etc/modprobe.d/blacklist.conf? There were many posts regarding various Ralink wireless devices either not connecting or performing very poorly and it looks like a kernel regression since 10.04. My Ralink worked flawlessly in 10.04 and wouldn't work at all in 10.10. Fixed now by the link above, but a pain to find out how to do it.
 
Just a suggestion since the problem listed doesn't really point to anything specific since it's just slow speeds.

---

### Post by rudi246 on 2010-11-12
I'm going to try a few of these methods starting with the manual ip address, but how do I get the ip address I need? Also, I need the subnet mask and local gateway.

Does anyone have any thoughts on using the windows driver with ndiswrapper? If it's a driver issue I want to try that as soon as I can get my driver. The driver is included in the chipset drivers I downloaded from HP which is an exe file, so now I need to try to get the sys file out of it.

EDIT: I was able to find my driver in a folder on my computer and I found out it is Ralink so I will try TBABill's link. I may also pop in the 32 bit live cd and see if the internet will go any faster.

I really hope we can figure this out. I have been using Ubuntu a lot more than Vista lately but it's kinda hard when my internet is slow as hell!

---

### Post by rudi246 on 2010-11-13
So I tried running the live cd for the 32 bit version and the internet is still really slow so I am assuming it's a driver issue. I'm going to try using ndiswrapper.

---

### Post by The_Doctor04 on 2010-11-27
I too am having the same problems after upgrading from Lucid with my wired connection.  Everything was great until I installed version 10.10.  I have disabled ipv6 in both Firefox and Ubuntu.  I have manually set my IP, DNS, etc, etc.  I have been digging over this forum & other sites for the past 24 hours with no luck.  I am very tempted at this point to just re-install Lucid as I had zero issues before upgrading.  XP is even running my Internet faster which is very disappointing.  Help :(

---

### Post by casaben on 2010-11-29
I was struggling with this myself, until I found out it was related to the power manager.
Every time on battery power, the wireless performance would drop to almost nothing.
Then, I tried : 
**sudo iwconfig eth1 power off **
where eth1 is the wireless adapter.

You have to do this **after** you unplugged your laptop from the AC power (so when you start running on battery). If you run it while still on AC, and then unplug, it will not work.

Hope this helps someone

---

### Post by hnasiet on 2010-11-29
I have the same problem, when I do the speedtest it gives me ~7 Mb/s on ubuntu 10.10 64-bit but on windows it gives me ~20 Mb/s. I'm on a desktop

> **The_Doctor04 said:**
> I too am having the same problems after upgrading from Lucid with my wired connection.  Everything was great until I installed version 10.10.  I have disabled ipv6 in both Firefox and Ubuntu.  I have manually set my IP, DNS, etc, etc.  I have been digging over this forum & other sites for the past 24 hours with no luck.  I am very tempted at this point to just re-install Lucid as I had zero issues before upgrading.  XP is even running my Internet faster which is very disappointing.  Help :(
just like me

---

### Post by nbren12 on 2010-11-29
> **casaben said:**
> I was struggling with this myself, until I found out it was related to the power manager.
Every time on battery power, the wireless performance would drop to almost nothing.
Then, I tried : 
**sudo iwconfig eth1 power off **
where eth1 is the wireless adapter.

You have to do this **after** you unplugged your laptop from the AC power (so when you start running on battery). If you run it while still on AC, and then unplug, it will not work.

Hope this helps someone

Wow, I tried this and it showed a big improvement. My internet has been extremely sluggish as well. I'd say this is a solid fix. Thanks!

---

### Post by xarxiusxiii on 2010-12-03
> **casaben said:**
> I was struggling with this myself, until I found out it was related to the power manager.
Every time on battery power, the wireless performance would drop to almost nothing.
Then, I tried : 
**sudo iwconfig eth1 power off **
where eth1 is the wireless adapter.

You have to do this **after** you unplugged your laptop from the AC power (so when you start running on battery). If you run it while still on AC, and then unplug, it will not work.

Hope this helps someone

That did help, however, it did not stay like that after each reboot, and (call me lazy) but I don't like having to run commands each time I reboot. I just disabled wireless power management completely by putting a blank file called "wireless" in /etc/pm/power.d and made sure that it wasn't executable.

I read up about that here: [LINK]("https://help.ubuntu.com/community/PowerManagement/ReducedPower").

I don't know if this will have the same effect on other people's laptops though, so don't blame me if you mess something up ;)

---

### Post by hnasiet on 2010-12-03
and what about wired connection?

---

### Post by t1010011 on 2010-12-07
OMG!

My Internet speed just went from 240B/s (yes, Bytes!) to just around 120 KB/s the normal speed of my connection!

By the way I'm on a pc... so no batteries at all...

Thanks!

---

### Post by buffalobillion on 2010-12-08
Wow, that fixed it for me--night and day difference. Thanks!

Any chance this gets fixed permanently?

---

### Post by togume on 2010-12-12
Thanks for the answer. This made a huge difference in my connection quality.

I ran some tests with the wireless power management on and off, and the difference was ridiculous.

With **sudo iwconfig eth1 on** (default, which causes the problem):
```
togume@togume-laptop:~$ ping google.com
PING google.com (74.125.95.106) 56(84) bytes of data.
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=1 ttl=53 time=102 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=2 ttl=53 time=125 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=3 ttl=53 time=47.1 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=4 ttl=53 time=72.8 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=5 ttl=53 time=90.9 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=6 ttl=53 time=113 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=7 ttl=53 time=243 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=8 ttl=53 time=874 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=9 ttl=53 time=919 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=10 ttl=53 time=824 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=11 ttl=53 time=104 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=12 ttl=53 time=127 ms
^C
--- google.com ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 12981ms
rtt min/avg/max/mdev = 47.184/303.935/919.544/332.001 ms

```

With **sudo iwconfig eth1 off** (default, which causes the problem):
```
togume@togume-laptop:~$ ping google.com
PING google.com (74.125.95.105) 56(84) bytes of data.
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=1 ttl=53 time=32.8 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=2 ttl=53 time=30.1 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=3 ttl=53 time=31.4 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=4 ttl=53 time=33.3 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=5 ttl=53 time=89.9 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=6 ttl=53 time=37.1 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=7 ttl=53 time=208 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=8 ttl=53 time=201 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=9 ttl=53 time=167 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=10 ttl=53 time=154 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=11 ttl=53 time=144 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=12 ttl=53 time=57.1 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=13 ttl=53 time=36.1 ms
^C
--- google.com ping statistics ---
13 packets transmitted, 13 received, 0% packet loss, time 12016ms
rtt min/avg/max/mdev = 30.138/94.199/208.725/67.716 ms
```

I did a quick search on to how to permanently disable this behavior, and came up with [this page]("http://uselessuseofcat.com/?p=67").

Basically, the solution is to create a file called **wireless** in the **/etc/pm/power.d/** directory. This file overrides the behavior of the /usr/lib/pm-utils/power.d/wireless script which causes the problem. To make sure that the wireless power management is disabled, enter the following in the newly created wireless script:

**/etc/pm/power.d/wireless**
```
#!/bin/sh

/sbin/iwconfig eth1 power off
```

Problem should be solved. However, this needs to be addressed in a formal way... Did anyone submit a bug request?

---

### Post by marranzano on 2010-12-13
this also permanently solved the problem on my HP tx2510us

sudo gedit /usr/lib/pm-utils/power.d/wireless
(make a copy before doing these changes)

apply these changes in the script:

```
case $driver in
        ipw2100) iwpriv_ac="set_power 0"
            iwpriv_batt="set_power 0"
            iwconfig_ac="power on"
            iwconfig_batt="power on";;
        ipw3945)
            iwpriv_ac="set_power 6"
            iwpriv_batt="set_power 6";;
        iwl*) if [ -f "/sys/class/net/$1/device/power_level" ]; then
                 iwlevel_ac=0
                 iwlevel_batt=0
              else
                 iwconfig_ac="power off"
                 iwconfig_batt="power off"
              fi;;
        *) iwconfig_ac="power off"
           iwconfig_batt="power off";;
    esac
```

credits to post #9 in [this thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651008")

---

### Post by wackyraces on 2010-12-13
I experienced slow web browsing on my laptop, using both wired and wireless connections. I'm using 64 bit Ubuntu 10.10. After following this tip, web browsing is back to normal again.

[http://usingnix.wordpress.com/2010/10/17/ubuntu-10-10-slow-internet/](http://usingnix.wordpress.com/2010/10/17/ubuntu-10-10-slow-internet/)

The tip involves disabling IPv6 when the machine boots, by adding a switch in GRUB. Disabling IPv6 this using the /etc/sysctl.conf method did not work for me.

I did, however, also apply these tweaks to /etc/sysctl.conf but on their own they did not work. I'm not sure if they have made any difference, or if you need to do both of these things in combination to get the speed increase.

## increase TCP max buffer size setable using setsockopt()
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
 ## increase Linux autotuning TCP buffer limits
 ## min, default, and max number of bytes to use
 ## set max to at least 4MB, or higher if you use very high BDP paths
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
 ## don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
 ## recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
 ## for 10 GigE, use this, uncomment below
 ## net.core.netdev_max_backlog = 30000
 ## Turn off timestamps if you're on a gigabit or very busy network
 ## Having it off is one less thing the IP stack needs to work on
 ## net.ipv4.tcp_timestamps = 0
 ## disable tcp selective acknowledgements.
net.ipv4.tcp_sack = 0
 ##enable window scaling
net.ipv4.tcp_window_scaling = 1

---

### Post by wackyraces on 2010-12-15
> **wackyraces said:**
> I experienced slow web browsing on my laptop, using both wired and wireless connections. I'm using 64 bit Ubuntu 10.10. After following this tip, web browsing is back to normal again.

[http://usingnix.wordpress.com/2010/10/17/ubuntu-10-10-slow-internet/](http://usingnix.wordpress.com/2010/10/17/ubuntu-10-10-slow-internet/)

The tip involves disabling IPv6 when the machine boots, by adding a switch in GRUB. Disabling IPv6 this using the /etc/sysctl.conf method did not work for me.

I did, however, also apply these tweaks to /etc/sysctl.conf but on their own they did not work. I'm not sure if they have made any difference, or if you need to do both of these things in combination to get the speed increase.

## increase TCP max buffer size setable using setsockopt()
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
 ## increase Linux autotuning TCP buffer limits
 ## min, default, and max number of bytes to use
 ## set max to at least 4MB, or higher if you use very high BDP paths
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
 ## don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
 ## recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
 ## for 10 GigE, use this, uncomment below
 ## net.core.netdev_max_backlog = 30000
 ## Turn off timestamps if you're on a gigabit or very busy network
 ## Having it off is one less thing the IP stack needs to work on
 ## net.ipv4.tcp_timestamps = 0
 ## disable tcp selective acknowledgements.
net.ipv4.tcp_sack = 0
 ##enable window scaling
net.ipv4.tcp_window_scaling = 1

Update:

I've now installed Ubuntu 10.10 32 bit, as I had problems with playback on the 64 bit version with Iplayer (even with the latest 64 bit flash plugin installed). 32 bit works better. However, I was still experiencing dropped packets on my wireless connection (plugged in or not). I've tracked the problem down to the Atheros AR9285 driver (Ath9k), which seems to have an issue with dropped connections. See

Bug report
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518818](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518818)

In desperation I installed ndiswrapper and installed the Atheros AR9285 XP driver (v7.7.0.329) from here
[http://www.nodevice.com/driver/AR9285/get64221.html](http://www.nodevice.com/driver/AR9285/get64221.html)

No more dropped packets, but the driver takes longer to connect.

---

### Post by kammmo on 2010-12-23
i dont know your status,  your problem is resolved or no, try to check your proxy server settings..:) >>System>Preferences>Network Proxy :)) I had the same problem as you :) after set proxy is everything OK :popcorn:

---

### Post by zapho on 2011-02-28
> **togume said:**
> Thanks for the answer. This made a huge difference in my connection quality.

I ran some tests with the wireless power management on and off, and the difference was ridiculous.

With **sudo iwconfig eth1 on** (default, which causes the problem):
```
togume@togume-laptop:~$ ping google.com
PING google.com (74.125.95.106) 56(84) bytes of data.
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=1 ttl=53 time=102 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=2 ttl=53 time=125 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=3 ttl=53 time=47.1 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=4 ttl=53 time=72.8 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=5 ttl=53 time=90.9 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=6 ttl=53 time=113 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=7 ttl=53 time=243 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=8 ttl=53 time=874 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=9 ttl=53 time=919 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=10 ttl=53 time=824 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=11 ttl=53 time=104 ms
64 bytes from iw-in-f106.1e100.net (74.125.95.106): icmp_req=12 ttl=53 time=127 ms
^C
--- google.com ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 12981ms
rtt min/avg/max/mdev = 47.184/303.935/919.544/332.001 ms

```

With **sudo iwconfig eth1 off** (default, which causes the problem):
```
togume@togume-laptop:~$ ping google.com
PING google.com (74.125.95.105) 56(84) bytes of data.
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=1 ttl=53 time=32.8 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=2 ttl=53 time=30.1 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=3 ttl=53 time=31.4 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=4 ttl=53 time=33.3 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=5 ttl=53 time=89.9 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=6 ttl=53 time=37.1 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=7 ttl=53 time=208 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=8 ttl=53 time=201 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=9 ttl=53 time=167 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=10 ttl=53 time=154 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=11 ttl=53 time=144 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=12 ttl=53 time=57.1 ms
64 bytes from iw-in-f105.1e100.net (74.125.95.105): icmp_req=13 ttl=53 time=36.1 ms
^C
--- google.com ping statistics ---
13 packets transmitted, 13 received, 0% packet loss, time 12016ms
rtt min/avg/max/mdev = 30.138/94.199/208.725/67.716 ms
```

I did a quick search on to how to permanently disable this behavior, and came up with [this page]("http://uselessuseofcat.com/?p=67").

Basically, the solution is to create a file called **wireless** in the **/etc/pm/power.d/** directory. This file overrides the behavior of the /usr/lib/pm-utils/power.d/wireless script which causes the problem. To make sure that the wireless power management is disabled, enter the following in the newly created wireless script:

**/etc/pm/power.d/wireless**
```
#!/bin/sh

/sbin/iwconfig eth1 power off
```

Problem should be solved. However, this needs to be addressed in a formal way... Did anyone submit a bug request?

This worked perfectly for me as well! Finally my net is usable. Thanks a million everyone :D

---

### Post by salomonvh on 2011-03-04
Hi,

I got it fixed by right-clicking on internet connections, Edit connections...>Edit and setting IPv6 Settings to Automatic, DHCP only.

---

### Post by antcharwill on 2011-03-17
Hi all,
 
I've just installed Ubuntu 10.10 after having massive problems with windows vista (watching youtube videos caused the graphics card to freak out and crash the laptop), and I've found similar problems with my internet.
 
Certain websites load fine, most in fact, but certain ones really struggle: facebook and gmail for instance. I've tried Firefox, Chrome and Chromium and in each the pattern is the same. I can log in to facebook or gmail fine once, but the browser won't load any subsequent pages (facebook inbox, other profiles, emails in gmail etc.). Then, if I go back and try to log in again, the browser won't load the page at all, saying it's temporarily unavailable.
 
I've tried the fixes mentioned in this and related threads but nothing seems to help. It seems to be having trouble with pages that require you to log in to something, does that sound like it makes any sense?

---

### Post by vcrpex on 2011-05-17
> **wackyraces said:**
> I experienced slow web browsing on my laptop, using both wired and wireless connections. I'm using 64 bit Ubuntu 10.10. After following this tip, web browsing is back to normal again.

[http://usingnix.wordpress.com/2010/10/17/ubuntu-10-10-slow-internet/](http://usingnix.wordpress.com/2010/10/17/ubuntu-10-10-slow-internet/)

The tip involves disabling IPv6 when the machine boots, by adding a switch in GRUB. Disabling IPv6 this using the /etc/sysctl.conf method did not work for me.

I did, however, also apply these tweaks to /etc/sysctl.conf but on their own they did not work. I'm not sure if they have made any difference, or if you need to do both of these things in combination to get the speed increase.

## increase TCP max buffer size setable using setsockopt()
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
 ## increase Linux autotuning TCP buffer limits
 ## min, default, and max number of bytes to use
 ## set max to at least 4MB, or higher if you use very high BDP paths
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
 ## don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
 ## recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
 ## for 10 GigE, use this, uncomment below
 ## net.core.netdev_max_backlog = 30000
 ## Turn off timestamps if you're on a gigabit or very busy network
 ## Having it off is one less thing the IP stack needs to work on
 ## net.ipv4.tcp_timestamps = 0
 ## disable tcp selective acknowledgements.
net.ipv4.tcp_sack = 0
 ##enable window scaling
net.ipv4.tcp_window_scaling = 1

disabling ipv6 on boot works for me as well. I also tried the sysctl method. I was on the verge of formatting and jumping to maybe debian. glad i found this post. thank you.

---

