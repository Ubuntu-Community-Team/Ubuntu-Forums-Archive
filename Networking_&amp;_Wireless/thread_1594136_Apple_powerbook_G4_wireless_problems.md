---
title: "Apple powerbook G4 wireless problems"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by thepotatobasher on 2010-10-12
**1 ) Machine Brand and Model (PC/Laptop)**:
Apple Powerbook G4 Titanium


**2 ) Wireless Brand, Model and Wireless Chipset:**
     Code:
     $ lspci $ lsusb 
here is output from lspci: doesn't seem to show wireless

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 PCI
0001:10:17.0 Unassigned class [ff00]: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:1a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 Internal PCI
0002:24:0e.0 FireWire (IEEE 1394): Agere Systems FW322/323
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)

([COLOR=Red]hint[/COLOR]) use **grep** to get only information about the Wireless
     Code:
     $ lspci -nn | grep 'Wireless Brand' 
I am struggling to get any output from the above code.  maybe because i don't know what to put for 'wireless brand'
[B]
3 ) check interface:[/B]
     Code:
     $ ifconfig $ iwconfig 
[B]ifconfig:

[/B]eth0      Link encap:Ethernet  HWaddr 00:03:93:b3:bc:aa  
          inet addr:192.168.1.141  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:93ff:feb3:bcaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6663 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11529389 (11.5 MB)  TX bytes:835933 (835.9 KB)
          Interrupt:41 Base address:0xd000 

eth1      Link encap:Ethernet  HWaddr 00:30:65:1f:c5:33  
          inet6 addr: fe80::230:65ff:fe1f:c533/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3211 (3.2 KB)
          Interrupt:57 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

([COLOR=Red]hint[/COLOR]) if the Wireless interface name is wlan0 you can also use
     Code:
     $ iwconfig wlan0 
[B]wireless driver is named eth1 for some reason but here is output for iwconfig eth1
[/B]
eth1      IEEE 802.11b  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-36 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:4
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[B]

4 ) Check for modules:[/B]
     Code:
     $ lsmod 
Module                  Size  Used by
isofs                  36058  1 
binfmt_misc             8558  1 
radeon                993740  0 
ttm                    68181  1 radeon
drm_kms_helper         33450  1 radeon
drm                   199176  3 radeon,ttm,drm_kms_helper
parport_pc             43723  0 
ppdev                   7753  0 
lp                      9472  0 
ipv6                  303022  14 
parport                39018  3 parport_pc,ppdev,lp
snd_powermac           68355  2 
loop                   16996  0 
apm_emu                 1472  0 
apm_emulation           7315  2 apm_emu
michael_mic             2388  4 
snd_aoa_i2sbus         20783  0 
snd_pcm                88078  2 snd_powermac,snd_aoa_i2sbus
snd_page_alloc          7776  1 snd_pcm
snd_seq_midi            6224  0 
snd_rawmidi            23466  1 snd_seq_midi
snd_seq_midi_event      7371  1 snd_seq_midi
snd_seq                61877  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24551  2 snd_pcm,snd_seq
airport                 3922  0 
snd_seq_device          7528  3 snd_seq_midi,snd_rawmidi,snd_seq
orinoco                76955  1 airport
sg                     32684  0 
pcmcia                 44258  0 
sr_mod                 16200  1 
snd                    64787  11 snd_powermac,snd_aoa_i2sbus,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           26982  0 
uninorth_agp            8348  1 
pmac_zilog             18394  0 
cfg80211              175966  1 orinoco
evdev                  11131  23 
pcmcia_rsrc            11721  1 yenta_socket
serial_core            23869  1 pmac_zilog
firewire_sbp2          15588  1 
soundcore               1140  1 snd
pcmcia_core            18128  3 pcmcia,yenta_socket,pcmcia_rsrc
rtc_generic             1399  0 
snd_aoa_soundbus        4936  1 snd_aoa_i2sbus
agpgart                40291  3 ttm,drm,uninorth_agp
usbhid                 45047  0 
hid                    78998  1 usbhid
firewire_ohci          27753  0 
firewire_core          58044  2 firewire_sbp2,firewire_ohci
sungem                 32968  0 
sungem_phy             12369  1 sungem
crc_itu_t               1475  1 firewire_core
windfarm_core          10472  0 

