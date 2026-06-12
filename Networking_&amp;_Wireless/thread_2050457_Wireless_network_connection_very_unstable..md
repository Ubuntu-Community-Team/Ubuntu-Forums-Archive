---
title: "Wireless network connection very unstable."
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by daenth on 2012-08-30
I'm having troubles with my internet connection in ubuntu right now. Well, a few actually. 

First, when I compare my speeds between ubuntu and Windows, I'm getting double my link speed on Windows than on ubuntu.

Second, my internet connection periodically drops. Usually when I'm downloading a large file or putting a large load on my connection. I can't connect to the internet for a few seconds and then my connection just drops and tries to reconnect (which is does after a few seconds).

I've tried a few fixes I've found around Google but none of them have helped me. My wired connection is perfectly fine but my router is in a place where I can't use wired as my default connection. My wireless connection is the one with the problems.

sudo lshw -c network:
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:02:00.2
       logical name: eth0
       version: 0a
       serial: 20:6a:8a:84:f6:85
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
  *-network
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 44:6d:57:b0:8b:e1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-29-generic firmware=N/A ip=192.168.11.150 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:f0500000-f057ffff memory:dfa00000-dfa0ffff
```

---

### Post by daenth on 2012-08-31
Help?

---

### Post by ectechnologies on 2012-08-31
Hi,

What version of ubuntu are you on?

---

### Post by steeldriver on 2012-08-31
Have you tried the ath9k nohwcrypt option?

```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1
```This will set the parameter temporarily - if it helps with the disconnect problem post back and we can make it persistent via a /etc/modprobe.d conf file

---

### Post by daenth on 2012-08-31
I'm on 12.04.01 right now.

> **steeldriver said:**
> Have you tried the ath9k nohwcrypt option?

```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1
```This will set the parameter temporarily - if it helps with the disconnect problem post back and we can make it persistent via a /etc/modprobe.d conf file
I'll give this a shot.

---

### Post by daenth on 2012-08-31
> **steeldriver said:**
> Have you tried the ath9k nohwcrypt option?

```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1
```This will set the parameter temporarily - if it helps with the disconnect problem post back and we can make it persistent via a /etc/modprobe.d conf file

No go with that. A few minutes after I put that command in, the internet did it's normal crash. Space out for 10 seconds and disconnect.

---

### Post by ectechnologies on 2012-08-31
Have you checked additional drivers for wireless network adapter?

---

### Post by daenth on 2012-08-31
> **ectechnologies said:**
> Have you checked additional drivers for wireless network adapter?
Yeah, I usually check the additional drivers page right after installing ubuntu and I had nothing on the page. Checking again, there is still nothing there.

---

### Post by ectechnologies on 2012-08-31
Are you on a satellite provider like hughes net? If so, you might only be able to use a set amount of bandwidth.

---

### Post by daenth on 2012-08-31
> **ectechnologies said:**
> Are you on a satellite provider like hughes net? If so, you might only be able to use a set amount of bandwidth.

Running a fiber connection with no bandwidth caps and I'm usually getting 110 mbps download speeds, don't think that's the problem. 

Another note, because the weaker link speed, I have to have my computer closer to the router and right now I have a 130 mbps link speed. The connection can't handle anything near that load though. I've noticed I can keep the connection running forever without it disconnecting, for example, if I'm just typing something up with nothing downloading. When I'm downloading something, watching a video, or browsing websites with a lot of media, it'll disconnect after a few minutes.

---

### Post by ectechnologies on 2012-08-31
Try unplugging the router power from the back and leaving it out for 10 seconds, then plugging it back in. If you haven't already.

---

### Post by daenth on 2012-08-31
> **ectechnologies said:**
> Try unplugging the router power from the back and leaving it out for 10 seconds, then plugging it back in. If you haven't already.

I've tried this multiple times with no success. This problem has affected every WiFi connection I've used, so I think it's a problem with my network card and not the routers.

---

### Post by ectechnologies on 2012-08-31
Try this, these 2 will take down and put up all network interfaces:

Press Ctrl-Alt-T

sudo ifdown -a
sudo ifup -a
Let me know how it works.

---

### Post by daenth on 2012-08-31
> **ectechnologies said:**
> Try this, these 2 will take down and put up all network interfaces:

Press Ctrl-Alt-T

sudo ifdown -a
sudo ifup -a
Let me know how it works.

Still suffering from disconnecting problems. =/

---

### Post by ectechnologies on 2012-08-31
It is seeming more and more like a provider issue. 

I've done all i know how to do, I apologize. If everything else you do fails, I would contact your provider and see if they are having any issues.

I'm going off now, sorry I couldn't help.

---

### Post by daenth on 2012-08-31
> **ectechnologies said:**
> It is seeming more and more like a provider issue. 

I've done all i know how to do, I apologize. If everything else you do fails, I would contact your provider and see if they are having any issues.

I'm going off now, sorry I couldn't help.

Alright, well thanks for trying to help. It's a frustrating problem, even more so as I have to attend live, online sessions for school frequently. Can anyone else help me out?

---

### Post by steeldriver on 2012-08-31
A few more things you can try

1. look in dmesg to see if there are actually any driver errors being reported

```
dmesg | grep -e 'ath9k' -e '*interface*'
```where *interface *is your wireless interface (wlan0 or whatever)

2. use the wireless tools to see if there are any nearby routers using the same channel as yours and possibly interfering

```
nmcli dev wifi list
```or if you don't have nmcli,

```
sudo iwlist [*interface*] scan
```If there are, try editing your router config to use a different channel

---

### Post by daenth on 2012-08-31
> **steeldriver said:**
> A few more things you can try

1. look in dmesg to see if there are actually any driver errors being reported

```
dmesg | grep -e 'ath9k' -e '*interface*'
```where *interface *is your wireless interface (wlan0 or whatever)

2. use the wireless tools to see if there are any nearby routers using the same channel as yours and possibly interfering

```
nmcli dev wifi list
```or if you don't have nmcli,

```
sudo iwlist [*interface*] scan
```If there are, try editing your router config to use a different channel

dmesg | grep -e 'ath9k' -e 'wlan0'
```
[   15.896779] ath9k 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.896804] ath9k 0000:03:00.0: setting latency timer to 64
[   16.036445] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.037436] Registered led device: ath9k-phy0
[   17.325814] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.330020] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.878678] wlan0: authenticate with 4c:e6:76:fa:18:d5 (try 1)
[   25.880176] wlan0: authenticated
[   25.906504] wlan0: associate with 4c:e6:76:fa:18:d5 (try 1)
[   25.908022] wlan0: RX AssocResp from 4c:e6:76:fa:18:d5 (capab=0x11 status=0 aid=2)
[   25.908026] wlan0: associated
[   25.911899] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   36.003382] wlan0: no IPv6 routers present
[  116.526860] wlan0: deauthenticating from 4c:e6:76:fa:18:d5 by local choice (reason=3)
[  120.487416] wlan0: authenticate with 4c:e6:76:fa:18:d5 (try 1)
[  120.488964] wlan0: authenticated
[  120.501692] wlan0: associate with 4c:e6:76:fa:18:d5 (try 1)
[  120.503262] wlan0: RX ReassocResp from 4c:e6:76:fa:18:d5 (capab=0x11 status=0 aid=2)
[  120.503272] wlan0: associated
[  131.432340] wlan0: no IPv6 routers present

