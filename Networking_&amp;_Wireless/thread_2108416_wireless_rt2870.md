---
title: "wireless rt2870"
date: 2013-01-24
forum: Networking &amp; Wireless
---

### Post by Hodevah on 2013-01-24
Hi. I recently installed the latest version of Ubuntu about a week ago. I have had a look around the net and have tried to follow a number of threads on how to get a Ralink2870 driver working. 

My problem is mostly in the comprehension of commands in the Terminal. 
In the terminal, I have the following output using lsusb

> Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 004: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 005: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 004 Device 002: ID 05e3:0612 Genesys Logic, Inc. 
Bus 004 Device 003: ID 05e3:0612 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0db0:3871 Micro Star International 
Bus 002 Device 004: ID 0db0:a871 Micro Star International 
Bus 003 Device 006: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 003 Device 007: ID 4971:ce07 SimpleTech 
Bus 003 Device 008: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
user@user-desktop:~$ 
As you can see, I am still using Microstar International. I don't think that is what I should/need to be using. On the Windows 7 side of my computer, I am running the Ralink 2870 driver; thereofore, I should be running this same driver in Ubuntu.

I find that the current wifi setup that was given me upon the install is working not very well. It seems to be in and out. That is, connections are good one minute and the next they are out. 

My landlord let's me  use his Wifi so this means that I don't have access to their router. 

There are a number of posts/threads that I have visited and found some helpful information on them . 

Firstly, I download the ralink 2870 from the ralink website. 
Secondly, a number of the threads  I visited did help but only so much. 
Some threads  I found useful were the following:

*(1). ubuntuforums.org/showthread.php?t=1743530*

*(2) ubuntuforums.org/showthread.php?t=1855422*

*(3) ubuntuforums.org/showthread.php?t=960642*

In the first thread, in the first post, it says to change the 'n' to 'y' as shown below.

> # Support Wpa_Supplicant HAS_WPA_SUPPLICANT=y  # Support Native WpaSupplicant for Network Maganger HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=yI did that.  
In the third point in that first post, it says to change 

> LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/net/wirelessto this

> LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/staging/rt2870I did that too; however, I found conflicting information in the second link that I gave above and in post #2,* 'kelwynsa8'* says to not change it. So I reverted the above change back to it's original content. 

In the third link I gave above, I tried to do as per instructions. The problem that I have with this post is in understanding how to go about it so that I am using the Ralink2870 driver. 

There is some very useful information that I found at this thread here;

*(4) ubuntuforums.org/showthread.php?t=1783881&highlight=rt2870*

This thread seems to have given me a boost up until the terminal command:

> cp RT2870.[SIZE=2]dat[/SIZE] /etc/Wireless/RT2870STA/[FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]

[SIZE=2][SIZE=2]which [SIZE=2]at the very end[/SIZE] gave me th[SIZE=2]is[/SIZE] output

