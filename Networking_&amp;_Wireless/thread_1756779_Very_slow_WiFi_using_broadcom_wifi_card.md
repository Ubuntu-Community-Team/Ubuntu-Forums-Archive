---
title: "Very slow WiFi using broadcom wifi card"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by SimonHester on 2011-05-12
Hi All

I'm new to the forums and somewhat new to Ubuntu so any help would be great.

I'm struggling to get WIFI working on my Dell D600 with Ubuntu 11.04 freshly installed. 

I some limited sucched following the this post [http://ubuntuforums.org/showthread.php?t=1621331](http://ubuntuforums.org/showthread.php?t=1621331) this got the card working but it was very very slow over 70% packet loss to the WIFIrouter. 

1. Machine details 

Dell Latitude D600

2 Wireless Broadband and Chip set

lspci -nn | grep Broadcom - 02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 02)

3. Check interfaces

eth0      Link encap:Ethernet  HWaddr 00:0b:db:e0:1c:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:25:00:eb:f1:bb  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:ff:feeb:f1bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2817076 (2.8 MB)  TX bytes:279645 (279.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

@mokey:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

4 Check Modules

@mokey:~$ lsmod 
Module                  Size  Used by
radeon                896428  3 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
ttm                    65184  1 radeon
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
asix                   18138  0 
pcmcia                 39671  0 
joydev                 17322  0 
ndiswrapper           192828  0 
ppdev                  12849  0 
usbnet                 25175  1 asix
snd_timer              28659  2 snd_pcm,snd_seq
drm                   180037  5 radeon,ttm,drm_kms_helper
dcdbas                 14054  0 
yenta_socket           27230  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18951  0 
parport_pc             32111  1 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
i2c_algo_bit           13184  1 radeon
soundcore              12600  1 snd
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
tg3                   131476  0 

5. Kernal Boot Messages

Not sure what i;m looking for here the list is rather big so not included it yet. see to be nothing about my wifi mind. 

6. @mokey:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:e0:1c:5b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5702-v2.25 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:faff0000-faffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:fafee000-fafeffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 00:25:00:eb:f1:bb
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=14-Jun-2006 duplex=full firmware=ASIX AX88772 USB 2.0 Ethernet ip=192.168.0.7 link=yes multicast=yes port=MII speed=100Mbit/s

7. Iwlist 

iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

8. 

11.4

9.
mokey:~$ uname -mr
2.6.38-8-generic i686

---

### Post by SimonHester on 2011-05-18
I've been trying several different idea from various post all with little success and currently the wifi is down. 

It seem to me that the broadcom 4309 chip set is very hit and miss. Also i'm confused about which driver it really does need. Some seem to say it is a truemobile 1400 which is what the Dell web site says my machine has. 

All in all very lost. 

I have tried using ndiswrapper but can't get this to work. 

If anyone can help then i'd be grateful.

---

### Post by SimonHester on 2011-05-18
Have trying loads of stuff i have finall ygiven in and re-installed 11.04

I'm now getting the following errors with the dmesg command

[   21.369899] type=1400 audit(1305752846.128:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=774 comm="apparmor_parser"
[   22.392316] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   22.619162] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   23.058865] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.347800] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   23.347809] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[   32.784043] eth1: no IPv6 routers present

How do i download the correct firmware? 

Also should  i be trying to use Ndiswrapper or b43 the forums I have seen so far seem unclear on this.

I had tried ndiswrapper before but with little success using the GUI to install the driver it all seemed to work but then i still could not see wifi network in the desktop top right network manager drop down.  

The site [http://linuxwireless.org/en/users/Drivers/b43/devices](http://linuxwireless.org/en/users/Drivers/b43/devices) seems to suggest my card is support by the b43 drivers? can anyone confirm this?

Yet the same site that says the b43 driver can be used also does not list my chipset of 4309 as one that is supported. 
[http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types](http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types) 

Thanks in advance

---

### Post by SimonHester on 2011-05-19
Back to working wifi but very very slow only getting about 500k throughput to the wifi router which can't be right.

To get it working again i used the initial guide found here.  [http://ubuntuforums.org/showthread.php?t=1621331](http://ubuntuforums.org/showthread.php?t=1621331)

Not it i working but like i say very slow. 

Iwconfig shows

it running at 54Mbps

wlan0     IEEE 802.11bg  ESSID:"SKY63467"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:2F:6D:FD:CC   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:103  Invalid misc:705   Missed beacon:0

Checking a Dmesg i'm seeing a lot of errors like

[ 2050.169986] b43legacy-phy0 ERROR: PHY transmission error

Not sure what they are or if they re linked with my problem.

---

### Post by Ufonautas on 2011-06-23
Have you fixed your slow wifi problem? I have same problem too...

---

### Post by SimonHester on 2011-06-25
Hi
 
I never got the problem solved. Gave up to be honest! I had tried a loads of stuff but still the same packet loss. 
 
The only thing I might try again is using ndiswrapper. But the first time I tried this it broke it all completly and my thoughts are I'd rather have it work slowly than not at all. 
 
It is a real pain as whilst I don't use the machine alot i can't stream any video etc as it is just to slow.
 
If you have any luck then please let me know. I'll do like wise if I ever get round to trying to fix it again. 
 
Regards

---

