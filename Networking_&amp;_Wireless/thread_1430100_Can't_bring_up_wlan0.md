---
title: "Can't bring up wlan0"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by lost09 on 2010-03-14
Here's to adding to the wealth of wireless troubleshooting threads; hopefully this will at least be of use to others. My ethernet connection works perfectly, but I can't connect to wireless to save my life. 

First I scanned for networks in the area:
```
$ iwlist wlan0 scan
wlan0     Failed to read scan data : Network is down
```

So I tried bring it up:
```
$ ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132
```

After several hours of searching, the only "solution" I've found is the following set of commands:
```
rmmod ath9k
rfkill block all
rfkill unblock all
modprobe ath9k
rfkill unblock all
```

But I didn't even get past the first of them:
```
$ rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
```

Regardless, the unanimous opinion seems to be that this is both inelegant and temporary. Does any one have any insight into what the problem is, and more importantly, how to fix it? 

Much appreciated,
l

---

### Post by l4zy on 2010-03-15
Are you shure that module for you ath.. is loaded ? 

lsmod shows ath9k module ?

It should work without any problems.

Linux media-box 2.6.31-20-generic / ath9k i havent had any problems.

---

### Post by lost09 on 2010-03-16
Here's the output of lsmod:
```
$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
pcmcia                 36808  0 
arc4                    1660  2 
ecb                     2524  2 
iptable_filter          3100  0 
snd_atiixp_modem       11940  5 
snd_seq_dummy           2656  0 
snd_atiixp             15720  2 
snd_ac97_codec        101216  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
psmouse                56500  0 
ip_tables              11692  1 iptable_filter
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
snd_pcm                75296  6 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            28576  0 
x_tables               16544  1 ip_tables
serio_raw               5280  0 
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
ath5k                 124772  0 
mac80211              181140  1 ath5k
led_class               4096  1 ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  23 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_atiixp_modem,snd_atiixp,snd_pcm
i2c_piix4               9932  0 
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
radeon                636000  2 
ttm                    36212  1 radeon
drm                   160032  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp

```

The closest I see is "ath", but I confess I don't really know what this is (or what "aht9k" is, for that matter). Please advise.

---

### Post by lost09 on 2010-03-16
Ok, I've made some progress. I found the correct driver with lshw:
```
$ lshw
           *-network:0
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: wmaster0
                version: 01
                serial: 00:11:f5:63:ce:2f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes [COLOR="Red"]driver=ath5k[/COLOR] latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:c0200000-c020ffff
```

Then I retried the above "solution" with the correct driver:
```
rmmod ath5k
rfkill block all
rfkill unblock all
modprobe ath5k
rfkill unblock all
```

This seemed to have an effect, as a scan now returns the available wireless networks. However, I cannot get an IP address:
```
$ dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5217
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:f5:63:ce:2f
Sending on   LPF/wlan0/00:11:f5:63:ce:2f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


Has anyone experienced a similar problem?

---

### Post by aeiah on 2010-03-16
you could try using the madwifi drivers instead (ath_pci)

be sure to blacklist the ath5k during testing, and unblacklist ath_pci (or install madwifi if need be), of course.

madwifi changed into ath5k which got put in the kernel. the code is streamlined and better and blah blah blah. sometimes it still doesnt work though, so try the older stuff.

---

### Post by lost09 on 2010-03-16
Alright, I tried blacklisting ath5k and switching to madwifi. But installation of the madwifi-source fails, claiming that I need to add contrib and non-free archives. I was trying to follow steps here: [http://wiki.debian.org/WiFi/ath_pci](http://wiki.debian.org/WiFi/ath_pci)

But aptitude update gives a 404 on both the Lenny and Etch repositories. To make matters worse, no ath drivers are to be found on the system anymore, even after unblacklisting. :(

Anyone? Anyone?

---

### Post by lost09 on 2010-03-16
Here's some more info; I seem to be farther away from a solution than before. The system no longer recognizes  wlan0 at all:
```
$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
```

And lshw reveals that what was previously my wireless interface is now unclaimed:
```
$ lshw -C network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
       resources: memory:c0200000-c020ffff
```

I'm inching closer and closer to desperate here.

---

### Post by lost09 on 2010-03-16
Found one step towards a fix, which should have been obvious. For some reason, ndiswrapper wasn't installed. After installing it, I retried a scan:
```
$ iwlist wlan0 scan
wlan0     No scan results
```

Now, I know there are at least 7 or 8 wireless networks in the area, so why am I unable to pick up any?

---

### Post by draperdt on 2010-03-16
Your card seems to take the ath5k driver. 

I think ultimately you need madwifi-ng, ath5k, mac80211 stack, wext or wpa-supplicant if you need wpa connectivity. 

I would say start clean slate. That is uninstall every driver you think you might have tried or blacklist them.

I personally issue "airdriver-ng installed" to get the info on currently installed wireless drivers. There are a lot of ways to get that info.

---

### Post by lost09 on 2010-03-16
The ath5k driver seems to be functioning again after installing ndiswrapper:
```
$ lshw -C network
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wmaster0
       version: 01
       serial: 00:11:f5:63:ce:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=ath5k[/COLOR] latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:c0200000-c020ffff