[/SIZE][/SIZE][/FONT][/SIZE][/COLOR][/SIZE][/FONT]
> make[2]: *** [/home/user/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/user/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-22-generic'
make: *** [LINUX] Error 2
user@user-desktop:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ [FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif][SIZE=2][SIZE=2]

[SIZE=2]I decided to i[SIZE=2]gnore the [SIZE=2]erro[SIZE=2]rs and go ahe[SIZE=2]ad with the next [SIZE=2]terminal comm[SIZE=2]and as [SIZE=2]manzdagratiano puts in post #6 in that l[SIZE=2]ast link I gave above. The command that [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/COLOR][/SIZE][/FONT][SIZE=2][FONT=Arial, Helvetica, sans-serif]I co[SIZE=2]uld not go any further was at the Terminal command

[/SIZE][/FONT][/SIZE]> [FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]sudo [/FONT][/SIZE][/COLOR][/SIZE][/FONT][FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]insmod rt2870sta.ko[/FONT][/SIZE][/COLOR][/SIZE][/FONT]which gave me the output

> insmod: can't read 'rt2870sta.ko': No such file or directory
This is where I get stuck.


For your information some useful terminal command outputs are the following

> user@user-desktop:~$ iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"XXXXXX"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 20:76:00:06:B3:54   
          Bit Rate:19.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:125  Invalid misc:87   Missed beacon:0
> user@user-desktop:~$ iwpriv
eth0      no private ioctls.

eth1      no private ioctls.

lo        no private ioctls.

wlan0     no private ioctls.

by the way, before I started out in any of the above attempts, I did run in the terminal

> apt-get update
apt-get install build-essential

---

### Post by bogan on 2013-01-25
Hi!, **houdeva**h,

If you google "0db0:3871 Micro Star International" you will see that it is indeed a RalinkRT2870 chip and ubuntu uses the the same rt2870 driver for linux.

Please Post:```
uname -r
ifconfig -a | grep -iA9 wlan0
sudo lshw -C network
lsmod | grep -e rt2
```Chao!, **bogan**.

---

### Post by Hodevah on 2013-01-25
Hi bogan, and thanks for getting back to me about this. Here is what the results were of the terminal command you asked for.

> user@user-desktop:~$ uname -r
3.5.0-22-generic
user@user-desktop:~$ ifconfig -a | grep -iA9 wlan0
wlan0     Link encap:Ethernet  HWaddr 94:db:c9:50:d4:94  
          inet addr:192.168.1.96  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::96db:c9ff:fe50:d494/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1262657 (1.2 MB)  TX bytes:257138 (257.1 KB)

user@user-desktop:~$ sudo lshw -C network
[sudo] password for user: 
Sorry, try again.
[sudo] password for user: 
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 00:22:4d:82:e5:5d
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:52 memory:eff00000-eff1ffff memory:eff39000-eff39fff ioport:f040(size=32)
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 00
       serial: 00:22:4d:82:e5:6c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=2.1-2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:efd20000-efd3ffff memory:efd00000-efd1ffff ioport:d000(size=32) memory:efd40000-efd43fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.5
       logical name: wlan0
       serial: 94:db:c9:50:d4:94
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.5.0-22-generic firmware=0.29 ip=192.168.1.96 link=yes multicast=yes wireless=IEEE 802.11bgn
user@user-desktop:~$ 
I see that it shows that I am using the rt2800 usb driver version. 

I don't understand something. YOur saying that I am using the 2870 driver on the Linux side. But it says that I am using a ralink 2800 driver. Or is it just being loaded up as a 2800 driver wherein it is actually a ralink 2870 driver?

Also, I went to this link here  "[http://wiki.debian.org/rt2800usb](http://wiki.debian.org/rt2800usb)" after I did a brief Google on 
*'0db0:3871 Micro Star International"*

At that link, it states that 

> It is included in the mainline Linux kernel since version 2.6.31 and replaces the [rt2870sta]("http://wiki.debian.org/rt2870sta") staging driverso basically, from what I understand then is that the ralink 2870sta driver is replaced (*for what-ever reason, I guess*). But that is for Debian systems. Would or could that also then be applicable for Ununtu OS? I mean, I guess it could since that is what the terminal command reported. 

Again, thanks a bunch for replying and looking forward to hearing from you in this thread once again.  :)

EDIT: Additional information found that I think might coincide with what I stated above:

> This adds support for rt27xx/rt28xx/rt30xx wireless chipset family. Supported chips: RT2770, RT2870 & RT3070, RT3071 & RT3072
  **When compiled as a module, this driver will be called "rt2800usb.ko".**


