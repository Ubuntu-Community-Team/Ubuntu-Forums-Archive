---
title: "Broadcom 4328 wireless help (wifi light on, no scan) on Karmic"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by fifth_rune on 2010-03-22
Ok, I'm about at the end of my rope.  I've tried everything from reinstalling my system to using the 'Broadcom STA' in restricted drivers (both before and after re-installing everything) to the ndiswrapper based solution found here: [WIFI fix]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851")

No matter what solution I try, the end result is usually the same: I'll get my wifi light to turn on, and my system will detect the wifi card, but I can't scan or connect to any networks via network manager.  Please please help.  I will post any terminal commands for information as requested if anyone is willing to help me.

---

### Post by bkratz on 2010-03-22
> **fifth_rune said:**
> Ok, I'm about at the end of my rope.  I've tried everything from reinstalling my system to using the 'Broadcom STA' in restricted drivers (both before and after re-installing everything) to the ndiswrapper based solution found here: [WIFI fix]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851")

No matter what solution I try, the end result is usually the same: I'll get my wifi light to turn on, and my system will detect the wifi card, but I can't scan or connect to any networks via network manager.  Please please help.  I will post any terminal commands for information as requested if anyone is willing to help me.

According to the official Broadcom site

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Your device is listed in the readme files as working with the STA driver with directions in the last 10-12 lines of the page. But obviously you have already gone that route with little success.

You might want to copy/paste the outputs from the following terminal commands (Applications>>Accessories>>Terminal) in case it gives someone a direction to follow:  By the way please use the "#" code tags since some listing might be long as are easier to read when done this way.

```
sudo lshw -C network
sudo iwlist scan
iwconfig
rfkill list
lsmod
```


The commands that start with lxxxx are actually lowercase "L's" in the above like lshw (LSHW) not "1's"
The commands that start with sudo will require your password which will not be echoed during typing-just press enter when done.

---

### Post by fifth_rune on 2010-03-23
Results for 'sudo lshw -C network'
```
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:6a:7f:53
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,09/20/2007, 4.170. latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:efdfc000-efdfffff memory:e0000000-e00fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:70:0f:4c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.100 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

Results for 'sudo iwlist scan'
```
lo        Interface doesn't support scanning.

wlan0     No scan results

vboxnet0  Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

Results for 'iwconfig'
```
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

eth0      no wireless extensions.

```

Results for 'rfkill list'
```
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Results for 'lsmod'
```

Module                  Size  Used by
b44                    28652  0 
ssb                    35524  1 b44
mii                     5212  1 b44
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetadp              7296  0 
vboxnetflt             14344  0 
vboxdrv               176360  2 vboxnetadp,vboxnetflt
snd_hda_codec_idt      59876  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
joydev                 10240  0 
ip_tables              11692  1 iptable_filter
ndiswrapper           184956  0 
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
x_tables               16544  1 ip_tables
lp                      8964  0 
parport                35340  2 ppdev,lp
dell_wmi                2564  0 
psmouse                56500  0 
dell_laptop             8128  0 
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  1 sdhci
serio_raw               5280  0 
dcdbas                  7292  1 dell_laptop
ricoh_mmc               3676  0 
reiserfs              229288  3 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
ieee1394               86596  1 ohci1394
video                  19380  1 i915
output                  2780  1 video
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp

```

---

### Post by chili555 on 2010-03-23
My esteemed colleague bkratz probably went to get coffee and I'm real anxious to get to 5000 posts, so please excuse my exuberance.
Please try:```
sudo rmmod -f dell-laptop
```Now does the wireless LED and key press seem to work correctly? Can you now scan and connect?

This is a known issue with ndiswrapper + wpa_supplicant + WPA network = no connection. Is your network WPA encrypted?

'Scuse me, bkratz, I will behave now!

---

### Post by bkratz on 2010-03-23
I really don't see anything wrong in the listings other than you can't connect! It just looks like it is waiting to associate with an A/P.

Perhaps one of the following would give us more useful info


ndiswrapper -l
uname -a
dmesg | grep -e ndis -e wlan

---

### Post by bkratz on 2010-03-23
> **chili555 said:**
> My esteemed colleague bkratz probably went to get coffee and I'm real anxious to get to 5000 posts, so please excuse my exuberance.
Please try:```
sudo rmmod -f dell-laptop
```Now does the wireless LED and key press seem to work correctly? Can you now scan and connect?

This is a known issue with ndiswrapper + wpa_supplicant + WPA network = no connection. Is your network WPA encrypted?

'Scuse me, bkratz, I will behave now!



i remember when you were trying to just get to 4000!  I did go to the gas station to get coffee!  No I appreciate the help, but the earlier commands did not show a problem with rfkill. Please don't go away, I really don't see anything wrong yet!


Send me one it will count!

---

### Post by chili555 on 2010-03-23
There is an issue with the implementation of *dell-laptop* and its ability to properly relate the meaning of key presses to the kernel; it may actually be an issue with *dell-ami* vs. *dell-laptop*. When I hear that someones wireless mysteriously doesn't work, and they talk about their light or LED and then mention Dell, I get suspicious. Often, but not always, unloading *dell-laptop* works wonders.

Thanks for your generosity and understanding!

---

### Post by bkratz on 2010-03-23
> **chili555 said:**
> There is an issue with the implementation of *dell-laptop* and its ability to properly relate the meaning of key presses to the kernel; it may actually be an issue with *dell-ami* vs. *dell-laptop*. When I hear that someones wireless mysteriously doesn't work, and they talk about their light or LED and then mention Dell, I get suspicious. Often, but not always, unloading *dell-laptop* works wonders.

Thanks for your generosity and understanding!



Almost there!  Try one more, I thought that would show up in rfkill list as a block or am I totally confused?

---

### Post by chili555 on 2010-03-23
> I thought that would show up in rfkill list as a block or am I totally confused?I think *dell-laptop* is totally confused. Sometimes it shows as blocked when it's not, so I suspect it may also show as not blocked when it is! You were quite correct, though, to suspect *rfkill*.

---

### Post by fifth_rune on 2010-03-23
sudo rmmod -f dell-laptop did not do anything, unfortunately

here are the results of other requested actions:

results of 'ndiswrapper -l'

```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)

```

results of 'uname -a'
```
Linux highwind 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

```

results of 'dmesg | grep -e ndis -e wlan'
```
[   13.216933] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   13.701066] ndiswrapper: driver bcmwl5 (Broadcom,09/20/2007, 4.170.25.12) loaded
[   13.701311] ndiswrapper 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.701398] ndiswrapper 0000:0c:00.0: setting latency timer to 64
[   13.716349] ndiswrapper: using IRQ 17
[   13.936743] wlan0: ethernet device 00:16:cf:6a:7f:53 using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
[   13.936788] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.939106] usbcore: registered new interface driver ndiswrapper
[   16.972135] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2998.995041] ndiswrapper 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 2998.995065] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 2998.995074] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xefdfc004)
[ 2998.995080] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2998.995089] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 2999.124491] ndiswrapper 0000:0c:00.0: PME# disabled
[ 2999.124497] ndiswrapper 0000:0c:00.0: PME# disabled
[ 3002.129729] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4050.779568] ndiswrapper 0000:0c:00.0: PME# disabled
[ 4050.779574] ndiswrapper 0000:0c:00.0: PME# disabled
[ 4053.618115] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6377.556843] ndiswrapper 0000:0c:00.0: PME# disabled
[ 6377.556849] ndiswrapper 0000:0c:00.0: PME# disabled
[ 6379.902584] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Also, thanks again for all your help so far.  I hope this gets fixed soon.

---

### Post by mcooke1 on 2010-03-24
I have this card on Dell Laptop (installed it recently as part of upgrading home network to be N, 5 GHz only). Installed Kubuntu 10.04 yesterday and installed bcmwl-kernel-source and the STA driver. But the Network Manager in KDE did not work with it so I installed WICD and it is now working fine. I must stress I am on a different OS than you but this worked for me.

