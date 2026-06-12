---
title: "network and wireless internet access slow"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by duvalt on 2011-11-25
Hello,

I have a question about internet speeds on both wireless and wired connections. 

When using either wireless or a wired connection to my enterprise lan (wireless is wpa2 psk, wired has no encryption or controls) the internet is extremely slow. 

I know this is not a hardware issue as I have Win 7 dual booting on it and am no longer having the issue. At first I did but fixed it with this: netsh int tcp set global autotuninglevel=disable
([http://www.vistax64.com/tutorials/72308-auto-tuning-tcp-ip-receive-level.html](http://www.vistax64.com/tutorials/72308-auto-tuning-tcp-ip-receive-level.html))

What I would like to know if there is anything in linux that would be analyzing traffic like autotuning or something that would be trying to watch for possible enterprise encryption. 

I have tried this:

sudo pico /etc/modprode.d/options.conf
options iwlagn 11n_disable=1
(save&exit)
sudo reboot

([http://ubuntuforums.org/showthread.php?p=11390174](http://ubuntuforums.org/showthread.php?p=11390174))

I had to switch to WICd to handle the WPA2 encryption; however the speed issue was existent before this change.

I have disabled IPv6 as far as I know. 


any help would be appreciated. 

Thank you

---

### Post by duvalt on 2011-11-25
just to add to this.

Our network firewall is a cisco asa 5501 

we looked up what to do about Win. 7 being slow to the internet with it an Cisco's official response is to turn off autotuning. 

So I guess it points to the way ubuntu is sending its Http traffic through the ASA. Does Ubuntu send http traffic differently than other distros? 

Puppy and Suse work fine.

---

### Post by duvalt on 2011-11-27
**Bump**

---

### Post by duvalt on 2011-11-29
bump

---

### Post by duvalt on 2011-12-01
Perhaps some info about the network cards installed:

trevor@ubuntutest:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 1c:c1:de:bf:1f:10
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=0.12-3 ip=172.20.17.58 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:d4700000-d471ffff memory:d472a000-d472afff ioport:5020(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:43:00.0
       logical name: wlan0
       version: 35
       serial: 00:27:10:2f:00:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-13-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:d0500000-d0501fff

---

### Post by duvalt on 2011-12-01
the wlan0 card is switched off but it is the same crappy Internet result:

Ubuntu on either wireless or wired: .65Mb Download .2 Upload

Win7: 30Mb Down 30 Up (synchronous speeds) 

basically I am thinking that Ubuntu is packet shaping the same way win7 and win vista does based on network traffic.

If so is it possible to turn that off? Any thoughts about this?

---

### Post by duvalt on 2011-12-02
ok so I am half way fixed.

I have used these settings in /etc/sysctl.conf 

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



This did not do anything until I noticed windows scaling. As stated in my other posts there must be some network scaling happening.

After changing net.ipv4.tcp_window_scaling=1 to =0 I drastically increased only my upload speeds. See the below speedtest results. 


[http://www.speedtest.net/result/1625350080.png](http://www.speedtest.net/result/1625350080.png)


second try

[http://www.speedtest.net/result/1625357094.png](http://www.speedtest.net/result/1625357094.png)


does anyone have anything i could try not that I know that the window scaling exists in Linux?

---

### Post by duvalt on 2011-12-02
ok ladies and gentlemen this one is solved.

combination of adding the lines in my previous post to turn off autotuning and enabling tcp_htcp congestion control.

I'll give you the end result first

[http://www.speedtest.net/result/1625392082.png](http://www.speedtest.net/result/1625392082.png)

21.86Mb down 22.63Mb up.


here is the command that solved the issue:

/sbin/modprobe tcp_htcp

---

### Post by duvalt on 2011-12-02
Ok so heres the overview of what I did:

use these settings in /etc/sysctl.conf

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
##enable window scaling **This one was the important one for upload**
**net.ipv4.tcp_window_scaling = 0** 

next do this:

Linux supports pluggable congestion control algorithms . To get a list of congestion control algorithms that are available in your kernel (kernal  2.6.20+), run:

sysctl net.ipv4.tcp_available_congestion_control

If cubic and/or htcp are not listed try the following, as most distributions include them as loadable kernel modules:

/sbin/modprobe tcp_htcp
/sbin/modprobe tcp_cubic


**since I only had cubic installed i needed to install htcp. I formatted and re-installed ubuntu on 3 differenct workstations, 2 with intel nics and one broadcom. Does not seem to matter what kind of card it did not install the htcp algorithm. Maybe a note should be made for the ubuntu developers on this.**

I know there are more people out there than just me with this issue. Ours and many other corporate networks are very complicated but it seems a lot of people behind a Cisco ASA 55XX series and/or a Cisco IPS. Win 7 requires autotuning to be off as stated on their site as the official "fix" for internet slowness and it appears what I have done "fixes" internet slowness on the linux side.

Now how do I set this as SOLVED?

---

### Post by Reiger on 2011-12-03
So you may also want to add tcp_htcp to /etc/modules (which is the list of modules to auto-load at boot time).

---