I got that information from this link here:
[http://cateee.net/lkddb/web-lkddb/RT2800USB.html](http://cateee.net/lkddb/web-lkddb/RT2800USB.html)

---

### Post by squakie on 2013-01-25
I need to do some more review of your posts, but the first thing I can tell you is that Ubuntu is based on Debian, so if something works in Debian it should work in ubuntu.

I also noticed your errors when trying to build the driver.  Since there were errors, then of course there was no module to load - hence the error on trying to modprobe the driver.  I do have a couple of questions for you regarding this download:

[LIST]
[*]usually when you download something like this it is an archive, so after download you have unpack it - it should go in a new subfolder.  After that, via the command line, you need to change your working directory (cd) to that newly created subfolder.  There should be a readme file there also for you to read.
[*]be sure to install the build-essential package.  While the description now indicates it is only needed if building deb packages, it should be noted that you want to install all of its dependencies as you'll need those.  So, just simply install the build-essential package.
[/LIST]
After the above, then try compiling your driver again.

---

### Post by 3rdalbum on 2013-01-26
You already have the driver installed. Compiling it from source will not help unless it is a newer version than what comes in the kernel and the reliability problems are the result of bugs in the older version.

What you should try first is connecting to the router and then changing the speed of the card from "auto" to "5.5m". The iwconfig command can do this, I can't remember the exact syntax but you can see it in the manual or on Google.

---

### Post by Hodevah on 2013-01-26
> **3rdalbum said:**
> .
What you should try first is connecting to the router and then changing  the speed of the card from "auto" to "5.5m". The iwconfig command can do  this, I can't remember the exact syntax but you can see it in the  manual or on Google.

Hi. As I mentioned earlier in my first post, I don't have a router. My landlord let's me use his wifi.  :)

And I also appreciate your help.  :D


> **squakie said:**
> I need to do some more review of your posts, but the first thing I can tell you is that Ubuntu is based on Debian, so if something works in Debian it should work in ubuntu.

I also noticed your errors when trying to build the driver.  Since there were errors, then of course there was no module to load - hence the error on trying to modprobe the driver.  I do have a couple of questions for you regarding this download:

[LIST]
[*]usually when you download something like this it is an archive, so after download you have unpack it - it should go in a new subfolder.  After that, via the command line, you need to change your working directory (cd) to that newly created subfolder.  There should be a readme file there also for you to read.
[*]be sure to install the build-essential package.  While the description now indicates it is only needed if building deb packages, it should be noted that you want to install all of its dependencies as you'll need those.  So, just simply install the build-essential package.
[/LIST]
After the above, then try compiling your driver again.

Hi. 
Yes. Your right and I understand about having to unarchive files into a seperate folder. After I downloaded the archived file to my desktop, it came out with a new folder from which I knew to work with. Leaving it there for further usage. 

The working directory from which I was to now work with was the following:

> user@user-desktop:~$ cd /home/user/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1
user@user-desktop:~/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1$ 

afterwords, if memory serves me correct, I then began to work out of

> 
user@user-desktop:~/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux

I believe that I did those Terminal commands correctly, did I not? Please do inform me of any mistakes. I assume that I did that command correctly because of the output. 

And I do believe I did the build essential package as I stated close to the very bottom of my first post. I do believe that those were the correct commands, were they not? 

And I did those Terminal commands at the very beginning even though I posted those commands at the bottom of my first post. I only mentioned them at that point in the post because I had forgotten to post them initially and only posted them then (last).

---

### Post by squakie on 2013-01-26
Another question - are you running 12.04 LTS or are you running 12.10?  I've read various places that this adapter should be recognized and work find with 12.10 - no need to try another driver.  So, if you just installed, and if you are at 12.04 LTS, you may want to try downloading the ISO for 12.10, burn it to a disk, boot the disk and see if your wifi works better then.  If so, I would install 12.10 at that point.

---

### Post by Hodevah on 2013-01-26
> **squakie said:**
> Another question - are you running 12.04 LTS or are you running 12.10?  I've read various places that this adapter should be recognized and work find with 12.10 - no need to try another driver.  So, if you just installed, and if you are at 12.04 LTS, you may want to try downloading the ISO for 12.10, burn it to a disk, boot the disk and see if your wifi works better then.  If so, I would install 12.10 at that point.


No. I don't have 12.10 LTS. I installed just 12.10 via USB. 