([COLOR=Red]hint[/COLOR]) search for the Wireless module
     Code:
     $ lsmod | grep "wlan_module_name" 
**5 ) Kernel boot messages**
     Code:
     $ dmesg 
Here is one of many duplicate error messages 
[  117.604681] eth1: Lucent/Agere firmware doesn't support manual roaming

([COLOR=Red]hint[/COLOR]) the same as in (4)

**6 ) Network configuration**
     Code:
     $ sudo lshw -C network 
 *-network               
       description: Ethernet interface
       product: UniNorth GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:24:0f.0
       logical name: eth0
       version: 01
       serial: 00:03:93:b3:bc:aa
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.1.141 latency=16 link=yes maxlatency=64 mingnt=64 multicast=yes port=MII speed=100MB/s
       resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:65:1f:c5:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=airport driverversion=2.6.35-22-powerpc firmware=Lucent/Agere 9.48 link=yes multicast=yes wireless=IEEE 802.11b
[B]


7 ) Scan for networks:[/B]
     Code:
     $ iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

**8 ) Ubuntu Version: **
     Code:
     $ lsb_release -d 
[B]Description:    Ubuntu 10.10


9 ) Kernel/architecture (including 32 vs. 64 bit): [/B]
     Code:
     $ uname -mr 
[B]2.6.35-22-powerpc ppc

10 ) Restarting the network:[/B]
     Code:
     $ sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                          
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.




supplementary links:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[http://newyork.ubuntuforums.org/showthread.php?t=1537469](http://newyork.ubuntuforums.org/showthread.php?t=1537469)

---

### Post by thepotatobasher on 2010-10-12
bumping for the AM crowd

---

### Post by thepotatobasher on 2010-10-12
Bumping again for the PM and late night crowd...please help =(
[ 	  ]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9960051")

---

### Post by thepotatobasher on 2010-10-15
bumping again just to see if anyone has any clue about what could be wrong

---

### Post by culby on 2010-10-30
Your post was two weeks ago, with no responses, so I don't know if you've given up in despair.
I'm struggling with the same problem, and therefore cannot claim any expertise--just a lot of empathy!

I've managed to get a partial solution with basically the same hardware, and I'm running 10.10 instead of 10.04. I can connect to a WEP-encrypted access point but not to a WPA one, so I'm still working on this.

First, it must mean something that you don't get a wireless entry with lspci. You get:
.
.
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 PCI
0001:10:17.0 Unassigned class [ff00]: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
.
.

I get:
.
.
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:17.0 Unassigned class [ff00]: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
.
.
in the same spot.

It must mean something, although what I cannot say.

The other thing I see in your output is that you appear to have the wrong driver for the card. You'll need to get the b43 driver for it. 

I see on other posts that this Broadcom controller that is the 'Airport Extreme' in the Macs is problematic everywhere. In order to make it work you need to update the firmware, and Broadcom does not make that easy. You need to download and install an 'fw_cutter' app to cut the firmware out from a Broadcom firmware file. 

Here's a link with a full discussion of the Broadcom driver/firmware issue, with documentation and instructions: [http://wireless.kernel.org/en/users/Drivers/b43#What.27s_the_difference_between_b43legacy_and_b43.3F](http://wireless.kernel.org/en/users/Drivers/b43#What.27s_the_difference_between_b43legacy_and_b43.3F)

And, I've seen other posts suggesting that the node will need to be wlan0 rather than eth1. I've lost the links where I saw that discussion. But, maybe installing the driver will get that done.

However, there is still the problem I have--if I only had a WPA access point I would still not have a connection, but because I have both a WPA and a WEP going, I can confirm that I can connect with the latter but not the former. I saw one reference in passing that old Broadcom cards (which I have--see above--and that you probably do as well although I have no idea why lspci doesn't show it to you) cannot support WPA. Still chasing that one.

Sigh.

Good luck.

---

