---
title: "Wifi:  Very slow wifi, tried two fixes so far, no joy"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by Redflea on 2012-01-26
Really, really slow internet access on wifi...I've read around here and tried two popular fixes, neither worked for me.  Details below...

Ubuntu 10.4.03 LTS
Sony Vaio VPC CW290L
Atheros wifi

I've completed all the info gathering recommended on this page [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) to post a networking issue, see below.   

My problem is incredibly slow wifi:  [img]http://www.speedtest.net/result/1732720073.png[/img]
Ping: 20ms
Download: .06 Mbps
Upload: .16 Mbps

If I hover over the wifi icon at top of screen it shows strong connection: 80-90+ percent. Wifi connects up promptly, without issue.  

However, in actual use, internet is so slow as to be almost unusable. 

It's fine on wired.

Fine on wifi on all other devices in the house, and fine on this device on wifi when booted into Win 7. 

Tried the fix recommended for slow wifi when on battery in a post on this forum.  Placed file called "wireless" with below in etc/pm/power.d.  That seemed to help signal strength reported, but not connection speed/real world results.  

```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```


Also tried this below, did not help at all. 

```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```

Would really appreciate some assistance, this is making my laptop useless unless I'm tethered to ethernet. 

Thanks! 

System information: 

lspci:

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