I initially tried installing 12.10 via CD but I noticed that it kept hanging during it's boot into RAM. Found that to be very unusual. After booting into RAM, it continued to take a very long time to load up. Very strange and unusual, I felt. So I booted/installed via USB. But of course, none of that would be related to wifi. 


** EDIT: Additional info.**   

So as I no longer have any working wifi on Ubuntu 12.10 (*no changes to network/wifi were made the last time I used Ubuntu)*, this leaves me to pretty much make posts via Windows 7 or on my laptop which uses Broadcom, of which there are no problems with that when using Linux Mint 14.

---

### Post by GordThompson on 2013-01-26
> **3rdalbum said:**
> You already have the driver installed. Compiling it from source will not help unless it is a newer version than what comes in the kernel and the reliability problems are the result of bugs in the older version.

What you should try first is connecting to the router and then changing the speed of the card from "auto" to "5.5m". The iwconfig command can do this, I can't remember the exact syntax but you can see it in the manual or on Google.

> **Hodevah said:**
> Hi. As I mentioned earlier in my first post, I don't have a router. My landlord let's me use his wifi.  :)
I think you misunderstood. 3rdalbum just wanted you to change the speed setting of *your wireless adapter *using a command like

```
sudo iwconfig wlan0 rate 5.5M
```

---

### Post by Hodevah on 2013-01-26
> **GordThompson said:**
> I think you misunderstood. 3rdalbum just wanted you to change the speed setting of *your wireless adapter *using a command like

```
sudo iwconfig wlan0 rate 5.5M
```

Hi again, GordThompson.  :)
So I can do this even though I don't have physical access to a router?
 I'll give it a try then and post results. But I don't expect anything magical though. 

**EDIT**: Here are the results:

> user@user-desktop:~$ sudo iwconfig wlan0 rate 5.5M
[sudo] password for user: 
user@user-desktop:~$ 
Nothing. 
One other thing that I did try is according to the link here: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

*[[COLOR=#DD4814]ugm6hr[/COLOR]]("http://ubuntuforums.org/member.php?u=103883")* says to turn off Power Save function.  This I did on my Desktop as you can see here from this screen shot:


[IMG]http://i.imgur.com/2c3zcYq.jpg[/IMG]


After this, I rebooted into Ubuntu and thence found no network availability. Returned to Windows 7 to undo recent changes. Rebooted back into Ubuntu and now as of this writing, I have network service again. 

What I have noticed so far is that my wifi seems to intermittently go historically go On and Off. But this as I am sure as you read in my first post, are aware of.  :)


Also, did the following Terminal command

> ifconfig iwconfig route -n ping -c 3 208.67.219.101 ping -c 3 [www.opendns.com]("http://www.opendns.com")Results listed below: 


> user@user-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:4d:82:e5:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:eff00000-eff20000 

eth1      Link encap:Ethernet  HWaddr 00:22:4d:82:e5:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efd20000-efd40000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23580 (23.5 KB)  TX bytes:23580 (23.5 KB)

wlan0     Link encap:Ethernet  HWaddr 94:db:c9:50:d4:94  
          inet addr:192.168.1.96  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::96db:c9ff:fe50:d494/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2665194 (2.6 MB)  TX bytes:497448 (497.4 KB)

user@user-desktop:~$ iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"mcnzh"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 20:76:00:06:B3:54   
          Bit Rate:5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:62   Missed beacon:0

user@user-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
user@user-desktop:~$ ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.


--- 208.67.219.101 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

user@user-desktop:~$ ping -c 3 [www.opendns.com]("http://www.opendns.com")
PING [www.opendns.com]("http://www.opendns.com") (67.215.92.210) 56(84) bytes of data.

Also, Terminal command

> uname -aResults:

> user@user-desktop:~$ uname -a
Linux user-desktop 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
user@user-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal
user@user-desktop:~$ 
Terminal command:
> lspciResults:
> user@user-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1c.7 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts XT [Radeon HD 6800 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Barts HDMI Audio [Radeon HD 6800 Series]
03:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
04:00.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:01.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:04.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:05.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:07.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:09.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
07:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11)
0a:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 30)
0b:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
0c:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11)
Terminal command:
> lsusbResults:

> user@user-desktop:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 004: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 005: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 004 Device 002: ID 05e3:0612 Genesys Logic, Inc. 
Bus 004 Device 003: ID 05e3:0612 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0db0:3871 Micro Star International 
Bus 002 Device 004: ID 0db0:a871 Micro Star International 
Bus 003 Device 006: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 003 Device 007: ID 4971:ce07 SimpleTech 
Bus 003 Device 008: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUBTerminal command:
> route -nResults:
> user@user-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0Terminal command:
> sudo lshw -class networkResults: 
> user@user-desktop:~$ sudo lshw -class network
[sudo] password for user: 
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 00:22:4d:82:e5:5d
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz

The security I am using is
> WPA/WPA2

---

### Post by 3rdalbum on 2013-01-26
I should have explained better. Connect to wireless, and run the iwconfig command again. It will not give any indication of anything, but it will make your card communicate at a constant conservative speed rather than vary the speed to try and find the best at each moment. Try your internet now.

The changes will be lost after reboot but that's okay, it can be set up to run that command on boot.

---

### Post by bogan on 2013-01-26
Hi!, **Hodevah, **

You Posted:```
I don't understand something. YOur saying that I am using the 2870  driver on the Linux side. But it says that I am using a ralink 2800  driver. 
```What I meant was that the system will use the driver included with the kernel, that is correct for the RTL2870 chip .

You did not Post:```
 lsmod | grep -e rt2
```Which would confirm rt28XX.xxx is actually in use.

'uname -r shows you are using 12.10 3.5.0-22-generic, which is Quantal.

There is a generalised driver update available, which is included with the latest kernel update to 3.5.0-23 #35, just released as a 'Proposed' version. [ To install this, activate the 'proposed' option in Software Sources, and Update.]

You can download and install this separately - if you have a connection - with: ```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```I have this installed in both three versions of 12.10 and one of 12.04 and the result is a huge improvement - if not quite perfect - in internet connection and reliability, using both a Realtek and a Ralink wifi Adapter.

Chao!, **bogan.**

---

### Post by Hodevah on 2013-01-26
> **3rdalbum said:**
> I should have explained better. Connect to  wireless, and run the iwconfig command again. It will not give any  indication of anything, but it will make your card communicate at a  constant conservative speed rather than vary the speed to try and find  the best at each moment. Try your internet now.

The changes will be lost after reboot but that's okay, it can be set up to run that command on boot, it can be set up to run that command on boot.


Ok. Done that. Results are, as you say, give no indication of anything. And as such Terminal output no different than what I posted in post#10. 
When I left click on Network>Information sometime thereafter, I see

> 5 Mb/sHow possible to run on boot up?

Also, @Bogan:

Terminal command:
> lsmod | grep -e rt2Results:
> user@user-desktop:~$  lsmod | grep -e rt2
rt2800usb              22662  0 
rt2800lib              58731  1 rt2800usb
crc_ccitt              12708  1 rt2800lib
rt2x00usb              20665  1 rt2800usb
rt2x00lib              54939  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              539958  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              206797  2 rt2x00lib,mac80211
user@user-desktop:~$ > What I meant was that the system will use the driver included with the kernel, that is correct for the RTL2870 chip I think I might understand. What your saying then is that the RT2800 is what I am supposed to be using.

Also, Terminal command:
> 
sudo apt-get install linux-backports-modules-cw-3.6-quantal-genericResults:
> user@user-desktop:~$ sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-backports-modules-cw-3.6-3.5.0-22-generic
The following NEW packages will be installed:
  linux-backports-modules-cw-3.6-3.5.0-22-generic
  linux-backports-modules-cw-3.6-quantal-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,986 kB of archives.
