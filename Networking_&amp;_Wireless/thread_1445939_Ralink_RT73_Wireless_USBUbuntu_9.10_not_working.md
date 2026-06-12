---
title: "Ralink RT73 Wireless USB/Ubuntu 9.10 not working"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by Ceratonia on 2010-04-03
I have a Ralink USB WLAN device which I've plugged into an old pc with a clean install of Kubuntu 9.10. I can't get a wireless connection - reasonably sure the hardware itself is OK as the same setup worked fine with a different OS installed. I've played about with network manager GUI, to no avail.
 
A friend suggested blacklisting a particular USB driver and after doing this, network manager was able to detect the WLAN on a scan, but still no network connection. It seems like it doesn't try to connect rather than it tries but fails.
 
thanks for any suggestions on how to proceed.
 
**lsusb** shows
 
*Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp.*
 
**ifconfig**
 
eth0 Link encap:Ethernet HWaddr 00:0d:60:ad:ca:25 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:44 errors:0 dropped:0 overruns:0 frame:0
TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:2640 (2.6 KB) TX bytes:2640 (2.6 KB) 
wlan0 Link encap:Ethernet HWaddr 00:08:10:73:c9:9d 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
wmaster0 Link encap:UNSPEC HWaddr 00-08-10-73-C9-9D-00-00-00-00-00-00-00-00-00-00
UP RUNNING MTU:0 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
**iwconfig**
lo no wireless extensions.
eth0 no wireless extensions.
wmaster0 no wireless extensions.
wlan0 IEEE 802.11bgn ESSID:"BTHomeHub-2A70"
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=15 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
**lsmod**
 
Module Size Used by
rt2870sta 488820 0 
arc4 1660 2 
ecb 2524 2 
rt2800usb 37372 0 
ppdev 6688 0 
rt2x00usb 11548 1 rt2800usb
rt2x00lib 29756 2 rt2800usb,rt2x00usb
parport_pc 31940 1 
lp 8964 0 
parport 35340 3 ppdev,parport_pc,lp
led_class 4096 1 rt2x00lib 
input_polldev 3716 1 rt2x00lib 
iptable_filter 3100 0 
joydev 10272 0 
shpchp 32272 0 
ip_tables 11692 1 iptable_filter 
snd_intel8x0 30168 2 
snd_ac97_codec 101216 1 snd_intel8x0 
ac97_bus 1532 1 snd_ac97_codec 
snd_pcm_oss 37920 0 
snd_mixer_oss 16028 1 snd_pcm_oss 
snd_pcm 75296 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 2656 0 
snd_seq_oss 28576 0 
snd_seq_midi 6432 0 
snd_rawmidi 22208 1 snd_seq_midi 
snd_seq_midi_event 6940 2 snd_seq_oss,snd_seq_midi 
snd_seq 50224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211 181236 2 rt2x00usb,rt2x00lib 
snd_timer 22276 2 snd_pcm,snd_seq
snd_seq_device 6920 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 59204 14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 7264 1 snd
cfg80211 93052 2 rt2x00lib,mac80211
snd_page_alloc 9156 2 snd_intel8x0,snd_pcm
x_tables 16544 1 ip_tables
crc_ccitt 1852 1 rt2800usb
usbhid 38208 0
floppy 54916 0
e100 32452 0
mii 5212 1 e100
intel_agp 27484 1
agpgart 34988 1 intel_agp
 
**sudo lshw -C network**
 
*-network 
description: Ethernet interface 
product: 82562EZ 10/100 Ethernet Controller 
vendor: Intel Corporation 
physical id: 8 
bus info: pci@0000:03:08.0 
logical name: eth0 
version: 02 
serial: 00:0d:60:ad:ca:25 
size: 10MB/s 
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
resources: irq:20 memory:e4000000-e4000fff ioport:2000(size=64)
*-network
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:08:10:73:c9:9d
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
 
**lsb_release -d** 
 
Description: Ubuntu 9.10
 
**uname -mr**
 
2.6.31-14-generic i686

---

