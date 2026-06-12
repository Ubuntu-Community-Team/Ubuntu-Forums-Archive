---
title: "Can see wireless network but can't connect - Netgear WN111"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by skribanto on 2010-07-04
Hello and thanks for reading

I have managed to setup ndiswrapper and am able to see my wireless network but cannot connect to it.

I am using NDISWRAPPER and a Netgear WNDA3100 driver (I think this is Atheros-based) to connect through a Netgear WN111 USB Wireless dongle to my existing wireless network. I am running 9.04 on a Fujitstu-Siemens laptop. 

I am aware that the WNDA 3100 driver is not the intended driver for my WN111 dongle, but it is the only driver that showed "hardware present" when loaded. All others (I tried perhaps 5 or 6) showed driver installed but no info about hardware.

When I try to connect to the network it tries for a while, occasionally prompting me for the passphrase, and then eventually stops.

I would like some help figuring out what else I need to do. I feel I am nearly at the solution. My guesses are as follows (for what they're worth):

1. Could it be something to do with the WPA security?

2. Could it be something to do with this, output from dmesg?

> [   20.737363] ADDRCONF(NETDEV_UP): wlan1: link is not ready

3. Could I need to set some further parameters in the network manager?

Extremely grateful for any help anyone can give.

Cheers

Skrib

---

### Post by Roasted on 2010-07-04
In terminal, run "lspci" and post the results here.

Secondly, what if you remove security for a minute on your wireless - can you connect then??

---

### Post by roosh on 2010-07-05
Also, I don't think you're supposed to use both ndiswrapper and an ubuntu driver to manage the same device; are you saying that you're using the XP WNDA 3100 driver with ndiswrapper? 
Also could you run ```
lsmod
``` and ```
lsusb
``` and post the output.

---

### Post by skribanto on 2010-07-05
lspci

> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 04)

lsmod

> Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
ndiswrapper           193436  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         436276  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
sis190                 26116  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
mii                    13312  1 sis190
shpchp                 40212  0 
sis_agp                15360  1 
agpgart                42696  1 sis_agp
pcspkr                 10496  0 
video                  25872  0 
output                 11008  1 video
psmouse                61972  0 
serio_raw              13444  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


lsusb

> Bus 001 Device 002: ID 0846:9001 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by skribanto on 2010-07-05
lshw -C network

> *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:09:e5:31
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.2 ip=192.168.1.67 latency=0 module=sis190 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:73:8b:48:75:08
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:26:f2:98:ca:37
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+arusb_xp driverversion=1.53+,03/11/2008,3.0.0.102 multicast=yes wireless=Auto
skribanto@skribanto-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:09:e5:31
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.1.67 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:73:8b:48:75:08
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 00:26:f2:98:ca:37
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+arusb_xp driverversion=1.53+,03/11/2008,3.0.0.102 link=yes multicast=yes wireless=Auto


---

### Post by skribanto on 2010-07-05
> **Roasted said:**
> what if you remove security for a minute on your wireless - can you connect then??

Well firstly I can't in this case because my accesspoint is a Homeplug setup and THEN a router. I don't want to screw around with any of that, and besides, it works in Windows like a dream.

Secondly, I want to configure my laptop to be able to connect to secure access points elsewhere

---

### Post by skribanto on 2010-07-06
Any ideas please guys?

I have tried Gnome Network Manager and WICD. I have tried ndiswrapper and compiling ar9170 drivers from source. I have tried most things that looked like they could work from a dozen or more different walkthroughs. Beginning to lose my patience. I have 10.04 installed on my desktop and its a dream, but I need to get wireless working on my laptop.  Surely one of you has the solution to my problem?

---

### Post by pedro_orange on 2010-07-06
The next test would be to change the authentication type on the router to see if this is what is stopping you. 
Unless someone else has some ideas.

It doesn't matter if it works in Windows, I'm afraid this is not Windows. Your network card can obviously see the network, attempts to connect and fails. Therefore it's either being given the wrong passcode for the authentication, or the authentication is stopping it connecting to the network.

---

### Post by skribanto on 2010-07-06
> **pedro_orange said:**
> The next test would be to change the authentication type on the router to see if this is what is stopping you. 
Unless someone else has some ideas.

It doesn't matter if it works in Windows, I'm afraid this is not Windows. Your network card can obviously see the network, attempts to connect and fails. Therefore it's either being given the wrong passcode for the authentication, or the authentication is stopping it connecting to the network.

I take it that you've not looked at the verbose output from above, then?

It DOES matter that both the driver and the OS (Ubuntu) support WPA. The correct passcode is being given, I can assure you, I set it up, and the same passcode works on my Windows machine.

Therefore, this is a CONFIGURATION problem, hence my desire to enlist the help of some experts to tweak things so that they work.

Why is it that Ubuntu forums is increasingly full of posts that say that such and such is impossible, when even a cursory glance at other forums shows that it is?

---

### Post by pedro_orange on 2010-07-06
> **skribanto said:**
> I take it that you've not looked at the verbose output from above, then?

It DOES matter that both the driver and the OS (Ubuntu) support WPA. The correct passcode is being given, I can assure you, I set it up, and the same passcode works on my Windows machine.

Therefore, this is a CONFIGURATION problem, hence my desire to enlist the help of some experts to tweak things so that they work.

Why is it that Ubuntu forums is increasingly full of posts that say that such and such is impossible, when even a cursory glance at other forums shows that it is?

I take it you've not read what I said then? :P

I'm only trying to help, and the tone of your replies could be nicer. I'm simply saying what I see, you can choose to ignore it if you so wish.

I'm suggesting that the authentication type (Be it WPA/WPA2/WEP) is stopping Ubuntu from registering a connection on the network, and that changing the type of authentication may help you debug the issue. You can always change it back.

---

