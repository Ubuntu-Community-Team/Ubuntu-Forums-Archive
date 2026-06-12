---
title: "Killer E2200 ethernet not recognized."
date: 2013-08-10
forum: Networking &amp; Wireless
---

### Post by dustin2524 on 2013-08-10
I am very new to ubuntu (Linux in general) and just installed it on my laptop alongside windows 8. I can connect to my router just fine but Ethernet is a no-go. Here is all the possible information I could grab. 
```
dustin@dove:~$ sudo lshw -class network  
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Killer E2200 Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 13
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d3ffff ioport:c000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 135
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: c4
       serial: 0c:d2:92:47:43:57
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-19-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:45 memory:f7c00000-f7c01fff
```
```
dustin@dove:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3001 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:228528 (228.5 KB)  TX bytes:228528 (228.5 KB)


wlan0     Link encap:Ethernet  HWaddr 0c:d2:92:47:43:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:421 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:112382 (112.3 KB)  TX bytes:77148 (77.1 KB)
```
```
dustin@dove:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GTX 660M] (rev a1)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
02:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
03:00.0 Ethernet controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 13)
05:00.0 Network controller: Intel Corporation Centrino Wireless-N 135 (rev c4)
```
```
[FONT=arial]dustin@dove:~$ route[/FONT]
[FONT=arial]Kernel IP routing table[/FONT]
[FONT=arial]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT]
[FONT=arial]default         192.168.0.1       0.0.0.0             UG     0        0        0   wlan0[/FONT]
[FONT=arial]link-local      *                       255.255.0.0      U      1000    0        0   wlan0[/FONT]
[FONT=arial]192.168.0.0     *                   255.255.255.0   U       9        0        0   wlan0[/FONT]
```
```
ubuntu 13.04
```

The wireless cuts out A LOT but that might be something to do with the router and not ubuntu.

---

### Post by sanderj on 2013-08-10
If you search your unclaimed "Killer E2200" on this forum, you'll see it's possible to get it running, but quite difficulty (IMHO): it involves setting all kinds of settings.

Your Wifi is working, isn't it?

---

### Post by CitadelUniversal on 2013-08-10
Have you had a look at these:

