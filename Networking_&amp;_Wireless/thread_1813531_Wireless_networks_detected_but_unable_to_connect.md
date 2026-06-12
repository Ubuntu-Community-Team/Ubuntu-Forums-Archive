---
title: "Wireless networks detected but unable to connect"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by Isthatyourfinal on 2011-07-27
New Ubuntu user here, and I'm having difficulties connecting to my router at home.
I've searched around the forum for a couple of hours now, to no avail. 
My router was originally not broadcasting ssid, so I turned broadcasting on. Now I can see the router, but when I enter a password (which I know is correct) nothing gets connected.
Can someone tell me where to start?

---

### Post by wildmanne39 on 2011-07-27
Hi, run these commands in a terminal please
```
sudo lshw -C network 
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
``` 
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by nm_geo on 2011-07-27
I would add
```

sudo iwlist scan
```

---

### Post by Isthatyourfinal on 2011-07-28
sudo lshw -C network
*-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:9f:6b:2d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half ip=192.168.1.103 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:f9000000-f901ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:7b:22:88
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.38-8-generic firmware=Lucent/Agere 9.48 link=yes multicast=yes wireless=IEEE 802.11b

---

### Post by Isthatyourfinal on 2011-07-28
lspci -nn | grep 0280

-nothing in return

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Perez"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:8C:B1:EE:0E   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-64 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:1128
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Isthatyourfinal on 2011-07-28
rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by Isthatyourfinal on 2011-07-28
sudo iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : Device or resource busy

---

### Post by wildmanne39 on 2011-07-28
Hi, try the command that returned no results like this and see what happens.
```
lspci -nn
```
From now on post all your information in one post, so we can keep things tidy, I believe I gave instructions in my post on how to post the results so it fits easy in to a post.
Thank you

---

### Post by Isthatyourfinal on 2011-07-28
Here's what I got with lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
02:01.1 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
02:03.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)

```

---

### Post by wildmanne39 on 2011-07-28
Hi, run this command please and post the results, we are narrowing down the problem.
```
sudo iwlist eth1 auth
```
```
lsmod
```
Thank you

---

### Post by Isthatyourfinal on 2011-07-29
sudo iwlist eth1 auth
```

eth1      Authentication capabilities :
        WPA
        CIPHER-TKIP
          Current Key management :
        PSK
          Current TKIP countermeasures : no
          Current Authentication algorithm :
        open



```lsmod
```

Module                  Size  Used by
binfmt_misc            13213  1 
michael_mic            12540  4 
orinoco_cs             12898  1 
orinoco                69899  1 orinoco_cs
cfg80211              156212  1 orinoco
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
radeon                900494  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 radeon
joydev                 17322  0 
ppdev                  12849  0 
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  1 orinoco_cs
drm                   180037  4 radeon,ttm,drm_kms_helper
dcdbas                 14054  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13184  1 radeon
psmouse                73312  0 
soundcore              12600  1 snd
parport_pc             32111  1 
serio_raw              12990  0 
video                  18951  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
floppy                 60032  0 
3c59x                  37398  0 

```

---

### Post by wildmanne39 on 2011-07-29
Hi, there is three things of interest.

1. Is your SSID Perez? The reason I ask is that your signal is weak so it could be connected to a neighbors router possibly, or it is an issue that we need to work on.

2. A lot of wireless cards that are your brand do not use wpa2 so you should disable that and see if you can connect then.

3. The orinoco driver your card is using does not work that well you would be better off with another driver that we can install.

I would check the first two suggestions that I mentioned and make sure you do not have  a wired connection hooked to your system and then you may be able to connect with your wireless. 

If you are already connected by a wire restart your system with out the wire to try to get your wireless to connect, I am pretty sure you do not have a wired connection this is just in case you do.

---

### Post by Isthatyourfinal on 2011-07-29
> 1. Is your SSID Perez? The reason I ask is that your signal is weak so it could be connected to a neighbors router possibly, or it is an issue that we need to work on.
That is a neighbors ssid. Mine is a different one. I'm not sure why it's trying to connect to that, or why it's showing up there.

> 2. A lot of wireless cards that are your brand do not use wpa2 so you should disable that and see if you can connect then.
by disabling that do you mean change my wireless security to wep, or something else? I would prefer to keep it as it is, but I can change it for testing purposes if need be.

> 3. The orinoco driver your card is using does not work that well you would be better off with another driver that we can install.

I'm happy to try that if I need to.

---

### Post by wildmanne39 on 2011-07-29
Hi, yes just for testing purposes with the wpa2.

First open the internet connections by clicking on the icon in the top right corner of the screen and click on edit connection then click on wireless connection and then edit and change your SSID to your SSID then save and close.

Here is a screenshot to help you.

Your wireless might connect then since the signal is so weak that could be keeping it from connecting.

---

### Post by Isthatyourfinal on 2011-07-29
When I open the Internet connections window, that ssid doesn't show up, but mine does. Is there a way to switch this from a command line?

---

### Post by wildmanne39 on 2011-07-29
Hi, you can use these commands to change the SSID at the terminal. 
```
sudo ifconfig eth1 down
```
```
sudo iwconfig eth1 "essid"
```&#8220;ESSID IN QUOTES&#8221; Your SSID goes where the essid is and it is in quotes.
```
sudo ifconfig up
```
Check this first: When you click on the internet icon in the top right corner do you see more then one wireless connection there? If not you probably have your connection hidden and you will have to unhide it to connect to it.

Here is a screenshot of my and it has three there but only one is mine, and I can not connect even though it is there because the signal is to weak.

---

