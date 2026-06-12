---
title: "Wireless cuts out when bandwidth increases. Dell XPS 1530/3945ABG/Jaunty 9.04"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by bwolf1 on 2009-05-16
My wireless cuts out when bandwidth usage is anything more than minimal.

I have spent weeks trying various suggestions made by forum members to people with kind of similar problems and I'm not having any luck.

The way I work-around the problem is by disconnecting and reconnecting every time it happens by clicking here (of course rebooting works too):

[IMG]http://img355.imageshack.us/img355/8155/screenshotnhw.png[/IMG]

I recreated the issue (which isn't hard--all it takes is a click on any YouTube video) then ran all the commands suggested in the HOWTO post a Wireless issue (ticket) sticky thread.

1 ) Machine Brand and Model (PC/Laptop):

Dell XPS M1530 Laptop

2 ) Wireless Brand, Model and Wireless Chipset:

```

$ lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

``````

lsusb

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```3 ) check interface:

```

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:23:ae:1b:fe:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22574 (22.5 KB)  TX bytes:22574 (22.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:d2:68:b1  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fed2:68b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38081809 (38.0 MB)  TX bytes:4814996 (4.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-D2-68-B1-38-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

``````

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Belkin_N_Wireless_6784C6"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:DF:67:84:C6   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=85/100  Signal level:-48 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```4 ) Check for modules:

```

lsmod

Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
arc4                    9856  2 
ecb                    10752  2 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
iwl3945                97912  0 
snd_rawmidi            29696  1 snd_seq_midi
uvcvideo               63240  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  1 iwl3945
compat_ioctl32          9344  1 uvcvideo
psmouse                61972  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class              12036  1 iwl3945
nvidia               7233756  38 
dcdbas                 15264  0 
usbhid                 42336  0 
video                  25360  6 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
serio_raw              13316  0 
pcspkr                 10496  0 
soundcore              15200  1 snd
btusb                  19608  2 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
intel_agp              34108  0 
agpgart                42696  2 nvidia,intel_agp
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
output                 11008  1 video
cfg80211               38032  2 iwl3945,mac80211
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```5 ) Kernel boot messages:

```

dmesg | grep wlan0

[   19.442181] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.800419] wlan0: authenticate with AP 00:1c:df:67:84:c6
[   20.802209] wlan0: authenticated
[   20.802214] wlan0: associate with AP 00:1c:df:67:84:c6
[   20.804949] wlan0: RX AssocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=2)
[   20.804954] wlan0: associated
[   20.809152] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.820158] wlan0: disassociating by local choice (reason=3)
[   28.972655] wlan0: deauthenticated
[   28.974538] wlan0: authenticate with AP 00:1c:df:67:84:c6
[   28.980717] wlan0: authenticate with AP 00:1c:df:67:84:c6
[   28.980722] wlan0: authenticated
[   28.980724] wlan0: associate with AP 00:1c:df:67:84:c6
[   28.986575] wlan0: RX ReassocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=2)
[   28.986579] wlan0: associated
[   31.105058] wlan0: no IPv6 routers present
[ 1276.244185] wlan0: disassociating by local choice (reason=3)
[ 1276.249911] wlan0: direct probe to AP 00:1c:df:67:84:c6 try 1
[ 1276.449586] wlan0: direct probe to AP 00:1c:df:67:84:c6 try 2
[ 1276.462143] wlan0 direct probe responded
[ 1276.462155] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 1276.475470] wlan0: authenticated
[ 1276.475481] wlan0: associate with AP 00:1c:df:67:84:c6
[ 1276.482813] wlan0: RX AssocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=2)
[ 1276.482821] wlan0: associated
[ 1283.143706] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 1283.344162] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 1283.347766] wlan0: authenticated
[ 1283.347776] wlan0: associate with AP 00:1c:df:67:84:c6
[ 1283.351282] wlan0: RX ReassocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=2)
[ 1283.351289] wlan0: associated
[ 6943.954664] wlan0: disassociating by local choice (reason=3)
[ 6943.961589] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 6943.963307] wlan0: authenticated
[ 6943.963310] wlan0: associate with AP 00:1c:df:67:84:c6
[ 6943.969236] wlan0: RX AssocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=2)
[ 6943.969239] wlan0: associated
[ 6943.970654] wlan0: disassociating by local choice (reason=3)
[ 6963.796198] wlan0: deauthenticated
[ 6963.798214] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 6963.800582] wlan0: authenticated
[ 6963.800588] wlan0: associate with AP 00:1c:df:67:84:c6
[ 6963.811813] wlan0: RX ReassocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=2)
[ 6963.811821] wlan0: associated

```6 ) Network configuration:

```

sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:1b:fe:33
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:d2:68:b1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.5 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 62:8b:9c:13:2e:27
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```7 ) Scan for networks:

```

iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```8 ) Ubuntu Version: 

```

lsb_release -d

Description:    Ubuntu 9.04

```9 ) Kernel/architecture (including 32 vs. 64 bit): 

```

uname -mr

2.6.28-11-generic i686

```10 ) Restarting the network:

```

sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.

```

---

### Post by bwolf1 on 2009-05-16
I should probably also add that my wife runs a HP Pavilion ZE5400 with Windows XP Pro on the same network and she has no issues with her wireless connection.

---

### Post by bwolf1 on 2009-05-16
I'm also running 8.10 on another (a desktop) machine with a wired connection to the same router, and no problems there either.

---

### Post by bwolf1 on 2009-05-17
Does anyone actually have the 3945abg working 100% in 9.04?

---

### Post by bwolf1 on 2009-05-17
I'm wondering if installing the latest compat-wireless might be the answer. Anyone have thoughts on that? I don't see that suggested often, but perhaps that's just because most people don't know how to compile drivers?

---

### Post by bwolf1 on 2009-05-21
If anyone has the Intel Pro Wireless 3945 abg working 100% in 9.04 I would love to hear what you did to make it work, or if it just worked "out-of-the-box".

---

### Post by superprash2003 on 2009-05-21
if you still face the frequent disconnections , you could try changing MTU values

---

### Post by bwolf1 on 2009-05-22
Looks like is set to 1500 right now. That's pretty standard, isn't it? Do you suggest that I try decreasing it a little?

```

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:d2:68:b1  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fed2:68b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23945 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28355598 (28.3 MB)  TX bytes:4040165 (4.0 MB)

```

---

### Post by superprash2003 on 2009-05-22
yea , you could try 1452,1454,1492

---

### Post by jmlm-1970 on 2013-01-02
In my experience it cuts because of speed of usb devices connected... If I connect an usb3 disk to the usb3 port, the internal wi-fi disconnects immediately... If I connect the same usb3 disk to an usb2 hub, forcing disk to work at lower speed, the wi-fi is stable all the time...

---

### Post by overdrank on 2013-01-02
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