### Post by chili555 on 2010-04-03
> Module Size Used by
rt2870sta 488820 0
rt2800usb 37372 0
rt2x00usb 11548 1 rt2800usb
rt2x00lib 29756 2 rt2800usb,rt2x00usbMan! That is a lot of driver for one tiny wireless card. Please remove the device, open a terminal and do:```
sudo su
ifconfig wlan0 down
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00lib" >> /etc/modprobe.d/blacklist.conf
rmmod -f rt2800usb
rmmod -f rt2x00usb
rmmod -f rt2x00lib
ifconfig wlan0 up
exit
```If things go correctly, you will see no output from these commands. Reinsert the device and report your results.

---

### Post by Ceratonia on 2010-04-03
> **chili555 said:**
> If things go correctly, you will see no output from these commands. Reinsert the device and report your results.
 
It works!
 
Thank you so much - spent several hours trying to figure out the problem.

---

### Post by Rayve on 2010-07-23
Working with Ubuntu 9.10, this post has solved some issues for me, but I can't seem to get a DHCP offer.  

The status right now is: I can see "linksys" (my home wireless network, WPA2) as a possible connection, the green "Link" light is blinking on my ZONET 2500 little wireless USB (Ralink card, apparently using rt2870 chipset per some Googling) which is more than it was doing before, but when I try to connect through Network Manager it spins and then just says "Disconnected" and any dhclient attempt Discovers 255.255.255.255 but no offers.  Earlier tonight, I could get connected (though ifconfig told me ra0 had a private address in the 10.xxx.xxx.xxx range) but still no DHCP success.

I have constant wired internet at this time, so that's not a problem.  I have downloaded ndiswrappers but would love if it wasn't necessary.

Edit: I don't know if this helps / means anything, but for a while tonight I had about six WLAN possibilities to connect to - but their name in the Network Manager drop-down was all corrupted characters and the symbol next to them was for an unsecured network.  Each time I tried to connect, however, the name changed to linksys.  It was odd... haven't seen it since I went through and deleted all of them in the Network Manager GUI and then recreated a new Linksys entry.

Here is some info:

```

candice@candice-desktop:~$ lsusb | grep Ralink
Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. 

```

```

candice@candice-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_nvhdmi     6048  1 
snd_hda_codec_realtek   277860  1 
ipt_REJECT              3584  1 
ipt_LOG                 6404  1 
xt_limit                3236  2 
xt_tcpudp               3616  18 
xt_state                2432  6 
ipt_addrtype            2912  4 
ip6table_filter         3968  1 
snd_hda_intel          31976  2 
snd_hda_codec          87584  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ip6_tables             22608  1 ip6table_filter
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
nf_nat_irc              2688  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
nf_conntrack_irc        6552  1 nf_nat_irc
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia              10861992  56 
nf_nat_ftp              3584  0 
amd64_edac_mod         26688  0 
snd_timer              26992  2 snd_pcm,snd_seq
nf_nat                 22452  2 nf_nat_irc,nf_nat_ftp
rt3070sta             569480  1 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nf_conntrack_ipv4      16376  8 nf_nat
edac_core              48876  1 amd64_edac_mod
shpchp                 37756  0 
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2             8168  0 
nf_defrag_ipv4          2400  1 nf_conntrack_ipv4
soundcore               9088  1 snd
nf_conntrack_ftp        8984  1 nf_nat_ftp
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
nf_conntrack           80800  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          3872  1 
ip_tables              21200  1 iptable_filter
lp                     11908  0 
x_tables               25832  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables
parport                40528  2 ppdev,lp
usbhid                 43968  0 
video                  23612  0 
output                  3680  1 video
forcedeth              61292  0

```

```

candice@candice-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:64:31:9c  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe64:319c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2706316 (2.7 MB)  TX bytes:448334 (448.3 KB)
          Interrupt:28 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:263390 (263.3 KB)  TX bytes:263390 (263.3 KB)

ra0       Link encap:Ethernet  HWaddr 00:a1:b0:c0:61:5c  
          inet6 addr: fe80::2a1:b0ff:fec0:615c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:263691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97945 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68243602 (68.2 MB)  TX bytes:9439884 (9.4 MB)

```

```

candice@candice-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"Linksys"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: 00:25:9C:B8:6D:28   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:-45 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

candice@candice-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 40:61:86:64:31:9c
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.101 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:28 memory:f4e7c000-f4e7cfff ioport:a480(size=8) memory:f4e7e400-f4e7e4ff memory:f4e7e000-f4e7e00f
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:a1:b0:c0:61:5c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2870 Wireless

```