---

### Post by bamboy89 on 2010-03-24
dear friends..

how about with my wi-fi device...? Broadcom BCM4311 802.11b/g WLAN. I used ubuntu 9.10. 
the problem is my wi-fi seems not work automatically after I turn on wi-fi button in on my laptop.

I think my wi-fi is not damaged, because I can used it when I run Ubuntu with Live-On CD..

your helped,please.... thx...

---

### Post by chili555 on 2010-03-24
> **bamboy89 said:**
> dear friends..

how about with my wi-fi device...? Broadcom BCM4311 802.11b/g WLAN. I used ubuntu 9.10. 
the problem is my wi-fi seems not work automatically after I turn on wi-fi button in on my laptop.

I think my wi-fi is not damaged, because I can used it when I run Ubuntu with Live-On CD..

your helped,please.... thx...[http://ubuntuforums.org/showthread.php?t=1189367&highlight=4311](http://ubuntuforums.org/showthread.php?t=1189367&highlight=4311)

---

### Post by fifth_rune on 2010-03-25
Bump.  Still need assistance, but appreciate all the help so far.

---

### Post by fifth_rune on 2010-03-26
Anybody else got any suggestions?

---

### Post by chili555 on 2010-03-26
After you read the link I gave you, what did you try? What is not working? Can you click the Network Manager icon and see networks?

---

### Post by fifth_rune on 2010-03-26
Unfortunately I am unable to follow the guide in the link you posted because of the other drivers I have installed/steps I have taken to try to remedy this.  I followed the guide linked in my first post.  Are there some commands I can use to undo those changes/reset my installations to default without reinstalling my OS?

---

### Post by chili555 on 2010-03-27
Is your network WPA protected? There is a known issue with Broadcom cards, ndiswrapper and wpa_supplicant.

---

### Post by fifth_rune on 2010-03-27
No, it is not WPA protected.  Isn't that beside the point though since no networks even show up on the Network Manager scan?  Just curious.

---

### Post by chili555 on 2010-03-27
Please let me see:```
lsmod | grep -e wl -e b43 -e ssb
rfkill list
```Thanks.

---

### Post by fifth_rune on 2010-03-28
> **chili555 said:**
> Please let me see:```
lsmod | grep -e wl -e b43 -e ssb
rfkill list
```Thanks.

```
david@highwind:~$ lsmod | grep -e wl -e b43 -e ssb
ssb                    35524  1 b44
wl                   1272936  0 
lib80211                6432  1 wl

```

```
david@highwind:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by chili555 on 2010-03-28
Earlier, you posted this:> configuration: broadcast=yes [COLOR="Red"]driver=ndiswrapper+bcmwl5 [/COLOR]driverversion=1.55+Broadcom,09/20/2007, 4.170. latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:efdfc000-efdfffff memory:e0000000-e00fffff(prefetchable)
However, your computer is loading the STA driver, called *wl*, also. Let's blacklist it and see if ndiswrapper takes over:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist wl
```Proofread, save and close gedit. Please let me see:```
ls /etc/modprobe.d | grep black
```

If ndiswrapper is working correctly, a reboot will get you going. Post back with your report, please.

---

### Post by fifth_rune on 2010-03-28
Ok, first reboot for some reason killed my network manager (did not load on startup).  Second reboot network manager reappeared but unfortunately scanning did not return.  Also my wired connection stopped working so I had to sudo modprobe b44 to get it back.  Here's the return for 'ls /etc/modprobe.d | grep black' (the result was the same before and after reboot):

```
blacklist
blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist.conf
blacklist.conf~
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf

```

---

### Post by chili555 on 2010-03-28
Please do:```
cat /etc/modprobe.d/blacklist
```In a separate terminal, do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Move any listings in *blacklist* to **blacklist.conf**, unless they are duplicates. Add a new line to **blacklist.conf**:```
blacklist wl
```Proofread carefully, twice, save and close gedit. Close the 'cat' terminal, as well.

Now do:```
sudo rm /etc/modprobe.d/blacklist
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
sudo su
echo b44 >> /etc/modules
exit
```The double arrows are very important, don't forget them.

Reboot with the ethernet cable detached and let us know if the wireless has improved.

---

### Post by fifth_rune on 2010-03-28
I copy/pasted the commands as you listed.  I noticed bcm43xx was blacklisted twice so I removed one of the duplicates.  All the other entries from 'blacklist' were already in 'blacklist.conf' so I just saved it and entered the rest of the commands.  After reboot, the wireless did not improve.  The same issue where network manager disappeared occurred again.  Upon a 2nd reboot, wireless was still not scanning but network manager was present.  Also, the wired connection no longer required 'sudo modprobe b44' to get it working.

---

### Post by chili555 on 2010-03-28
Perhaps ndiswrapper is not working correctly. Let's see:```
ndiswrapper -l
iwconfig
```Thanks.

---

### Post by fifth_rune on 2010-03-28
```
david@highwind:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)
david@highwind:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