```

I didn't find any channel interference with the second command.

---

### Post by steeldriver on 2012-08-31
Hmm... are you using WEP? I was just looking at this yesterday for another poster and there seem to be reports of a kernel regression bug related to WEP in the ath9k driver

If you *are* using WEP can you change to WPA? (WEP is strongly discouraged anyway because of poor security)

---

### Post by daenth on 2012-08-31
> **steeldriver said:**
> Hmm... are you using WEP? I was just looking at this yesterday for another poster and there seem to be reports of a kernel regression bug related to WEP in the ath9k driver

If you *are* using WEP can you change to WPA? (WEP is strongly discouraged anyway because of poor security)
Nope, I'm not running on WEP security.

---

### Post by daenth on 2012-09-01
Here's a little more information.

[IMG]http://i.imgur.com/H4NZM.png[/IMG]
My connection is the one on the very bottom. The TX power likes to jump anywhere from 10M to 120M and the signal quality is very, very low compared to every other connection. I am no more than 10-15 feet away from the router with nothing in between the computer and the router. The computer with the connection with 70% signal quality is identical to my computer in terms of location and has a AR9285 chip running Windows 7.

```
64 bytes from 192.168.11.1: icmp_req=1065 ttl=64 time=3.22 ms
64 bytes from 192.168.11.1: icmp_req=1066 ttl=64 time=1.25 ms
64 bytes from 192.168.11.1: icmp_req=1067 ttl=64 time=1.40 ms
64 bytes from 192.168.11.1: icmp_req=1068 ttl=64 time=3082 ms
64 bytes from 192.168.11.1: icmp_req=1069 ttl=64 time=2075 ms
64 bytes from 192.168.11.1: icmp_req=1070 ttl=64 time=1067 ms
64 bytes from 192.168.11.1: icmp_req=1071 ttl=64 time=59.2 ms
64 bytes from 192.168.11.1: icmp_req=1072 ttl=64 time=77.2 ms
64 bytes from 192.168.11.1: icmp_req=1073 ttl=64 time=20.6 ms
#Disconnecting from the network.
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
64 bytes from 192.168.11.1: icmp_req=1101 ttl=64 time=24.5 ms
64 bytes from 192.168.11.1: icmp_req=1102 ttl=64 time=1.82 ms
64 bytes from 192.168.11.1: icmp_req=1103 ttl=64 time=1.28 ms