```

candice@candice-desktop:~$ lsb_release -d
Description:	Ubuntu 9.10
candice@candice-desktop:~$ uname -mr
2.6.31-22-generic x86_64

```

```

candice@candice-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:a1:b0:c0:61:5c
Sending on   LPF/ra0/00:a1:b0:c0:61:5c
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
candice@candice-desktop:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:61:86:64:31:9c  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe64:319c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28990 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3221469 (3.2 MB)  TX bytes:634350 (634.3 KB)
          Interrupt:28 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:272165 (272.1 KB)  TX bytes:272165 (272.1 KB)

ra0       Link encap:Ethernet  HWaddr 00:a1:b0:c0:61:5c  
          inet6 addr: fe80::2a1:b0ff:fec0:615c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:271120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70215847 (70.2 MB)  TX bytes:9767944 (9.7 MB)

ra0:avahi Link encap:Ethernet  HWaddr 00:a1:b0:c0:61:5c  
          inet addr:169.254.8.146  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

```

After reading dozens of forum posts, here are some files which I've changed:

```

candice@candice-desktop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto ra0
iface ra0 inet dhcp
	pre-up ifconfig ra0 up
#	pre-up iwpriv ra0 set SSID="Linksys"
#	pre-up iwpriv ra0 set EncrypType=TKIP
#	pre-up iwpriv ra0 set WPA2PSK="DAR23KS23KY"
#	pre-up iwpriv ra0 set NetworkType=Infra
wireless-essid Linksys
wireless-key 00a1b0c0615c

```

Only after the automatic blacklist entries:
```

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist snd_usb_audio

# Blacklisting ipv6, supposedly makes internet run faster.
blacklist ipv6

# ipv6 and following from this post: 
# http://ubuntuforums.org/showthread.php?t=884247
blacklist rt2400
blacklist rt2400pci
blacklist rt2570
blacklist rt2500
blacklist rt2500usb
blacklist rt2500pci
blacklist rt2x00
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
blacklist rt73

# following from http://ubuntuforums.org/showthread.php?t=400236
# Blacklist rt73usb, as it is a non-functional beta module which 
# conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib

# per http://www.linuxquestions.org/questions/linux-networking-3/ralink-chipset-works-in-ubuntu-jaunty-not-karmic-beta-761949/
blacklist rt2800usb
# removed the following because I need rt2870 driver per address of Bus 004 Device 003: ID 148f:3070 Ralink Technology, Corp. 
# blacklist rt2870sta

# from http://ubuntuforums.org/showthread.php?t=563547&highlight=avahi+ralink
blacklist rt2500usb
blacklist rt2500pci
blacklist rt2500 
blacklist rt2570
blacklist rt73usb
blacklist rt73pci
blacklist rt73
blacklist rt61usb
blacklist rt61pci
blacklist rt61
blacklist rt2860
blacklist rt2860sta
blacklist rt2x00usb
blacklist rt2x00lib

# from http://ubuntuforums.org/showthread.php?t=1445939
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

```

Thanks for any and all help!

---

### Post by Rayve on 2010-07-25
Well, I am able to get an IP address for my wireless now, and network manager tells me it is connected, but I can't disconnect my ethernet connection or else I lose everything.  When I try to use only my wireless connection, I have no internet.  

I tried wicd but didn't get anywhere else, so I went back to network-manager.  However, I can't just click "linksys" from the drop-down and have it connect.  That attempt only works once.  After that, I have to right-click and "edit connections" and then input the password again, click "Apply", and *then* it will try to connect.  Again, only works once.  Then I have to go back in to the properties tabs.  Quite annoying, honestly, and I don't know how to get it to work properly - I have it for "Connect Automatically" and "Apply to all users".

I think one of the errors might be that ra0 (my ralink usb wireless adapter) is trying to find an ipv6 router, even though I have ipv6 blacklisted.  At least, that's what's in dmesg when I plug in the usb.

Here is some current info:

```

lsmod | grep rt

rt3070sta             569480  1 

```
```

sudo ifconfig -a

ra0       Link encap:Ethernet  HWaddr 00:a1:b0:c0:61:5c  
          inet6 addr: fe80::2a1:b0ff:fec0:615c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:47692 errors:0 dropped:0 overruns:2772589245 frame:2772589245
          TX packets:1250287445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12464954 (12.4 MB)  TX bytes:996588 (996.5 KB)

```