After this operation, 11.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-backports-modules-cw-3.6-3.5.0-22-generic amd64 3.5.0-22.8 [2,983 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-backports-modules-cw-3.6-quantal-generic amd64 3.5.0.22.28 [2,658 B]
Fetched 2,986 kB in 7s (425 kB/s)                                              
Selecting previously unselected package linux-backports-modules-cw-3.6-3.5.0-22-generic.
(Reading database ... 182588 files and directories currently installed.)
Unpacking linux-backports-modules-cw-3.6-3.5.0-22-generic (from .../linux-backports-modules-cw-3.6-3.5.0-22-generic_3.5.0-22.8_amd64.deb) ...
Selecting previously unselected package linux-backports-modules-cw-3.6-quantal-generic.
Unpacking linux-backports-modules-cw-3.6-quantal-generic (from .../linux-backports-modules-cw-3.6-quantal-generic_3.5.0.22.28_amd64.deb) ...
Setting up linux-backports-modules-cw-3.6-3.5.0-22-generic (3.5.0-22.8) ...
update-initramfs: Generating /boot/initrd.img-3.5.0-22-generic
Setting up linux-backports-modules-cw-3.6-quantal-generic (3.5.0.22.28) ...
user@user-desktop:~$ Ok. So I guess the modules were downloaded (*since I was able to attain internet connection again)* and applied. Rebooted there-after.
[B]
EDIT: Additional information after reboot:[/B]

> Speed: 19 Mb/sThis small bit of info coincides with what you said, 3rdalbum. That the speed does vary. So what you are proposing is that I keep the speed constant at the speed you provided for as an example. Is that correct?

---

### Post by bogan on 2013-01-26
Hi!,** hodevah**,

What you Posted looks the same as what I got installing 'backports-modules-cw-3.6-quantal-generic'.

Where did you get the Speed figure of [COLOR=Red]15Mb/s[/COLOR]??  from Network>wireless ??

As far as I know, that is a theoretical maximum for the hardware and firmware, mine shows 54Mb/s, but my [COLOR=RoyalBlue]actual maximum[/COLOR] download speed is never more than[COLOR=Red] 1.5 Mb/s.[/COLOR]

From memory of more than two years ago, when I was using the rt2800usb driver I was told that the rt2x00usb driver [ and rt2x00lib ]would conflict with the rt2800usb and I should blacklist them.

You could try that, you can always remove the blacklist if it does not help, but, on the other hand, if it works dont 'fix' it.

Chao!, **bogan**.

---

### Post by Hodevah on 2013-01-27
Hello bogan.   The speed that I posted above I got from the left-click selection of the wireless  icon. Under *"Information",* I am able to see the speed posted. I noticed that it also varied. A few times I noticed that it went down to 13/14 mb/s and then sometime there-after to returned to 19 mb/s.   In consideration of blacklisting the unwanted drivers so as to prevent conflict, would you mind just briefly explaining me how I might be able to do that, please? That is, which text file should I access to make any corrections (if that would be the case)?

---

### Post by 3rdalbum on 2013-01-27
> **Hodevah said:**
> Hello bogan.   The speed that I posted above I got from the left-click selection of the wireless  icon. Under *"Information",* I am able to see the speed posted. I noticed that it also varied. A few times I noticed that it went down to 13/14 mb/s and then sometime there-after to returned to 19 mb/s.   In consideration of blacklisting the unwanted drivers so as to prevent conflict, would you mind just briefly explaining me how I might be able to do that, please? That is, which text file should I access to make any corrections (if that would be the case)?

Hodevah, you understand exactly what I mean about setting the speed to something constant. The driver may be switching to too high a speed and losing connection.

If you take out the word 'sudo' from the iwconfig command, and put the remainder of the command into /etc/rc.local, it will run on startup.

If an inappropriate driver is being loaded for the card, like Bogan says, you would need to put its name into the file /etc/modprobe.d/blacklist.conf

I used to have to blacklist a driver when I was using a very similar card to yours but it has worked fine out-of-the-box since Ubuntu 11.04. If you know what driver is currently in use you can try 'sudo modprobe -r ' then the driver name, to temporarily deactivate the driver, and see what other driver takes hold, if any.

---

### Post by Hodevah on 2013-01-27
HI 3rdalbum: 

The shell script *rc.local *currently has the following in it. 

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
So as I am leaving out the *'sudo' *portion of the command and am instead going to insert 
> iwconfig wlan0 rate 5.5M(if that will be the rate that I am going to use, that is. Actually I should ask here at this point. According to your experience, would this be a decent rate so as to maintain constancy without it losing connection on an infrequent basis? Since I've run the command that bogan gave earlier in post #12

> sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic  I have not really noticed any drop outs since bogan's suggestion to install the backports module.   That's a great thing! :p)

So as to prevent any type of errors experienced and to proceed prudently beforehand, where precisely within the shell script will I be placing it? 

For example, will I be placing the *iwconfig* command immediately after *#!/bin/sh -e*
such that it would look like this:

> #!/bin/sh -e
**#iwconfig wlan0 rate 5.5M**
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0Thanks again for your kind help.  :p

---

### Post by GordThompson on 2013-01-27
> **Hodevah said:**
> So as to prevent any type of errors experienced and to proceed prudently beforehand, where precisely within the shell script will I be placing it? 

For example, will I be placing the *iwconfig* command immediately after *#!/bin/sh -e*
such that it would look like this:
You probably noticed that all but 1 of the lines in the default script started with '#' which means that they are comments. The last line 'exit 0' terminates the script. So, one would normally add new commands just before the 'exit 0' statement.

---

### Post by bogan on 2013-01-27
Hi!, **Hodevah,**

+1 to **GordThompson**'s Post, but you do not want the '#' symbol at the start of your command line, except to deactivate it.

To blacklist a driver: ```
gksudo gedit /etc/modprobe/blacklist.conf
``` and add, for example, like this:> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# for ralink rt2573
# blacklist rt2x00usb
 # blacklist rt2x00lib
# blacklist rt2x00 Substitute the drivers shown in the lsmod output and remove the '#' fr0m the one you want  to blacklist. Save and reboot twice.

Like **3rdalbum **I no longer have to blacklist any drivers, I made up that list a year ago, and when I tried them, one at a time, it made no difference. So I am not advising you to blacklist anything, merely suggesting it as something you could try out.

If the 'cw' compat-wireless-modules, and the speed limit have done the trick, I would leave alone what is working.

In Network>wireless the speed shown is the same as in the Network dropdown menu Connection Information. ie usually 54Mb/s, at present 48 Mb/s, but actual maximum 1.5 Mb/s. I am going to try the limit at 5.5M.

Chao!,** bogan.**

---

### Post by Hodevah on 2013-01-28
Hi everyone.

Terribly sorry for a late reply as it was not my intention to reply late. Most especially in consideration of wanting to resolve a number of Ubuntu related concerns. One of them being no internet  again. 

I was able to edit the rc.local file via Terminal command:

> gksudo gedit /etc/rc.localand have the file saved with the result as shown below


> #!/bin/sh -e
iwconfig wlan0 rate 7.0M
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0Rebooted.

No change in Speed. For example, speed as of this writing is 21Mb/s. I have seen it as high as 45 on a prior occasion.

Terminal command

> iwconfig wlan0 rate 7.0M Result:

> user@user-desktop:~$ iwconfig wlan0 rate 7.0M
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; Operation not permitted.Changed the* rc.local* script file from 7.0M to 7M (* I thought that perhaps there would be an interpretation error as a result of having the ".0")*.

Rebooted.

No change. Inconsistent rate continues.

Terminal command

> sudo iwconfig wlan0 rate 7MResult:
> 
user@user-desktop:~$** sudo** iwconfig wlan0 rate 7M
user@user-desktop:~$ iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"mcnzh"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 20:76:00:06:B3:54   
          Bit Rate:**21.7 Mb/s**   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:31  Invalid misc:57   Missed beacon:0Have done some Googling. Some results suggest to turn IPv6 off.  Though I don't see how that would change things. 
IPv6 is/has been off since start. 

Just for the sake of providing a different rate other than the one I displayed above. I changed the* rc.local* file to 5.5M
No change.

---

### Post by bogan on 2013-01-28
Hi!, Hodevah,

I do not have any skill in the bit-rate business, but this is from  'man iwconfig':
>   rate/bit[rate]
              For  cards  supporting  multiple  bit rates, set the bit-rate in
              b/s. The bit-rate is the speed at  which  bits  are  transmitted
              over  the  medium,  the  user  speed of the link is lower due to
              medium sharing and various overhead.
              You may append the suffix k, M or G to the value (decimal multi&#8208;
              plier  :  10^3,  10^6  and  10^9 b/s), or add enough '0'. Values
              below 1000 are card specific, usually an index in  the  bit-rate
              list.  Use  auto  to select automatic bit-rate mode (fallback to
              lower rate on noisy channels), which is  the  default  for  most
              cards, and fixed to revert back to fixed setting. If you specify
              a bit-rate value and append auto, the driver will use  all  bit-
              rates lower and equal than this value.
              Examples :
                   iwconfig eth0 rate 11M
                   iwconfig eth0 rate auto
                   iwconfig eth0 rate 5.5M autoI should think you might try the last example, substituting wlan0 [ make sure it is a 'nought'.

Chao!, **bogan.**

---

### Post by squakie on 2013-01-28
Perhaps it's a timing issue?  It may be executing the command in the file before wireless is actually up, which I would think would mean the command would just drop off into the bit bucket.

---

### Post by Hodevah on 2013-01-28
> **squakie said:**
> Perhaps it's a timing issue?  It may be executing the command in the file before wireless is actually up, which I would think would mean the command would just drop off into the bit bucket.

I am thinking that perhaps squakie is perhaps correct. This is evidenced by the fact that since I rebooted a couple of times after editing the *rc.local* file, that currently and since then (about a couple of hours since the editing), that the speed is currently displayed at 5 Mb/s. 


Overall, I think this pretty much solves my issues with respect to connectivity. I surmise that I was pretty much offline because of there being no constancy in wifi connectivity speed issues the last time I booted up Ubuntu. 

One final thing that I'd like to bring up and it pertains to the earlier actions I undertook as posted in my first post in this thread.
 For example, removal of prior scripts etc  made from initial commands but obviously never were necessary since I am using the correct driver (rt2800) that is made for what I thought I needed, that is, rt2870 (* confusion and misinterpretation on my part)*

**(1)** Are there any changes that I need to enable in order to avoid potential conflict with the first Terminal input commands (*if, according to your knowledge base and experiences such commands might cause conflict issues) *I posted in** post #1**? 
That being based on the fact that those files and commands were enabled via Terminal commands. 
Yet, they have not been utilized (or perhaps were/are, though unnoticed).

**(2).** Might there be any potential conflicts with connectivity in regards to having changed *LINUX_SRC_MODULE*  lines to what is described per instructions in the README file having accompanied the *2010_0709_RT2870_Linux_STA_v2.4.0.1.tar* which I downloaded, extracted, and worked from. 

I hope the above posted questions I pose do make sense. If not, please let me know to clarify.  :o

Thank you all very, very, very much for having helped me out and having clarified a number of issues.

---

### Post by bogan on 2013-01-29
Hi!. **Hodevah,**

Q 1) I am not able to answer.

Q 2) In the case of video drivers, and I imagine the same applies to Network Adapter drivers, it is certainly advisable to clean out the previously installed driver specifically, by package name, and to purge its config files, before installing another version. eg:```
 sudo apt-get remove --purge <package-name>
```.

Similarly with re-installation of the kernal, formatting the root partition and mounting, but not formatting, any separate /home partition serves the same function.

Chao,** bogan**.

---

