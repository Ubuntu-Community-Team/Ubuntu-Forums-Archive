---
title: "Ubuntu 12.04 and Broadcom NetXtreme b57XX on Dell Precision M65"
date: 2013-07-03
forum: Networking &amp; Wireless
---

### Post by jones60538 on 2013-07-03
Hello,

I just installed Ubuntu 12.04 LTS on a Dell Precision M65 laptop that has an integrated Broadcom NetXtreme b57xx Ethernet Adapter. Network Manager shows the Wired Network disconnected and I am unable to get it to connect. The tg3 driver appears to load correctly as a kernel module. I've tried manually entering configuration for eth0 into /etc/network/interfaces instead of letting NM manage the connection, but this didn't work either. Lights on the back of the NIC are orange indicative of no physical link, but I am able to get a link and IP when booting into Windows from the same laptop. I've spent the last two days reading posts to the forums and have not been able to identify any solutions that work in my case and would be very appreciative of any help or suggestions from the forum.

> root@Ubuntu1:~# uname -a
Linux Ubuntu1 3.5.0-34-generic #55~precise1-Ubuntu SMP Fri Jun 7 16:25:50 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

> root@Ubuntu1:~# lshw -C network
*-network
description: Wireless interface
product: PRO/Wireless 3945ABG [Golan] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:0c:00.0
logical name: wlan0
version: 02
serial: 00:18:de:39:63:ef
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 driverversion=3.5.0-34-generic firmware=15.32.2.9 ip=192.168.10.122 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
resources: irq:45 memory:dcfff000-dcffffff
*-network
description: Ethernet interface
product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 02
serial: 00:15:c5:c1:0e:82
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair
resources: irq:47 memory:dcef0000-dcefffff

> root@Ubuntu1:~# lspci |grep net
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)

> root@Ubuntu1:~# ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:15:c5:c1:0e:82
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:18

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1071 errors:0 dropped:0 overruns:0 frame:0
TX packets:1071 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:96935 (96.9 KB) TX bytes:96935 (96.9 KB)

wlan0 Link encap:Ethernet HWaddr 00:18:de:39:63:ef
inet addr:192.168.10.122 Bcast:192.168.10.255 Mask:255.255.255.0
inet6 addr: fe80::218:deff:fe39:63ef/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:32628 errors:0 dropped:0 overruns:0 frame:0
TX packets:11673 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:19857629 (19.8 MB) TX bytes:1602764 (1.6 MB)

> root@Ubuntu1:~# lsmod
Module Size Used by
rfcomm 47562 12
bnep 18240 2
nvidia 11309216 44
wl 3074942 0
coretemp 13642 0
joydev 17694 0
kvm 422160 0
ppdev 17114 0
hid_generic 12541 0
gpio_ich 13384 0
dell_laptop 17426 0
dcdbas 14491 1 dell_laptop
microcode 23030 0
snd_hda_codec_idt 70774 1
snd_usb_audio 136422 1
parport_pc 32867 1
pcmcia 49390 0
snd_hda_intel 34063 3
snd_hda_codec 135141 2 snd_hda_codec_idt,snd_hda_intel
snd_pcm 97523 3 snd_usb_audio,snd_hda_intel,snd_hda_codec
lib80211 14382 1 wl
snd_hwdep 17765 2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib 29478 1 snd_usb_audio
snd_seq_midi 13325 0
snd_seq_midi_event 14900 1 snd_seq_midi
snd_rawmidi 30750 2 snd_usbmidi_lib,snd_seq_midi
snd_seq 61931 2 snd_seq_midi,snd_seq_midi_event
video 19653 0
mac_hid 13254 0
snd_timer 29990 2 snd_pcm,snd_seq
uvcvideo 78117 0
videobuf2_core 33025 1 uvcvideo
usbhid 47259 0
hid 100815 2 hid_generic,usbhid
videodev 125126 2 uvcvideo,videobuf2_core
videobuf2_vmalloc 12861 1 uvcvideo
snd_seq_device 14498 3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf2_memops 13405 1 videobuf2_vmalloc
arc4 12530 2
yenta_socket 32181 0
pcmcia_rsrc 18431 1 yenta_socket
pcmcia_core 22615 3 pcmcia,yenta_socket,pcmcia_rsrc
snd 83674 19 snd_hda_codec_idt,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwl3945 74592 0
iwlegacy 105121 1 iwl3945
psmouse 102506 0
mac80211 555272 2 iwl3945,iwlegacy
serio_raw 13216 0
btusb 22432 0
lpc_ich 17145 0
bluetooth 211812 24 rfcomm,bnep,btusb
cfg80211 208382 4 wl,iwl3945,iwlegacy,mac80211
soundcore 15092 1 snd
snd_page_alloc 18573 2 snd_hda_intel,snd_pcm
lp 17800 0
parport 46563 3 ppdev,parport_pc,lp
firewire_ohci 41034 0
firewire_core 64697 1 firewire_ohci
crc_itu_t 12708 1 firewire_core
tg3 156646 0