---

### Post by Rayve on 2010-07-27
No ideas?

---

### Post by w2vy on 2010-07-27
Ok I am also very close

lsusb

```
Bus 002 Device 002: ID 04dd:92e7 Sharp Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsmod - I compiled and installed the module from the RALink website.
I have WPA_SUPPLICANT support enabled

```
Module                  Size  Used by
ks79xx_sdio            60904  0 
rt2870sta             579784  1 
```

ifconfig - I see the RA0 dvice - a good start

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4864 (4.8 KB)  TX bytes:4864 (4.8 KB)

ra0       Link encap:Ethernet  HWaddr 00:0d:09:40:63:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:34920 (34.9 KB)
```

lshw -C network

It recognizes it as a wireless device, even better

```
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:0d:09:40:63:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.0 multicast=yes wireless=Ralink STA
```

iwconfig

```
ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

uname -a

```
Linux tom 2.6.28-15-araneo #50fsl1araneo19-Ubuntu PREEMPT Mon Jan 25 15:54:27 UTC 2010 armv7l GNU/Linux
```

Ok it is Ubuntu 9.04 on an ARM (i.MX51) the araneo remix

Where can I look for clues as to why network manager ignores it.

Tom

---

### Post by w2vy on 2010-07-27
Boy this is a bit silly.

When searching the forum, I got to assume that the 2870 driver as designed to work for 148f:3070 but I was at the RALink website and saw the RT3070 driver.

I downloaded it, make & make install and it does about the same thing, except now ifconfig -a shows received bytes

No packets, so I assume it is just control data.

I then tried a manual scan:

```
root@tom:~/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412# wpa_cli ra0 scan
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
root@tom:~/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412# 