lsusb
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 05ca:18b5 Ricoh Co., Ltd 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:be:c4:a4:31  
          inet addr:192.168.2.24  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:beff:fec4:a431/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1270804 (1.2 MB)  TX bytes:239427 (239.4 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2219 (2.2 KB)  TX bytes:2219 (2.2 KB)

wlan0     Link encap:Ethernet  HWaddr 78:dd:08:ca:39:4a  
          inet addr:192.168.2.23  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::7add:8ff:feca:394a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2900256 (2.9 MB)  TX bytes:2142325 (2.1 MB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"AP-2N"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:75:5A:A6:36   
          Bit Rate=486 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod
Module                  Size  Used by
ath9k                 306106  0 
aes_i586                7268  2 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
rfcomm                 33453  4 
sco                     7949  2 
bridge                 45646  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30656  16 rfcomm,bnep
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
vgastate                8961  1 vga16fb
nouveau               467048  0 
ttm                    49847  1 nouveau
drm_kms_helper         29329  1 nouveau
snd_hda_codec_realtek   203440  1 
drm                   163747  3 nouveau,ttm,drm_kms_helper
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm                70694  3 snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
btusb                  11053  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
i2c_algo_bit            5028  1 nouveau
uvcvideo               57438  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
mac80211              205434  1 ath9k
video                  17375  0 
ath                     7611  1 ath9k
snd                    54244  16 snd_hda_codec_realtek,snd_pcm_oss,snd_mixer_oss,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      7028  0 
output                  1871  1 video
sony_laptop            28248  0 
cfg80211              126528  3 ath9k,mac80211,ath
intel_agp              24375  0 
agpgart                31724  3 ttm,drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63677  0 
serio_raw               3978  0 
sdhci_pci               5470  0 
sdhci                  15494  1 sdhci_pci
led_class               2864  2 ath9k,sdhci
parport                32635  2 ppdev,lp
ohci1394               26950  0 
sky2                   40807  0 
ieee1394               81181  1 ohci1394
ahci                   32680  2 


sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 78:dd:08:ca:39:4a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.23 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:e7a00000-e7a0ffff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:24:be:c4:a4:31
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.2.24 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:e5220000-e5223fff ioport:a000(size=256) memory:e5200000-e521ffff(prefetchable)
 

iwlist scan wlan0
wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:7A:70:AF
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"AP-2N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000797ce27e
                    Extra: Last beacon: 11892ms ago
                    IE: Unknown: 000541502D324E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080A00000000000000000000000000000000000000
                    IE: Unknown: 3D1601080A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B0001031047001000000000000010000000C03F0E7A70AF102100074E65746765617210230008574E445233373030102400025631104200046E6F6E651054000800060050F204000110110008574E445233373030100800020086103C000103
          Cell 02 - Address: 00:26:75:5A:A6:36
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"AP-2N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000634e04ef9e
                    Extra: Last beacon: 4752ms ago
                    IE: Unknown: 000541502D324E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502001E127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706534720010D10
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A8800026755AA6361021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 03 - Address: 00:26:75:59:25:98
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"AP-2N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000634e43017f
                    Extra: Last beacon: 11928ms ago
                    IE: Unknown: 000541502D324E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040017127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706534720010D10
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A8800026755925981021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101

uname -mr
2.6.32-38-generic i686


sudo /ect/init.d/networking restart
2.6.32-38-generic i686
xxx@xxx:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
Ignoring unknown interface eth0=eth0.

---

### Post by Redflea on 2012-01-27
OK...I decided to upgrade the kernel...since I'm a Linux/Ubuntu noob, I needed a simple way.

Found this page:

[http://www.ramoonus.nl/2011/05/19/linux-kernel-2-6-39-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/05/19/linux-kernel-2-6-39-installation-guide-for-ubuntu-linux/)

Used that to upgrade the kernel to:

2.6.39-020639-generic

Rebooted, selected that kernel, and after a couple scary error message (have to boot up again and remember what they said) things booted fine and wifi internet is SCREAMING fast.  

Assuming nothing significant is borked w/the new kernel install, I AM HAPPY!  :) 

Any advice on an alternate 2.6.39-020639-generic kernel install process that might clean up error messages.

---

### Post by varunendra on 2012-01-27
..And we can't help without knowing what the error messages are.. :)

But if everything is working fine regardless of those messages, I think you should mark this thread as [Solved] now, and update this status on your other post in this thread: [http://ubuntuforums.org/showthread.php?p=11643062&postcount=8](http://ubuntuforums.org/showthread.php?p=11643062&postcount=8)

If the problem occurs again, I'd recommend to update that again (in a new post), and wait for praseodym's reply there, as he is one of the best guys for troubleshooting wireless issues.

..And if you are 'really' scared by those messages ;) please post them here so we could suggest if they could be ignored.


**_EDIT_:**
Nevermind.. I just realized you have already started a new thread about those messages: [http://ubuntuforums.org/showthread.php?t=1915829](http://ubuntuforums.org/showthread.php?t=1915829)

---

### Post by Redflea on 2012-01-27
> **varunendra said:**
> ..And we can't help without knowing what the error messages are.. :)

But if everything is working fine regardless of those messages, I think you should mark this thread as [Solved] now, and update this status on your other post in this thread: [http://ubuntuforums.org/showthread.php?p=11643062&postcount=8](http://ubuntuforums.org/showthread.php?p=11643062&postcount=8)

If the problem occurs again, I'd recommend to update that again (in a new post), and wait for praseodym's reply there, as he is one of the best guys for troubleshooting wireless issues.

..And if you are 'really' scared by those messages ;) please post them here so we could suggest if they could be ignored.


**_EDIT_:**
Nevermind.. I just realized you have already started a new thread about those messages: [http://ubuntuforums.org/showthread.php?t=1915829](http://ubuntuforums.org/showthread.php?t=1915829)

Yup...so no comments on my scary messages in the other thread?  ;-) 

Thanks for posting the link, I was coming back to add it and mark this solved.

---

### Post by varunendra on 2012-01-27
> **Redflea said:**
> Yup...so no comments on my scary messages in the other thread?  ;-)
..because I don't have much idea about the first message ("mdio-gpio already registered...") and the second one is harmless unless you have heating problems in the system.

So I was expecting maybe someone else with a better insight could pick up the question and maybe could offer a precise solution too. But a quick search suggests that it is perhaps a common (and harmless) error message with custom built kernels, and not many people are interested in answering or solving it. So I'm going to comment there whatever I could find about it.

---

### Post by Redflea on 2012-01-27
> **varunendra said:**
> ..because I don't have much idea about the first message ("mdio-gpio already registered...") and the second one is harmless unless you have heating problems in the system.

So I was expecting maybe someone else with a better insight could pick up the question and maybe could offer a precise solution too. But a quick search suggests that it is perhaps a common (and harmless) error message with custom built kernels, and not many people are interested in answering or solving it. So I'm going to comment there whatever I could find about it.

Thanks...that seems to match up with what I thought/hoped, based on the message content.  Internet still zooming...!! Happy.  :)

---

### Post by Redflea on 2012-02-01
Just dropping back by to note that: 

1. This kernel update has not caused any issues on my laptop.  Things are running great.

2. Previously I had thought that a separate patch to turn off wifi powersaving was also necessary to fix slow wifi on battery, but I just reinstalled ubuntu (due to some other unrelated issues) and only installed the kernel update and wifi is great in all situations, on and off power.  So it's all good!  :)

---