```
This is what my pinging to the router looks like before it kicks me off or I disconnect.

```
64 bytes from 192.168.11.1: icmp_req=1186 ttl=64 time=1.33 ms
64 bytes from 192.168.11.1: icmp_req=1187 ttl=64 time=6.99 ms
64 bytes from 192.168.11.1: icmp_req=1188 ttl=64 time=123 ms
64 bytes from 192.168.11.1: icmp_req=1189 ttl=64 time=67.4 ms
64 bytes from 192.168.11.1: icmp_req=1190 ttl=64 time=18.9 ms
64 bytes from 192.168.11.1: icmp_req=1191 ttl=64 time=30.5 ms
64 bytes from 192.168.11.1: icmp_req=1192 ttl=64 time=96.5 ms
64 bytes from 192.168.11.1: icmp_req=1193 ttl=64 time=38.9 ms
64 bytes from 192.168.11.1: icmp_req=1194 ttl=64 time=2.68 ms

```
Another small skip I've noticed.

[IMG]http://i.imgur.com/Hgh95.png[/IMG]
Connection information.

---

### Post by daenth on 2012-09-01
Anything? :(

I tried installing the Windows driver for my network card and that didn't work for some reason so I switched it back to ath9k and the disconnecting problem is getting worse.

---

### Post by steeldriver on 2012-09-01
It seems odd that it is (apparently) negotiating the highest RX rate of the bunch when it has the lowest SNR

Can you set your router to 54Mb/s max (or disable 802.11n)? If so it would be interesting to see if it stabilizes. (Unlike the Intel drivers, I don't think ath9k has a 'disable n' parm on the driver side.)

---

### Post by daenth on 2012-09-01
> **steeldriver said:**
> It seems odd that it is (apparently) negotiating the highest RX rate of the bunch when it has the lowest SNR

Can you set your router to 54Mb/s max (or disable 802.11n)? If so it would be interesting to see if it stabilizes. (Unlike the Intel drivers, I don't think ath9k has a 'disable n' parm on the driver side.)

Results:
[IMG]http://i.imgur.com/pwjxI.png[/IMG]

Cursor is highlighting my connection.

---

### Post by steeldriver on 2012-09-01
is it still disconnecting though?

---

### Post by daenth on 2012-09-01
> **steeldriver said:**
> is it still disconnecting though?

No disconnects in the past 10 minutes, though, if I'm careful, I'm usually able to stay connected for an hour before being disconnected. I'll try putting a heavy load on the connection and seeing if it disconnects. One question though, if this works, is this the only way to fix it? I wouldn't mind if my connection was below 54 Mbps but it kind of sucks being gimped out of half your download speed.

---

### Post by daenth on 2012-09-01
45 minutes and no disconnect, so far so good. The connection speed has been maxed out the entire time as well. Though, on average, my pings to the router are getting 50-100ms latency. I'm still hoping this isn't the only solution as a halved connection isn't too nice.

---

### Post by gordintoronto on 2012-09-01
When you posted "a little more information," it's not clear what that was. Different routers? Different computers connected to your router? What program produced that output?

In any case, 35% signal strength for a router across the room is unreasonable. It really looks like a physical problem. Antenna?

Have you considered installing inSSIDer? [http://www.metageek.net/products/inssider/](http://www.metageek.net/products/inssider/)

I mostly use it for picking a channel, but it might help provide some clue about the problem.

---

### Post by daenth on 2012-09-01
> **gordintoronto said:**
> When you posted "a little more information," it's not clear what that was. Different routers? Different computers connected to your router? What program produced that output?

In any case, 35% signal strength for a router across the room is unreasonable. It really looks like a physical problem. Antenna?

Have you considered installing inSSIDer? [http://www.metageek.net/products/inssider/](http://www.metageek.net/products/inssider/)

I mostly use it for picking a channel, but it might help provide some clue about the problem.
Sorry about that, the picture is of my connection to the router as shown on the dd-wrt page. My connection is listed at the bottom. I'm using the network card that came with this laptop. I doubt it's physical, on Windows 7 I'm getting 2 to 3 times the signal quality and much higher link speeds.

---

### Post by BarryDocks on 2012-11-16
Having simlar problems with my new Satalie Pro C850
Did you have any success to solve this?

```
$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)

```

---

### Post by wildmanne39 on 2012-11-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