```

Ok! an error message!

why doesn't wpa_ctrl_open exist?
Is it a file that gets created on the fly as devices are inserted?

off to google... bed and hopefully a few replies by morning!

Tom
---
Well I switched to WICD and it saw the device.

It sure would be a nice Sticky Topic of how NetowrkManager, WPA_SUPPLICANT and device insertion/removal interact

---

### Post by rmamrick on 2010-07-28
> **chili555 said:**
> Man! That is a lot of driver for one tiny wireless card. Please remove the device, open a terminal and do:```
sudo su
ifconfig wlan0 down
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00lib" >> /etc/modprobe.d/blacklist.conf
rmmod -f rt2800usb
rmmod -f rt2x00usb
rmmod -f rt2x00lib
ifconfig wlan0 up
exit
```If things go correctly, you will see no output from these commands. Reinsert the device and report your results.
Amazing.  Any help with my wireless system would be appreciated.

  	 	 	 	 	 	  I have a Linksys AE 1000 wireless adapter and Linksys A3000 router with pc ubuntu 10.04 . I can't get a wireless connection.   
 lsusb 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 002: ID 04f3:02f4 Elan Microelectronics Corp.  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 

 ifconfig 
 eth0      Link encap:Ethernet  HWaddr 00:13:72:9f:e8:14   
           inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: 2002:6021:5a16:0:213:72ff:fe9f:e814/64 Scope:Global 
           inet6 addr: fe80::213:72ff:fe9f:e814/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:6341 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:4854 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:4019473 (4.0 MB)  TX bytes:938075 (938.0 KB) 
           Interrupt:16  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
 

 iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions.
 

 lsmod 
 Module                  Size  Used by 
 binfmt_misc             6587  1  
 tuner_simple           13577  1  
 tuner_types            14233  1 tuner_simple 
 nxt200x                12740  1  
 cx88_dvb               19413  0  
 cx88_vp3054_i2c         1808  1 cx88_dvb 
 videobuf_dvb            5175  1 cx88_dvb 
 dvb_core               86142  2 cx88_dvb,videobuf_dvb 
 tuner                  20412  0  
 snd_intel8x0           25588  2  
 fbcon                  35102  71  
 snd_ac97_codec        100646  1 snd_intel8x0 
 tileblit                2031  1 fbcon 
 ac97_bus                1002  1 snd_ac97_codec 
 font                    7557  1 fbcon 
 cx8800                 27220  0  
 cx8802                 12841  1 cx88_dvb 
 cx88_alsa               8115  1  
 snd_pcm_oss            35308  0  
 snd_mixer_oss          13746  1 snd_pcm_oss 
 bitblit                 4707  1 fbcon 
 softcursor              1189  1 bitblit 
 cx88xx                 72756  4 cx88_dvb,cx8800,cx8802,cx88_alsa 
 snd_pcm                70886  4 snd_intel8x0,snd_ac97_codec,cx88_alsa,snd_pcm_oss 
 vga16fb                11385  0  
 v4l2_common            15431  3 tuner,cx8800,cx88xx 
 rt2870sta             461971  0  
 videodev               34361  4 tuner,cx8800,cx88xx,v4l2_common 
 snd_seq_dummy           1338  0  
 snd_seq_oss            26726  0  
 vgastate                8961  1 vga16fb 
 v4l1_compat            13251  1 videodev 
 ir_common              38875  1 cx88xx 
 tveeprom               11102  1 cx88xx 
 snd_seq_midi            4557  0  
 videobuf_dma_sg        10814  5 cx88_dvb,cx8800,cx8802,cx88_alsa,cx88xx 
 i915                  285891  3  
 ndiswrapper           184867  0  
 snd_rawmidi            19056  1 snd_seq_midi 
 videobuf_core          16356  5 videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg 
 drm_kms_helper         29297  1 i915 
 intel_agp              24415  2 i915 
 drm                   163034  4 i915,drm_kms_helper 
 psmouse                63245  0  
 i2c_algo_bit            5028  3 cx88_vp3054_i2c,cx88xx,i915 
 ppdev                   5259  0  
 btcx_risc               3624  4 cx8800,cx8802,cx88_alsa,cx88xx 
 snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
 dell_wmi                1793  0  
 parport_pc             26250  1  
 snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
 serio_raw               3978  0  
 agpgart                31788  2 intel_agp,drm 
 snd_timer              19098  2 snd_pcm,snd_seq 
 snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
 lp                      7028  0  
 video                  17375  1 i915 
 dcdbas                  5490  0  
 snd                    54148  17 snd_intel8x0,snd_ac97_codec,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 output                  1871  1 video 
 soundcore               6620  1 snd 
 snd_page_alloc          7172  2 snd_intel8x0,snd_pcm 
 parport                32635  3 ppdev,parport_pc,lp 
 ohci1394               27238  0  
 usbhid                 36174  0  
 hid                    67032  1 usbhid 
 ieee1394               81213  1 ohci1394 
 floppy                 53080  0  
 tg3                   109580  0  
 

 $ sudo lshw -C network 
 [sudo] password for rick:  
   *-network                
        description: Ethernet interface 
        product: NetXtreme BCM5751 Gigabit Ethernet PCI Express 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        logical name: eth0 
        version: 01 
        serial: 00:13:72:9f:e8:14 
        size: 1GB/s 
        capacity: 1GB/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751-v3.44a ip=192.168.1.134 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s 
        resources: irq:16 memory:fe8f0000-fe8fffff 
 lsb_release -d  
 Description:	Ubuntu 10.04.1 LTS 
 

 uname -mr 
 2.6.32-24-generic-pae i686

---

### Post by rmamrick on 2010-07-28
> **rmamrick said:**
> Amazing.  Any help with my wireless system would be appreciated.

  	 	 	 	 	 	  I have a Linksys AE 1000 wireless adapter and Linksys A3000 router with pc ubuntu 10.04 . I can't get a wireless connection.   
 lsusb 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 002: ID 04f3:02f4 Elan Microelectronics Corp.  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 

 ifconfig 
 eth0      Link encap:Ethernet  HWaddr 00:13:72:9f:e8:14   
           inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: 2002:6021:5a16:0:213:72ff:fe9f:e814/64 Scope:Global 
           inet6 addr: fe80::213:72ff:fe9f:e814/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:6341 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:4854 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:4019473 (4.0 MB)  TX bytes:938075 (938.0 KB) 
           Interrupt:16  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
 

 iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions.
 

 lsmod 
 Module                  Size  Used by 
 binfmt_misc             6587  1  
 tuner_simple           13577  1  
 tuner_types            14233  1 tuner_simple 
 nxt200x                12740  1  
 cx88_dvb               19413  0  
 cx88_vp3054_i2c         1808  1 cx88_dvb 
 videobuf_dvb            5175  1 cx88_dvb 
 dvb_core               86142  2 cx88_dvb,videobuf_dvb 
 tuner                  20412  0  
 snd_intel8x0           25588  2  
 fbcon                  35102  71  
 snd_ac97_codec        100646  1 snd_intel8x0 
 tileblit                2031  1 fbcon 
 ac97_bus                1002  1 snd_ac97_codec 
 font                    7557  1 fbcon 
 cx8800                 27220  0  
 cx8802                 12841  1 cx88_dvb 
 cx88_alsa               8115  1  
 snd_pcm_oss            35308  0  
 snd_mixer_oss          13746  1 snd_pcm_oss 
 bitblit                 4707  1 fbcon 
 softcursor              1189  1 bitblit 
 cx88xx                 72756  4 cx88_dvb,cx8800,cx8802,cx88_alsa 
 snd_pcm                70886  4 snd_intel8x0,snd_ac97_codec,cx88_alsa,snd_pcm_oss 
 vga16fb                11385  0  
 v4l2_common            15431  3 tuner,cx8800,cx88xx 
 rt2870sta             461971  0  
 videodev               34361  4 tuner,cx8800,cx88xx,v4l2_common 
 snd_seq_dummy           1338  0  
 snd_seq_oss            26726  0  
 vgastate                8961  1 vga16fb 
 v4l1_compat            13251  1 videodev 
 ir_common              38875  1 cx88xx 
 tveeprom               11102  1 cx88xx 
 snd_seq_midi            4557  0  
 videobuf_dma_sg        10814  5 cx88_dvb,cx8800,cx8802,cx88_alsa,cx88xx 
 i915                  285891  3  
 ndiswrapper           184867  0  
 snd_rawmidi            19056  1 snd_seq_midi 
 videobuf_core          16356  5 videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg 
 drm_kms_helper         29297  1 i915 
 intel_agp              24415  2 i915 
 drm                   163034  4 i915,drm_kms_helper 
 psmouse                63245  0  
 i2c_algo_bit            5028  3 cx88_vp3054_i2c,cx88xx,i915 
 ppdev                   5259  0  
 btcx_risc               3624  4 cx8800,cx8802,cx88_alsa,cx88xx 
 snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
 dell_wmi                1793  0  
 parport_pc             26250  1  
 snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
 serio_raw               3978  0  
 agpgart                31788  2 intel_agp,drm 
 snd_timer              19098  2 snd_pcm,snd_seq 
 snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
 lp                      7028  0  
 video                  17375  1 i915 
 dcdbas                  5490  0  
 snd                    54148  17 snd_intel8x0,snd_ac97_codec,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 output                  1871  1 video 
 soundcore               6620  1 snd 
 snd_page_alloc          7172  2 snd_intel8x0,snd_pcm 
 parport                32635  3 ppdev,parport_pc,lp 
 ohci1394               27238  0  
 usbhid                 36174  0  
 hid                    67032  1 usbhid 
 ieee1394               81213  1 ohci1394 
 floppy                 53080  0  
 tg3                   109580  0  
 

 $ sudo lshw -C network 
 [sudo] password for rick:  
   *-network                
        description: Ethernet interface 
        product: NetXtreme BCM5751 Gigabit Ethernet PCI Express 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        logical name: eth0 
        version: 01 
        serial: 00:13:72:9f:e8:14 
        size: 1GB/s 
        capacity: 1GB/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751-v3.44a ip=192.168.1.134 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s 
        resources: irq:16 memory:fe8f0000-fe8fffff 
 lsb_release -d  
 Description:	Ubuntu 10.04.1 LTS 
 

 uname -mr 
 2.6.32-24-generic-pae i686
lsusb  Bus 001 Device 005: ID 13b1:002f Linksys

---

### Post by chili555 on 2010-07-29
> lsusb Bus 001 Device 005: ID 13b1:002f LinksysPlease start a new thread. You clearly do not have a Ralink RT73 device. Please include:```
dmesg | grep -e ndis -e rt2
```Thanks.

---

