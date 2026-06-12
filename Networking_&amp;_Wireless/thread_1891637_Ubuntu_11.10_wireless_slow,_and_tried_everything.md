---
title: "Ubuntu 11.10 wireless slow, and tried everything"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by mao3 on 2011-12-06
My wireless connection is really slow, I'm typing this up on Windows because I could not even get the webpage to load in Ubuntu.  I tried various different solutions from various different forums/threads, but nothing worked.  So I figured I would post my own thread here, hoping someone would have a solution I have not tried.

I have an HP dv6-6140us laptop.  These are the results of some commands I figured may be useful:

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 10:1f:74:11:b6:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4656 (4.6 KB)  TX bytes:4656 (4.6 KB)

wlan0     Link encap:Ethernet  HWaddr 40:2c:f4:02:b0:23  
          inet addr:128.61.126.176  Bcast:128.61.127.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4786824 (4.7 MB)  TX bytes:1007264 (1.0 MB)
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"GTwpa"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C0:62:6B:D5:3A:F4   
          Bit Rate=72.2 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0
```

sudo lshw -C network
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 10:1f:74:11:b6:ff
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 40:2c:f4:02:b0:23
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-13-generic firmware=N/A ip=128.61.126.176 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0200000-f0203fff
```

lsmod
```
Module                  Size  Used by
btusb                  18600  1 
bnep                   18436  2 
rfcomm                 47946  8 
bluetooth             166112  23 btusb,bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
vesafb                 13809  1 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
joydev                 17693  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
bcma                   20219  0 
arc4                   12529  2 
psmouse                73882  0 
serio_raw              13166  0 
snd_hda_codec_idt      70553  1 
k10temp                13166  0 
video                  19412  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
fglrx                2929009  102 
brcmsmac              631693  0 
snd_seq_midi           13324  0 
brcmutil               17837  1 brcmsmac
snd_rawmidi            30547  1 snd_seq_midi
mac80211              462092  1 brcmsmac
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              199587  2 brcmsmac,mac80211
crc_ccitt              12667  1 brcmsmac
wmi                    19256  1 hp_wmi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
input_polldev          13896  1 lis3lv02d
rts_pstor             445246  0 
i2c_piix4              13301  0 
snd                    68266  14 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
pata_atiixp            13164  0 
ahci                   26002  2 
xhci_hcd               82772  0 
r8169                  52788  0 
libahci                26861  1 ahci
```

If you took the time to look at this, I appreciate it.

---

### Post by bkratz on 2011-12-06
Perhaps this users work will help (using a different driver).

[http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170)

---

### Post by mao3 on 2011-12-07
:( No...that suggestion actually made my wireless connection stop working.  I have tried changing to different drivers, but most of those threads have to do with not being able to connect to the Internet at all.  My problem was not that I couldn't connect to the Internet (although it is now), but that it was really slow.  The suggestion in that thread was pretty much to install the lowest rated driver on Ubuntu Software Center, after uninstalling and blacklisting all other drivers , but I figured it may work anyway, and then lost the Internet.

---

### Post by carverj on 2011-12-08
[http://ubuntuforums.org/showthread.php?t=1424280&page=3](http://ubuntuforums.org/showthread.php?t=1424280&page=3)
might be useful to resolve although didn't read all the posts
Good luck

---

