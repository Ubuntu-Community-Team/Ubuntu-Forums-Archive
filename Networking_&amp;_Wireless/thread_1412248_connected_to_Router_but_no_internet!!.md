---
title: "connected to Router but no internet?!?!?"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by williamirvine67 on 2010-02-21
Hi all,

just installed Ubuntu Netbook remix on my acer aspire one, 
and come across a problem Ive never faced before. Im able to Connect to my router (and access it through the internal ip address) but as soon as i try access anything outside of my network  there is nothing! 
This i found odd as first i thought it might have just been my Routers problem, but seeing as all my other computers were connected to it with no problems (wired and wireless) I quickly traced the problem back to the laptop. 

After this i decided to see if after a simple update would fix the problem. so i connected it up through the Ethernet port... once again it connects to the router... but no internet! 

I have tried everything in my knowledge, but with no success!
please help me put the 'Net' back in my 'Netbook'... other wise its just a book... and we know how boring they are!

Any suggestions would be much appreciated 

Thanks in advance, William

---

### Post by northd_tech on 2010-02-21
To determine what kind of hardware you are running, can you post the results when you run these commands in a terminal?

```
lspci 

lsusb

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```

---

### Post by williamirvine67 on 2010-02-21
> **northd_tech said:**
> To determine what kind of hardware you are running, can you post the results when you run these commands in a terminal?

```
lspci 

lsusb

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```

sure thing.

results

```

william@William-NetBook:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01) 
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)


william@William-NetBook:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera 

william@William-NetBook:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat 
usb_storage            52544  1 
bridge                 47952  0 
stp                     2272  1 bridge 
bnep                   12060  0 
btusb                  11856  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               7200  1 snd_hda_codec 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
ip_tables              11692  1 iptable_filter 
arc4                    1660  2 
snd_seq_midi            6432  0 
x_tables               16544  1 ip_tables 
ecb                     2524  2 
joydev                 10272  0 
snd_rawmidi            22208  1 snd_seq_midi 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi 
ath5k                 124260  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
lp                      8964  0 
uvcvideo               59080  0 
mac80211              181236  1 ath5k 
snd_timer              22276  2 snd_pcm,snd_seq 
ath                     8060  1 ath5k 
videodev               36736  1 uvcvideo 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
psmouse                56180  0 
v4l1_compat            14496  2 uvcvideo,videodev 
parport                35340  2 ppdev,lp 
cfg80211               93052  3 ath5k,mac80211,ath 
led_class               4096  1 ath5k 
serio_raw               5280  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore               7264  1 snd 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm 
fbcon                  36640  72 
tileblit                2460  1 fbcon 
font                    8124  1 fbcon 
bitblit                 5372  1 fbcon 
softcursor              1756  1 bitblit 
atl1e                  31824  0 
i915                  221064  3 
drm                   159584  3 i915 
i2c_algo_bit            5760  1 i915 
video                  19380  1 i915 
output                  2780  1 video 
intel_agp              27484  2 i915 
agpgart                34988  2 drm,intel_agp 

william@William-NetBook:~$ uname -a 
Linux William-NetBook 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux 

william@William-NetBook:~$ sudo lshw -c network 
[sudo] password for william: 
  *-network               
       description: Wireless interface 
       product: AR5001 Wireless Network Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: wmaster0 
       version: 01 
       serial: 00:24:2b:8e:43:39 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k ip=10.1.1.4 latency=0 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:16 memory:55100000-5510ffff 
  *-network 
       description: Ethernet interface 
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller 
       vendor: Attansic Technology Corp. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: b0 
       serial: 00:23:5a:4e:d5:f5 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:27 memory:53000000-5303ffff ioport:1000(size=128) 

william@William-NetBook:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:23:5a:4e:d5:f5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:8e:43:39  
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0 
          inet6 addr: fe80::224:2bff:fe8e:4339/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:2056 (2.0 KB)  TX bytes:7314 (7.3 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-8E-43-39-38-65-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

william@William-NetBook:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:"irvine wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A:12:CA:94   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=41/70  Signal level=-69 dBm  Noise level=-98 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

```

---

### Post by Iowan on 2010-02-21
A couple more things to check: **route -n** and contents of */etc/resolv.conf*

---

