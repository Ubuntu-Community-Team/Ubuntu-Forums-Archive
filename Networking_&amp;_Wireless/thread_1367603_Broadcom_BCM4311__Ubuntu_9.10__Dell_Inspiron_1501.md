---
title: "Broadcom BCM4311 / Ubuntu 9.10 / Dell Inspiron 1501"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by Beniamin on 2009-12-29
Hello all,

I really didn't want to have to ask for help; I've been hither and yon looking at [various tutorials]("http://www.ubuntu1501.com/2007/01/fixing-wifi-on-dell-1501.html") trying to figure out how to get my wireless card to work, but I'm still having no luck.  Really it shouldn't be this hard!  But hopefully you'll be able to help.

Currently under "Wireless Networks" it says "device not ready."

Here's my info:

lspci:
```
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:19:b9:51:85:40  
          inet addr:192.168.1.96  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe51:8540/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4159482 (4.1 MB)  TX bytes:934741 (934.7 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsmod:
```
Module                  Size  Used by
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10272  0 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_codec_idt      59844  1 
iptable_filter          3100  0 
dell_wmi                2564  0 
b43                   122136  0 
mac80211              181076  1 b43
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
cfg80211               93052  2 b43,mac80211
psmouse                56500  0 
serio_raw               5280  0 
ricoh_mmc               3676  0 
snd_seq_dummy           2656  0 
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
led_class               4096  2 b43,sdhci
k8temp                  4188  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
i2c_piix4               9932  0 
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
b44                    28684  0 
mii                     5212  1 b44
video                  19380  0 
output                  2780  1 video
ssb                    35300  2 b43,b44
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp
```

dmesg:
```
[    2.540736] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:51:85:40
[   19.938690] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   20.076592] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
```

sudo lshw -C network
```
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:51:85:40
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.96 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:92:3e:56:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

iwlist scan```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

```

uname -mr
```
2.6.31-16-generic i686
```

sudo /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
```

So, there's all that information.  Hopefully this will give you some idea of what I need to do.  So far in the tutorials I've tried, I haven't even gotten past building ndiswrapper.  So, if you can help, please let me know!  Thanks in advance.

---

### Post by evanjohan on 2009-12-29
I have the same problem. It allowed me to install the proprietary drivers when I was testing it out before the actual install and now I can't seem to find/install them to get my wireless to work (when it worked in the try before you install option before I install 9.10).

Help would be appreciated. 

I have the same system it appears and installed from an i386 disk.

---

### Post by focwiz on 2009-12-29
> **evanjohan said:**
> I have the same problem. It allowed me to install the proprietary drivers when I was testing it out before the actual install and now I can't seem to find/install them to get my wireless to work (when it worked in the try before you install option before I install 9.10).

Help would be appreciated. 

I have the same system it appears and installed from an i386 disk.

Have you followed these instructions...?
[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by PRC09 on 2009-12-29
Broadcom Links.....

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

And this....

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by evanjohan on 2009-12-29
The second link of the above post worked for me:

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

Thanks a lot. It's working now and my sister-in-law is now a Linux user!

---

### Post by PRC09 on 2009-12-29
Welcome Aboard....

---

### Post by Beniamin on 2009-12-29
That did the trick for me as well--many thanks!  Apparently I was trying to do it the hard way.

And now my mother is a Linux user!

---

### Post by PRC09 on 2009-12-29
Your welcome.I have a couple of Dells with the Broadcom cards so I am just relaying the links that I used.Glad it worked....

---

### Post by Project PWNED on 2009-12-29
> **Beniamin said:**
> That did the trick for me as well--many thanks!  Apparently I was trying to do it the hard way.

And now my mother is a Linux user!

Don't forget to setup /etc/network/interfaces so the wireless interface is setup automatically. This will save you phone calls from your mom about being unable to get online. My mom tried using Redhat 6 (back before Fedora..) a long time ago. I had her login with my account because my dad was on the other computer, she asked where Internet Explorer was and when she figured out this was totally different she just logged off and never used Linux ever again.

---