```

But unlike earlier, a scan doesn't return any results, even after the rmmod business. Someone, please?

---

### Post by draperdt on 2010-03-16
[http://ubuntuforums.org/showthread.php?t=982808......This](http://ubuntuforums.org/showthread.php?t=982808......This)

That link has everything you need. You should read that thread first.

---

### Post by lost09 on 2010-03-16
First off, thanks for the response, draperdt. Unfortunately, I'm having trouble installing the necessary modules:
```
$ sudo aptitude install linux-backports-modules-intrepid-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
[COLOR="Red"]Couldn't find any package whose name or description matched "linux-backports-modules-intrepid-generic"
Couldn't find any package whose name or description matched "linux-backports-modules-intrepid-generic"
No packages will be installed, upgraded, or removed.[/COLOR]
0 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

I double-checked that the backports repositories are enabled, so do you know why I'm unable to locate the modules? Thanks in advance!

---

### Post by lost09 on 2010-03-16
Whoops, momentary stupidity on my part... I'm using karmic, so I retried the previous with karmic instead of intrepid. It installed successfully. Once again I'm able to see available wireless networks with iwlist, and although I can set the essid, I'm still unable to get an ip address.

Here's the current state of wlan0:
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"MyNetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

But dhclient returns no offers:
```
$ dhclient wlan0
Listening on LPF/wlan0/00:11:f5:63:ce:2f
Sending on   LPF/wlan0/00:11:f5:63:ce:2f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
...
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

So, back to the previous question. Why can't I get an IP?

---

### Post by lost09 on 2010-03-18
Well, this is interesting; for some reason, iwlist wlan0 scan no longer returns any results. I've tried rebooting, restarting the network, and bringing wlan0 down and back up, and nothing seems to have an effect. 

However, dmesg yields some telling (and unsettling) info:
```
$ dmesg
[   18.034826] ath: EEPROM regdomain: 0x64
[   18.034832] ath: EEPROM indicates we should expect a direct regpair map
[   18.034839] ath: Country alpha2 being used: 00
[   18.034841] ath: Regpair used: 0x64
[   18.130721] phy0: Selected rate control algorithm 'minstrel'
[   18.131639] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   19.510777] ppdev: user-space parallel port driver
[   19.567728] [drm] Setting GART location based on new memory map
[   19.568599] [drm] Loading R300 Microcode
[   19.568647] [drm] Num pipes: 2
[   19.568656] [drm] writeback test succeeded in 1 usecs
[   19.796522] ADDRCONF(NETDEV_UP): wlan0: [COLOR="Red"]link is not ready[/COLOR]
[   25.477099] eth0: link down
[   25.478236] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   83.594684] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  125.451053] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  125.451767] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  135.480075] eth0: no IPv6 routers present
[  143.123954] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  143.201314] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  153.340083] eth0: no IPv6 routers present
[  222.766235] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  222.766242] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  222.766246] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[  244.808457] ath5k 0000:02:04.0: PCI INT A disabled
[  261.065950] ath5k 0000:02:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  261.066056] ath5k 0000:02:04.0: registered as 'phy1'
[  261.664800] ath: EEPROM regdomain: 0x64
[  261.664806] ath: EEPROM indicates we should expect a direct regpair map
[  261.664813] ath: Country alpha2 being used: 00
[  261.664816] ath: Regpair used: 0x64
[  261.667042] phy1: Selected rate control algorithm 'minstrel'
[  261.667906] ath5k phy1: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[  284.796408] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Can anyone explain why the link is "not ready"?

---

### Post by lost09 on 2010-03-18
Minor update: I reinstalled ndiswrapper-utils-1.9 and ndiswrapper-common. iwlist wlan0 scan once again returns the list of available networks. However, dmesg still claims that ath0 is "not ready", and strangely, ndiswrapper -l returns no results. :confused:

---

### Post by silencej on 2010-03-19
hello~
I recommend that you should run iwlist scan with sudo:
```
sudo iwlist <yourWirelessInterface> scan
```

I am now also having "No dhpcoffers" problem. But when i use Wicd gui, the wireless works again.

---

### Post by lost09 on 2010-03-20
Sometimes running with sudo brings up results, and other times not. So far I can't determine any pattern, but it seems to stop turning up results after an arbitrary period of time. I suspect this is indicative of the core problem (but I have no idea what that is). Anyone had any luck with this?

---