[http://ubuntuforums.org/showthread.php?t=2075692](http://ubuntuforums.org/showthread.php?t=2075692)

[http://ubuntuforums.org/showthread.php?t=2034067](http://ubuntuforums.org/showthread.php?t=2034067)

[http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

These might help a bit..

---

### Post by chili555 on 2013-08-10
Please run the command:```
lspci -nn | grep 0200
```Is your device 1969:e091? Here are updated instructions to get your device working. First, I assume you are running Ubuntu 13.04:```
lsb_release -d
```If not, stop as these instructions are written for 13.04 only and will have unknown results on earlier or later Ubuntu versions. Open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
```Now download this to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.10/backports-3.10-2.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.10/backports-3.10-2.tar.bz2) Right-click it and select 'Extract Here.' Now back to the terminal:```
cd Desktop/backports-3.10-2
make defconfig-alx
make
sudo make install
sudo modprobe alx
```Your ethernet should now be working.

Post back if you get stuck or if it doesn't work as expected or if you have a different device. Certainly post back if it's solved so others can search and see the solution.

Then, if you'd like, let's fix up your wireless!

---

### Post by dustin2524 on 2013-08-10
Thanks a bunch chili! Everything went perfectly. Well I forgot sudo for the make install and that caused permission issues but I quickly realized my mistake. 

Now since you offered lets move onto issue number 2. My wireless internet stops working about ever 5 minutes. If you reconnect you will get another 5 minutes out of it or if you just wait a few minutes it will come back. This happens on windows 8, windows 7, and other laptops in the house as well. We have tried resetting the modem/router (it's one unit) before and that either does not or just gives us a temporary fix ranging from a day to a couple weeks.

---

### Post by chili555 on 2013-08-10
Let's do some housekeeping first. This is a fairly popular ethernet card that has been, up to now, a nightmare. Now it's easy! So that the searchers can find it, please edit the title of your thread to something like: *[SOLVED] Killer E2200 ethernet not recognized.*

Second, when a newer kernel is installed by Update Manager, you will need to recompile for the new kernel once you reboot:```
cd Desktop/backports-3.10-2
make clean
make defconfig-alx
make
sudo make install
sudo modprobe alx
```Please retain these instructions and the file for that time.

Finally, with respect to your wireless, please start a new thread and include:```
dmesg | grep -e iwl -e 80211
nm-tool
```Thanks.

Glad it's working!

---

### Post by chris112 on 2013-09-09
I would like to add on to this thread for any searching for a fix to problems with no connection to a wired killer e2200 because I searched and tried for several hours to get mine to work. I have a MSI Z87-GD65 gaming mobo that I used to build my first computer and am a first time linux user. The problem I faced was the mobo would read the ethernet register a connection in the BIOs, but Ubuntu 12.04 LTS would not register anything on the desktop. This thread worked for me after connecting a Belkin N150 Wi-fi USB adapter only for the purpose of gaining access to the internet and installing updates and the batch from this thread. I hope that this will help lessen the time it takes for those with the same problem as myself. Thank you to those that solved this problem and the Ubuntu community!

---

### Post by kkleidal on 2013-10-28
Just a quick note:  I just tried this on Ubuntu 12.04.3 LTS, and it solved my problem.  Thanks!

---

### Post by iamthebofh on 2013-10-31
Hi Chili555

This looks exactly what I'm looking for, thank you for the post. I have one question though. With the third step (sudo apt-get install linux-headers-generic build-essential) it needs to connect to the internet to get these files obviously. I don't have wifi access from PC, hence I need to get my NIC up and running. Is there a way for me to get these files via my working Windows install and install them manually onto the Linux? 

I am also a proper Linux noob and any help will be greatly appreciated.

Thanks

---

### Post by chili555 on 2013-10-31
>  Is there a way for me to get these files via my working Windows install and install them manually onto the Linux?Anything is possible. It is long, hard, tedious and almost no-one, including me, gets it in the first 2-3 tries. You could also beg, borrow or steal (oooops, no!) a USB wireless connection from a pal for two minutes and be all set.

I'll be right back. I'm machining an 8 ft. cube of titanium to make a microwave oven. I'm craving popcorn.

Get my point?

I'll help you either way.

---

### Post by Joe_McGuckin on 2014-01-21
I recently purchased an MSI gaming motherboard. The Ubuntu distro installed and runs, but ifconfig shows zeroed out counters for the p3p1 interface.
This doesn't seem normal.

Any suggestions?

Thanks,

Joe

---

### Post by chili555 on 2014-01-21
Please show us:```
ifconfig
sudo lshw -C network
ping -c3 www.google.com
lsb_release -d
```Thanks.

---

### Post by Joe_McGuckin on 2014-01-21
[COLOR=#00B225][FONT=Lucida Console]joe@miner1:~$ ifconfig[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]lo        Link encap:Local Loopback  [/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          inet6 addr: ::1/128 Scope:Host[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          RX packets:48 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          collisions:0 txqueuelen:0 [/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          RX bytes:3696 (3.6 KB)  TX bytes:3696 (3.6 KB)[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]
[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]p3p1      Link encap:Ethernet  HWaddr d4:3d:7e:f1:c3:3c  [/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          inet addr:157.22.219.243  Bcast:157.22.219.255  Mask:255.255.255.192[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          inet6 addr: fe80::d63d:7eff:fef1:c33c/64 Scope:Link[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          collisions:0 txqueuelen:1000 [/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]          Interrupt:19 [/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]
[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]joe@miner1:~$ [/FONT][/COLOR]


[COLOR=#00B225][FONT=Lucida Console]root@miner1:/home/joe# lshw -C network[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]  *-network               [/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       description: Ethernet interface[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       product: Killer E2200 Gigabit Ethernet Controller[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       vendor: Qualcomm Atheros[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       physical id: 0[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       bus info: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       logical name: p3p1[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       version: 13[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       serial: d4:3d:7e:f1:c3:3c[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       size: 100Mbit/s[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       capacity: 1Gbit/s[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       width: 64 bits[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=157.22.219.243 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]       resources: irq:50 memory:f7d00000-f7d3ffff ioport:d000(size=128)[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]root@miner1:/home/joe# [/FONT][/COLOR]


Pinging gateway address as firewall blocks incoming ICMP:

[COLOR=#00B225][FONT=Lucida Console]root@miner1:/home/joe# ping -c3 157.22.219.193[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]PING 157.22.219.193 (157.22.219.193) 56(84) bytes of data.[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]64 bytes from 157.22.219.193: icmp_seq=1 ttl=255 time=0.476 ms[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]64 bytes from 157.22.219.193: icmp_seq=2 ttl=255 time=5.35 ms[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]64 bytes from 157.22.219.193: icmp_seq=3 ttl=255 time=0.472 ms[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]
[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]--- 157.22.219.193 ping statistics ---[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]3 packets transmitted, 3 received, 0% packet loss, time 2000ms[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]rtt min/avg/max/mdev = 0.472/2.099/5.351/2.299 ms[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]root@miner1:/home/joe# [/FONT][/COLOR]


[COLOR=#00B225][FONT=Lucida Console]root@miner1:/home/joe# lsb_release -a[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]No LSB modules are available.[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]Distributor ID:    Ubuntu[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]Description:    Ubuntu 13.10[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]Release:    13.10[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]Codename:    saucy[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]root@miner1:/home/joe# [/FONT][/COLOR]



[COLOR=#00B225][FONT=Lucida Console] uname -a[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]Linux miner1 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
[COLOR=#00B225][FONT=Lucida Console]root@miner1:/home/joe#


[/FONT][/COLOR]






Thanks!

---

### Post by chili555 on 2014-01-21
Regardless of the puzzling *ifconfig* TX and RX numbers, it appears that you are well and truly connected, insofar as the firewall allows. Yes? No?

---

### Post by Joe_McGuckin on 2014-01-21
Yes, the ethernet interface is working, I'm simply concerned that the tx/rx numbers don't increment - makes me wonder if there's some driver weirdness.

Joe

---

### Post by chili555 on 2014-01-21
> **Joe_McGuckin said:**
> Yes, the ethernet interface is working, I'm simply concerned that the tx/rx numbers don't increment - makes me wonder if there's some driver weirdness.

JoeProbably. It isn't critical, is it? You could report a bug, but the term 'back burner' comes to mind. [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Is the behavior the same if you momentarily drop the firewall and ping Google? Fascinating.

---

### Post by michael97 on 2014-01-23
Thanks [**[COLOR=#000000]kkleidal[/COLOR]**]("http://ubuntuforums.org/member.php?u=1875900") for confirming that this works with 12.04.3 LTS!

---