david@highwind:~$ 

```

---

### Post by chili555 on 2010-03-28
With the ethernet cable detached, please do:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Any activity in Network Manager?

---

### Post by fifth_rune on 2010-03-28
> **chili555 said:**
> With the ethernet cable detached, please do:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Any activity in Network Manager?

No, it doesn't look like it.
```
david@highwind:~$ sudo ifconfig wlan0 up
david@highwind:~$ sudo iwlist wlan0 scan
wlan0     No scan results


```

---

### Post by fifth_rune on 2010-03-30
Bump

---

### Post by chili555 on 2010-03-30
I wonder if the kernel has anything useful to report:```
dmesg | grep -e ndis -e wlan
```Thanks.

---

### Post by fifth_rune on 2010-03-30
```
david@highwind:~$ dmesg | grep -e ndis -e wlan
[   11.402855] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   13.176303] ndiswrapper: driver bcmwl5 (Broadcom,09/20/2007, 4.170.25.12) loaded
[   13.176551] ndiswrapper 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.176637] ndiswrapper 0000:0c:00.0: setting latency timer to 64
[   13.191506] ndiswrapper: using IRQ 17
[   13.408739] wlan0: ethernet device 00:16:cf:6a:7f:53 using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
[   13.408785] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.410882] usbcore: registered new interface driver ndiswrapper
[   16.470514] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   89.962288] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1472.094982] ndiswrapper 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 1472.095006] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 1472.095015] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xefdfc004)
[ 1472.095022] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1472.095030] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 1472.212320] ndiswrapper 0000:0c:00.0: PME# disabled
[ 1472.212326] ndiswrapper 0000:0c:00.0: PME# disabled
[ 1475.248508] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1711.731082] ndiswrapper 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 1711.731106] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 1711.731115] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xefdfc004)
[ 1711.731122] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1711.731131] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 1711.868823] ndiswrapper 0000:0c:00.0: PME# disabled
[ 1711.868830] ndiswrapper 0000:0c:00.0: PME# disabled
[ 1714.837452] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2060.071056] ndiswrapper 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 2060.071080] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 2060.071089] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xefdfc004)
[ 2060.071095] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2060.071104] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 2060.208374] ndiswrapper 0000:0c:00.0: PME# disabled
[ 2060.208381] ndiswrapper 0000:0c:00.0: PME# disabled
[ 2063.192344] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2681.683115] ndiswrapper 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 2681.683139] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 2681.683148] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xefdfc004)
[ 2681.683155] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2681.683164] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 2681.823352] ndiswrapper 0000:0c:00.0: PME# disabled
[ 2681.823361] ndiswrapper 0000:0c:00.0: PME# disabled
[ 2684.875693] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[37891.872185] ndiswrapper 0000:0c:00.0: PME# disabled
[37891.872192] ndiswrapper 0000:0c:00.0: PME# disabled
[37908.184193] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[37923.645974] ndiswrapper 0000:0c:00.0: PME# disabled
[37923.645980] ndiswrapper 0000:0c:00.0: PME# disabled
[37924.836245] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[38595.299009] ndiswrapper 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[38595.299033] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[38595.299042] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xefdfc004)
[38595.299048] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[38595.299057] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[38595.417251] ndiswrapper 0000:0c:00.0: PME# disabled
[38595.417257] ndiswrapper 0000:0c:00.0: PME# disabled
[38598.453420] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[51195.576328] ndiswrapper 0000:0c:00.0: PME# disabled
[51195.576335] ndiswrapper 0000:0c:00.0: PME# disabled
[51196.968312] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by chili555 on 2010-03-30
> ndiswrapper 0000:0c:00.0: PME# disabledThat can't be good. I suspect it may be our old pal *ssb*. Please detach the ethernet cable and try:```
sudo rmmod -f ndiswrapper
sudo rmmod -f ssb
sudo modprobe ndiswrapper
```Is there any improvement? If so, we will have to work out how to unload *ssb* for wireless, yet load it for ethernet.

---

### Post by fifth_rune on 2010-03-31
Tried all the commands, got this error on disabling of ssb

```
david@highwind:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': Resource temporarily unavailable
```

Continued onward, no progress.  After all this, with the ethernet cable detached, re-entered 'dmesg | grep -e ndis -e wlan'

```
david@highwind:~$ dmesg | grep -e ndis -e wlan
[   11.402855] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   13.176303] ndiswrapper: driver bcmwl5 (Broadcom,09/20/2007, 4.170.25.12) loaded
[   13.176551] ndiswrapper 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.176637] ndiswrapper 0000:0c:00.0: setting latency timer to 64
[   13.191506] ndiswrapper: using IRQ 17
[   13.408739] wlan0: ethernet device 00:16:cf:6a:7f:53 using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
[   13.408785] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.410882] usbcore: registered new interface driver ndiswrapper
[   16.470514] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   89.962288] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1472.094982] ndiswrapper 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 1472.095006] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 1472.095015] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xefdfc004)
[ 1472.095022] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1472.095030] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 1472.212320] ndiswrapper 0000:0c:00.0: PME# disabled
[ 1472.212326] ndiswrapper 0000:0c:00.0: PME# disabled
[ 1475.248508] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1711.731082] ndiswrapper 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 1711.731106] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 1711.731115] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xefdfc004)
[ 1711.731122] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1711.731131] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 1711.868823] ndiswrapper 0000:0c:00.0: PME# disabled
[ 1711.868830] ndiswrapper 0000:0c:00.0: PME# disabled
[ 1714.837452] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2060.071056] ndiswrapper 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 2060.071080] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 2060.071089] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xefdfc004)
[ 2060.071095] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2060.071104] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 2060.208374] ndiswrapper 0000:0c:00.0: PME# disabled
[ 2060.208381] ndiswrapper 0000:0c:00.0: PME# disabled
[ 2063.192344] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2681.683115] ndiswrapper 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 2681.683139] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 2681.683148] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xefdfc004)
[ 2681.683155] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2681.683164] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 2681.823352] ndiswrapper 0000:0c:00.0: PME# disabled
[ 2681.823361] ndiswrapper 0000:0c:00.0: PME# disabled
[ 2684.875693] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[37891.872185] ndiswrapper 0000:0c:00.0: PME# disabled
[37891.872192] ndiswrapper 0000:0c:00.0: PME# disabled
[37908.184193] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[37923.645974] ndiswrapper 0000:0c:00.0: PME# disabled
[37923.645980] ndiswrapper 0000:0c:00.0: PME# disabled
[37924.836245] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[38595.299009] ndiswrapper 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[38595.299033] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[38595.299042] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xefdfc004)
[38595.299048] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[38595.299057] ndiswrapper 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[38595.417251] ndiswrapper 0000:0c:00.0: PME# disabled
[38595.417257] ndiswrapper 0000:0c:00.0: PME# disabled
[38598.453420] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[51195.576328] ndiswrapper 0000:0c:00.0: PME# disabled
[51195.576335] ndiswrapper 0000:0c:00.0: PME# disabled
[51196.968312] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[54897.665440] ndiswrapper 0000:0c:00.0: PME# disabled
[54897.665446] ndiswrapper 0000:0c:00.0: PME# disabled
[54898.885329] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[55224.088382] ndiswrapper: device wlan0 removed
[55224.088410] ndiswrapper 0000:0c:00.0: PCI INT A disabled
[55224.088614] usbcore: deregistering interface driver ndiswrapper
[55224.323839] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[55224.481026] ndiswrapper: driver bcmwl5 (Broadcom,09/20/2007, 4.170.25.12) loaded
[55224.481546] ndiswrapper 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[55224.481675] ndiswrapper 0000:0c:00.0: setting latency timer to 64
[55224.498122] ndiswrapper: using IRQ 17
[55224.717684] wlan0: ethernet device 00:16:cf:6a:7f:53 using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
[55224.717749] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[55224.719911] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[55224.720634] usbcore: registered new interface driver ndiswrapper
[55224.951530] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[55225.893429] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[55246.056419] ndiswrapper: device wlan0 removed
[55246.056445] ndiswrapper 0000:0c:00.0: PCI INT A disabled
[55246.056667] usbcore: deregistering interface driver ndiswrapper
[55246.160341] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[55246.173443] ndiswrapper: driver bcmwl5 (Broadcom,09/20/2007, 4.170.25.12) loaded
[55246.173990] ndiswrapper 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[55246.174120] ndiswrapper 0000:0c:00.0: setting latency timer to 64
[55246.191649] ndiswrapper: using IRQ 17
[55246.409699] wlan0: ethernet device 00:16:cf:6a:7f:53 using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
[55246.409765] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[55246.410142] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[55246.413267] usbcore: registered new interface driver ndiswrapper
[55246.444690] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[55247.469461] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[55277.585472] ndiswrapper: device wlan0 removed
[55277.585501] ndiswrapper 0000:0c:00.0: PCI INT A disabled
[55277.585728] usbcore: deregistering interface driver ndiswrapper
[55277.689510] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[55277.702137] ndiswrapper: driver bcmwl5 (Broadcom,09/20/2007, 4.170.25.12) loaded
[55277.702582] ndiswrapper 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[55277.702724] ndiswrapper 0000:0c:00.0: setting latency timer to 64
[55277.720819] ndiswrapper: using IRQ 17
[55277.942751] wlan0: ethernet device 00:16:cf:6a:7f:53 using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
[55277.942825] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[55277.944181] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[55277.948518] usbcore: registered new interface driver ndiswrapper
[55277.966080] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[55279.002417] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Also please note that the ethernet cable still worked even though I did not do 'sudo modprobe ssb' or 'b44'

---

### Post by chili555 on 2010-03-31
Your ethernet connection is using *ssb* so that's why the system is reluctant to unload it. Adverse interference between *ssb* and ndiswrapper is a known issue. Google will produce dozens of examples searching for "ssb ndiswrapper."

I noticed that previously, you had the module *wl* loaded and we blacklisted it. I wonder if your wireless works if you do:```
sudo rmmod -f ndiswrapper
sudo modprobe wl
```You will have to detach the ethernet cable for Network Manager to switch to wireless. If it works, we can remove ndiswrapper and un-blacklist *wl*.

---

### Post by fifth_rune on 2010-04-01
Sigh, it didn't work.  This is getting depressing.

---

### Post by fifth_rune on 2010-04-03
Alright, last try.  Is there anything else I can do to figure this out?  Thanks again for all your help Chili, and everyone else as well.

---