> root@Ubuntu1:~# ethtool eth0
Settings for eth0:
Supported ports: [ TP ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full
Supported pause frame use: No
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full
Advertised pause frame use: Symmetric
Advertised auto-negotiation: Yes
Speed: Unknown!
Duplex: Unknown! (255)
Port: Twisted Pair
PHYAD: 1
Transceiver: internal
Auto-negotiation: on
MDI-X: Unknown
Supports Wake-on: g
Wake-on: g
Current message level: 0x000000ff (255)
drv probe link timer ifdown ifup rx_err tx_err
Link detected: no

---

### Post by chili555 on 2013-07-03
First, please be sure all settings related to eth0 are removed from /etc/network/interfaces. Second, Network Manager will, in a few cases, refuse to activate any other interface if an active connection exists; in this case, wireless is active. Please click the Network Manager icon and click 'Disconnect.' Now let's look at some diagnostics.```
dmesg | grep -e tg3 -e eth0
cat /var/log/syslog | grep -e eth0 -e tg3 -e etwork | tail -n25
```Reconnect wireless and post the results here.

---

### Post by varunendra on 2013-07-03
> **jones60538 said:**
> ```
root@Ubuntu1:~# lshw -C network
*-network
description: Ethernet interface
product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
....
**capacity: 1Gbit/s**
....
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 firmware=5752-v3.19 latency=0 **link=[COLOR="#FF0000"]no[/COLOR]** multicast=yes port=twisted pair
```
Let's try to force the lowest speed and see if it can connect. Please do -
```
sudo ethtool -s eth0 speed 10 duplex full autoneg off
```
If that alone doesn't make any difference, also do -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

If this helps, you can try "100" instead of "10" in the command. To turn auto-negotiation on again, change "autoneg off" to "autoneg on" (see **man ethtool** for more details).

**EDIT:**
Ouch !! Sorry for the accident doc ! Started when your post wasn't here, got late in reading 'man' and trying myself :P

---

### Post by jones60538 on 2013-07-03
Thank you for the responses!  
The problem must have been in the speed negotiation with my switch.  As soon as I used ethtool to set to 100mbs full duplex, network manager immediately showed the connection as active.

```
root@Ubuntu1:~# ethtool -s eth0 speed 100 duplex full autoneg off
```

How can I make this change permanent?

Thanks again!

---

### Post by varunendra on 2013-07-03
You're welcome!

Unfortunately -
> **jones60538 said:**
> How can I make this change permanent?
.. I don't know a decent way to do this. In fact I believed the command itself has a permanent effect. However, the 'crude' way is to add the command to your '/etc/rc.local' file so it executes automatically at startup. Here's how -

[INDENT]1) Open the file as root -
```
gksu gedit /etc/rc.local
```

2) Insert the following line just above the last line ("exit 0") -
```
ethtool -s eth0 speed 100 duplex full autoneg off
```
It is very important that the last line in the file remains "exit 0", so make sure the above line is inserted above it. Proofread, save and close the file.[/INDENT]

**PS:**
Just noticed that you are running the system as 'root'. Not a good idea unless you have some very specific reasons and is absolutely necessary, even if you are a Linux expert and always know what you are doing. Not related to the problem though. :)

---

### Post by jones60538 on 2013-07-03
Thanks Varun.  Adding to /etc/rc.local seems to do the trick.

---