### Post by northd_tech on 2010-02-21
> **williamirvine67 said:**
> 
**  lspci **
01:00.0 Ethernet controller: **Atheros** Communications Inc. **AR5001 Wireless** Network Adapter (rev 01) 
[COLOR=DarkGreen]03:00.0 Ethernet controller: **Attansic** Technology Corp. **Atheros AR8121/AR8113/AR8114** PCI-E Ethernet Controller (rev b0)[/COLOR]

**  lsmod **
Module                  Size  Used by 

**ath5k**                 124260  0 
mac80211              181236  1 **ath5k **
ath                     8060  1 **ath5k** 
cfg80211               93052  3 **ath5k**,mac80211,ath 
led_class               4096  1 **ath5k** 
[COLOR=DarkGreen]
atl1e                  31824  0 [/COLOR]

  uname -a 
Linux William-NetBook** 2.6.31-14-generic** #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 **i686** GNU/Linux 

william@William-NetBook:~$ sudo lshw -c network 
[sudo] password for william: 
  *-network               
       description: Wireless interface 
       product: AR5001 Wireless Network Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: wmaster0 
       version: 01 
       serial: 00:24:2b:8e:43:39 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k ip=10.1.1.4 latency=0 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:16 memory:55100000-5510ffff 
  *-network 
       description: Ethernet interface 
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller 
       vendor: Attansic Technology Corp. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: b0 
       serial: 00:23:5a:4e:d5:f5 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:27 memory:53000000-5303ffff ioport:1000(size=128) 

william@William-NetBook:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:23:5a:4e:d5:f5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:8e:43:39  
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0 
          inet6 addr: fe80::224:2bff:fe8e:4339/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          **RX packets:18** errors:0 dropped:0 overruns:0 frame:0 
         ** TX packets:54** errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:2056 (**2.0 KB**)  TX bytes:7314 (**7.3 KB**) 

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-8E-43-39-38-65-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

william@William-NetBook:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:"**irvine wireless**"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A:12:CA:94   
          Bit Rate=**12 Mb/s **  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          **Link Quality=41/70**  Signal level=-69 dBm  Noise level=-98 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

That's an Atheros AR5001 wireless, which I haven't worked with, but there are several threads about those if you search this forum for "atheros AR5001".  The stuff in green is for your Atheros (Attansic) [COLOR=DarkGreen]**AR8121/AR8113/AR8114 **[COLOR=Black]cabled ethernet connection (which does not look like it is connected to anything).

The RX/TX stuff makes it look like you are getting a little bit of wireless connection over the network.  The signal to "irvine wireless" is a little weak, and the 12 Mb/sec is a slow speed by modern standards.

The "ath5k" stuff are the wireless modules- several associated modules are loaded by the "ath5k" wireless module.  I'm not sure if this is the correct setup since I haven't worked with those, but finding an "atheros AR5001" thread here will likely help (maybe just link to your post with the output, or my interpretation of it here).

At this point, it looks more like a slow/weak connection problem than a no-connection problem to me.

Here are some threads here about Atheros AR5001 wireless:

[http://ubuntuforums.org/showthread.php?t=1306136](http://ubuntuforums.org/showthread.php?t=1306136)

[http://ubuntuforums.org/showthread.php?t=1394095](http://ubuntuforums.org/showthread.php?t=1394095)

[http://ubuntuforums.org/showpost.php?p=8859100&postcount=64](http://ubuntuforums.org/showpost.php?p=8859100&postcount=64)
[/COLOR][/COLOR]

---

### Post by williamirvine67 on 2010-02-22
thanks for that. 

well after looking around several sites and on several different forums, i noticed that im defiantly not the only one having this problem. only problem is that in most other case the people having the same problems as me can access the internet through their ethernet cable which leaves me in a bit of a hole.

one suggestion i have seen is that i should install the madwifi drivers, (my other computers have internet access, would this work?). although im not sure if this is the problem as the wireless is actually connecting to the router (being able to access it). so i agree with "northd_tech" on this... my internet is connected, just extreamly slow (update from last post is i have been able to access the google homepage a couple of times, but if i try to go any further no page will load).

another suggestion ive had is to install the wicd network manager as apprantly the preinstalled one dosent work with some wireless devices. one problem with this is that the installation and downloading has to be done through the terminal, which is a problem because... once again i cant access the internet!!!

arrrrggghhh.....! it feels like im going in circles!
almost ready to install 9.04 Netbook remix and see if i have any luck with that!

Thankyou once again, keep the ideas coming!

[COLOR="DarkGreen"]E: forgot to say,the reason that the ethernet didnt seem to be connected to anything was because it wasnt! only have wireless running at the time of testing, happy to post results with ethernet cable plugged in if you want[/COLOR]

---

### Post by williamirvine67 on 2010-02-22
> **Iowan said:**
> A couple more things to check: **route -n** and contents of */etc/resolv.conf*

/etc/resolv.conf only has one file in it called update-libc.d

and route -n shows

```


Kernal IP routing table
Destionation   Gateway    Genmask     Flags  Metric  Ref  Use Iface
169.254.0.0    0.0.0.0   255.255.0.0   U     1000    0     0  wlan0
10.0.0.0       0.0.0.0   255.0.0.0     U     2       0     0  wlan0
0.0.0.0        10.1.1.1  0.0.0.0       UG    0       0     0  wlan0

```

---

### Post by Abaddon on 2010-02-22
Sorry to hijack the thread, william.

I'm having a similar problem - my wired internet seems to work though.

I have an Asus eeePC 901 running UNR Karmic, and it seems to have died after installing some updates today, including the most recent kernel.

Connects to network no worries, but Firefox and Thunderbird (as well as the Ubuntu update manager) all time out.

Below are my diagnostics:

Thanks in advance for any help.


```
##LSPCI

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
trent@trent-eeepc:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

##LSUSB

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05e3:0505 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##LSMOD
Module                  Size  Used by
cbc                     3516  314 
aes_i586                8124  315 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
dm_crypt               12928  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
bridge                 47952  0 
snd_hwdep               7200  1 snd_hda_codec
stp                     2272  1 bridge
snd_pcm_oss            37920  0 
joydev                 10240  0 
snd_mixer_oss          16028  1 snd_pcm_oss
iptable_filter          3100  0 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ip_tables              11692  1 iptable_filter
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
bnep                   12060  2 
x_tables               16544  1 ip_tables
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               59080  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               36736  1 uvcvideo
psmouse                56500  0 
v4l1_compat            14336  2 uvcvideo,videodev
btusb                  11856  2 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               5280  0 
rt2860sta             522456  1 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
eeepc_laptop           13936  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  226120  3 
atl1e                  31824  0 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                 2780  1 video

##UNAME -A

Linux myeeepc 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux

## sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: b0
       serial: 00:23:54:32:a0:86
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fbfc0000-fbffffff ioport:ec80(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:26:46:cf
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:fbef0000-fbefffff
trent@trent-eeepc:~$ uname -a
Linux trent-eeepc 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
trent@trent-eeepc:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: b0
       serial: 00:23:54:32:a0:86
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fbfc0000-fbffffff ioport:ec80(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:26:46:cf
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:fbef0000-fbefffff

## ifconfig

eth2      Link encap:Ethernet  HWaddr 00:23:54:32:a0:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ra0       Link encap:Ethernet  HWaddr 00:22:43:26:46:cf  
          inet6 addr: fe80::222:43ff:fe26:46cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:700690 (700.6 KB)  TX bytes:14662 (14.6 KB)
          Interrupt:19 

##iwconfig

lo        no wireless extensions.

eth2      no wireless extensions.

ra0       RT2860 Wireless  ESSID:"Wireless"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1B:9E:C8:5F:65   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-42 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

## route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 ra0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ra0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ra0

## /etc/resolv.conf
# Generated by NetworkManager
domain home
search home
nameserver 192.168.1.1

```

---

### Post by Iowan on 2010-02-22
> **williamirvine67 said:**
> /etc/resolv.conf only has one file in it called update-libc.d /etc/resolvconf is a directory - /etc/resolv.conf is (or should be) a file containing nameservers. **route** looks OK!

---

### Post by williamirvine67 on 2010-03-10
well guys, seemed to have fixed the problem. My Firefox is now working fine.

but still have the issue with updates. i cant update or install any programs, not through the software center or the terminal.
have checked and double checked the software sources, even trying from overseas servers, but without any luck. 
Any help much appreciated

---

### Post by matchett808 on 2010-03-10
what did you change on firefox?

---

