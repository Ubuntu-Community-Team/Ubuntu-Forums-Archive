---
title: "Can see wireless but can't connect"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by Hybird on 2010-05-16
Hi all, I am having trouble connecting to my wireless Linksys WRT610n router. I have had this computer set up to wireless networks through ubuntu previously but I can't seem to get it to connection at my new house. I can connect to the router using my Windows partition and it works fine. 

I am using Jaunty.

This is what i have tried so far. 

WIRELESS TAB
1.) Right Click Network icon and select Edit connections.
2.) Select my SSID and go to edit button to the right.
3.) I enter my SSID as it is broadcasted from the routers page. Im set to Infrastructure mode obviously. I entered the MAC address off of the router into that field. I don't know what to enter into BSSID cause I thought that was the same as the SSID, so I leave it blank. 

WIRELESS SECURITY TAB
1.) I am set to WPA & WPA2 Personal as is the same on the routers webpage.
2.) Here is where I think the problem is, it has a field named "Password" and my routers page only lists a 10 digit "PassPhrase". When I try to enter it, it changes it to a hex number.. now does it convert the passphrase to a password of is that just junk?

IPV4 SETTINGS TAB
1.) Set to DHCP, I don't use a static IP.


Can someone help me along somehow? I don't have a clue to get past this. I can give more info if required. Thanks in advance.

---

### Post by NUboon2Age on 2010-05-16
Good start, but let's start with the info requested in [HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?p=6183681")

---

### Post by Hybird on 2010-05-17
**1 ) Machine Brand and Model (PC/Laptop):**

HP Pavillion dv9000

**2 ) Wireless Brand, Model and Wireless Chipset:**
 
-lspci

```
00:00.0 RAM memory [0500]: nVidia Corporation MCP65 Memory Controller [10de:0444] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP65 LPC Bridge [10de:0442] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation MCP65 SMBus [10de:0446] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP65 SMU [10de:0447] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0454] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0455] (rev a3)
00:06.0 Ethernet controller [0200]: nVidia Corporation MCP65 Ethernet [10de:0450] (rev a3)
00:07.0 Audio device [0403]: nVidia Corporation MCP65 High Definition Audio [10de:044a] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI bridge [10de:0449] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP65 IDE [10de:0448] (rev a1)
00:0a.0 IDE interface [0101]: nVidia Corporation MCP65 SATA Controller [10de:045d] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation Device [10de:045b] (rev a1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:045a] (rev a1)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0458] (rev a1)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0459] (rev a1)
05:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
```

-lsusb
```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a110 Suyin Corp. 
```
[B]
3 ) check interface:[/B]

-ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:77:d3:ed  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:cf2f:fed9:0:21e:68ff:fe77:d3ed/64 Scope:Global
          inet6 addr: fe80::21e:68ff:fe77:d3ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30559 errors:1341 dropped:0 overruns:0 frame:1341
          TX packets:29721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27885003 (27.8 MB)  TX bytes:4257853 (4.2 MB)
          Interrupt:20 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:3f:f4:16  
          inet6 addr: fe80::221:ff:fe3f:f416/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:147 errors:0 dropped:0 overruns:0 frame:61476
          TX packets:180 errors:14 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29013 (29.0 KB)  TX bytes:24838 (24.8 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:608 (608.0 B)  TX bytes:608 (608.0 B)
```

-iwconfig

```
eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:167
          Rx invalid nwid:0  invalid crypt:7  invalid misc:0
```

**4 ) Check for modules:**

-lsmod

```
Module                  Size  Used by
usbhid                 47040  0 
michael_mic            10880  0 
arc4                   10240  0 
ecb                    11392  0 
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
ieee80211_crypt_tkip    17920  0 
wl                   1496016  0 
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  1 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ricoh_mmc              12544  0 
joydev                 20864  0 
sdhci_pci              16896  0 
sdhci                  27396  1 sdhci_pci
snd                    78792  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
nvidia               9638984  41 
i2c_nforce2            16136  0 
k8temp                 13440  0 
uvcvideo               69512  0 
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
psmouse                64028  0 
serio_raw              14468  0 
video                  29204  5 
output                 11648  1 video
ohci1394               42036  0 
ieee1394              108288  1 ohci1394
forcedeth              68368  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
```

[B]5 ) Kernel boot messages
Code:[/B]

-dmesg

##Assuming my only module is 'wl'

```
[   50.738298] wl 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 16 (level, low) -> IRQ 16
[   50.738304] wl 0000:03:00.0: setting latency timer to 64
```
[B]
6 ) Network configuration[/B]

-sudo lshw -C network

```
  *-network
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1e:68:77:d3:ed
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.103 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=1GB/s
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:21:00:3f:f4:16
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:ab:2e:75:e1:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

[B]7 ) Scan for networks:
Code:[/B]

-iwlist scan

```
interface doesn't support scanning
```

-iwlist scan wlan0

```
Unknown command wlan0
```

**8 ) Ubuntu Version:**

```
Ubuntu 9.04
```

**9 ) Kernel/architecture (including 32 vs. 64 bit):**

-uname -mr

```
2.6.28-11-generic x86_64
```

**10 ) Restarting the network:**

$ sudo /etc/init.d/networking restart

```
 * Reconfiguring network interfaces...
   ...done.
```

---

### Post by NUboon2Age on 2010-05-17
This person has the same network adapter.  Try this procedure.  Although I have a different Broadcom card, this procedure worked for me also:

[http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/](http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/)

---

### Post by NUboon2Age on 2010-05-17
Also see this procedure:

[http://www.micahcarrick.com/11-04-2007/bcm4328-wep-gutsy-ubuntu.html](http://www.micahcarrick.com/11-04-2007/bcm4328-wep-gutsy-ubuntu.html)

---

### Post by bkratz on 2010-05-17
When you did

-iwlist scan wlan0

Code:
Unknown command wlan0

Your wireless interface is name eth1 not wlan0, try that one again substituting eth1 for wlan0.

---

### Post by Hybird on 2010-05-20
> **bkratz said:**
> When you did

-iwlist scan wlan0

Code:
Unknown command wlan0

Your wireless interface is name eth1 not wlan0, try that one again substituting eth1 for wlan0.

That doesn't work, none of these things support the scan function, I get the following message for all of them. 

```

lo            Interface doesn't support scanning.

eth0        Interface doesn't support scanning.

eth1        Interface doesn't support scanning.

pan0       Interface doesn't support scanning.

```

---

### Post by Hybird on 2010-05-20
I'm pretty sure my wireless card is set up ok because I can see all of the wireless signals in the area and can connect to some one else's unsecured signal. I just can't connect to mine and can't figure out why. I think it has something to do with me entering a Passphrase instead of a password. Is there anyway to completely setup a wireless connection using only the terminal?

EDIT: Well I changed the wireless security to WEP and now I can connect. I'll have to look into this more, but at least it works for now. I don't like the idea of less security though.

---

