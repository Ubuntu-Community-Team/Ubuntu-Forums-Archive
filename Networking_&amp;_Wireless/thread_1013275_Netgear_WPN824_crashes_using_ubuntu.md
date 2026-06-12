---
title: "Netgear WPN824 crashes using ubuntu"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by Col. Mustard on 2008-12-16
Hello all, I have been dealing with this intermittent,but annoying issue for quite a while now. I have searched and searched, googled my brains out, and searched through dozens of pages on ubuntuforums about my issue, and can't seem to find anything sharing my problem. First, I will explain the issue, then I will detail all of my hardware info and do my best with anything that might help figure it out.

The problem seems to only be reproducible when I am browsing the web (can't find any correlation with a particular browser) and visiting multiple sites and performing downloads for longer periods of time. For example, looking for wallpapers and icon themes the other night, I was visiting many web sites and downloading files from them, roughly 20minutes into it my internet connection stopped completely. NetworkManager still shows me as connected, and with signal strength normal, but I cannot access the internet in any way. If i disconnect and attempt to re connect, or if I attempt to connect with another device (iPod touch/other computer), the network is shown as "up", but can not be connected to. The only solution is to unplug the router, and plug it back in. After a minute, my connection is good as new, and the cycle will start over again. 

However, if I am only lightly using the internet, or casually browsing without performing any downloads, I cannot get the router to crash with any particular pattern. sometimes it will stay up for days on end, but as soon as I put a heavy load on the router it will usually crash within 20minutes. The strange thing is, it doesn't do it when downloading large files or torrents... it seems to be specific to downloading a large number of smaller files. Also, when using windows Vista or xp this problem does not occur. I can download any number of files from whichever sites I please, and there have been times where the network stays up for nearly a week without a single crash. Unless I use ubuntu... Then I can pretty reliably get it to go down. Thanks for reading, and I greatly appreciate any help you may be able to offer. This has been driving me nuts >.< Below is all the info I can think of that may help:


```
**Ubuntu 8.10 2.6.27-9-generic i686**
**Netgear WPN824 Firmware V2.0.15_1.0.11**


**lspci:** 
04:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

**iwconfig:**
wlan0     IEEE 802.11bg  ESSID:"HOME"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:14:88:FE   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=51/100  Signal level:-61 dBm  Noise level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**ifconfig:**
wlan0     Link encap:Ethernet  HWaddr 00:1c:df:4c:c1:4f  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28488923 (28.4 MB)  TX bytes:615185 (615.1 KB)

**lsmod | grep b43:**
b43                   131356  0 
rfkill                 17176  3 rfkill_input,b43
mac80211              216820  1 b43
led_class              12164  1 b43
input_polldev          11912  1 b43
ssb                    40580  1 b43


**dmesg | grep b43:**
[    4.246498] b43-pci-bridge 0000:04:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   14.923133] b43-phy0: Broadcom 4318 WLAN found
[   28.241384] input: b43-phy0 as /devices/virtual/input/input9
[   28.320528] firmware: requesting b43/ucode5.fw
[   28.443370] firmware: requesting b43/pcm5.fw
[   28.460364] firmware: requesting b43/b0g0initvals5.fw
[   28.471187] firmware: requesting b43/b0g0bsinitvals5.fw
[   28.588518] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   28.704896] Registered led device: b43-phy0::tx
[   28.705426] Registered led device: b43-phy0::rx
[   28.705900] Registered led device: b43-phy0::radio

**sudo lshw -C network:**
 *-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:04:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:4c:c1:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.5 multicast=yes wireless=IEEE
```

---

### Post by Col. Mustard on 2009-01-09
I have an updated diagnosis, it seems this problem occurs regardless of what wireless adapter I have hooked to my computer, and also regardless of what I'm doing online. If I'm using bandwidth for 30+mins, it seems to 'paralyze' the network. (I.E. The network is still visible from other computers and iPods, but cannot be connected to until the router is reset.)

 This issue **ONLY** happens in Linux, as I already explained, I can use windows with the exact same hardware for days if not weeks without a hitch. Linux gives me roughly 30 mins (depending on bandwidth activity it seems). I know I made a long post and went into detail, but if anyone has any ideas... Please let me know. This is driving me nuts, and I'd love to hear someone else's thoughts on the issue. Thanks

---

### Post by barley342 on 2009-01-25
I also have this router [NETGEAR WPN824] and have had issues with it crashing while utilizing my dual booted ubuntu laptop. The airport extreme card is a Broadcom BCM43xx.

One of the fine print items in the description portion of the routers settings (when you log on to your router) states that if you use the AUTO 108MBPS feature that you may only use channel 6. This left me wondering if you need to set your router to the "B AND G" setting, therefore allowing the router to utilize other channels. Keep in mind that this was one of the MIMO 108 xtended range routers and has "xtended" features that need a special card to take advantage of the "108mbps." 

Have you tried doing this and/or have you found another workaround for this issue yet? Hope you can reply.

For those of you that have never logged onto your own router look up your router manufacturer online and follow their online directions. Usually you use your browser and type in a url such as 192.168.1.1 or something of that sort. 

-Barley342-

---

### Post by dtakamori on 2009-06-21
fwiw I fixed this on my Dell Inspiron 700m laptop by running

> iwconfig eth1 rate 2M auto


which limits my bandwidth to the router to 2Mbps but keeps the router from crashing.  

I don't have this being run automatically yet.  I did put it into a shellscript so I don't have to remember the details, tho.

---

### Post by fearciuin on 2010-03-13
Hi guys, thanks for this!  I have a Belkin Wireless G router and was experiencing the same problems - but limiting the rate has resolved it!

---

