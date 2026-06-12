---
title: "wireless doesn't work. please help."
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by 13tylse on 2011-09-30
I have ubuntu 11.04 installed on an HP G60 laptop. I can use an ethernet cord for connection, but it says my wireless is disabled. I saw someone mention in another forum mention an lspci command in the terminal. here's what i get when i type the command
 00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by Lisiano on 2011-10-10
That is weird, I don't see the AR5001 on the ath9k and ath5k drivers, maybe I'm not looking hard enough. Anyway.
Please give some more information.
```
lspci -k -nn -s 07:00.0
```
```
iwconfig
```
```
ifconfig
```
```
uname -a
```
```
sudo lshw -C network
```
```
lsmod
```
```
sudo iwlist scan
```
```
nm-tool
```
```
sudo rfkill list all
```
Enclose all of the output those commands give in the code tags, to do so, either type [ code ] (No spaces), copy-paste the output and type [ /code ] (No spaces) or press the **#**(hash) button.

---

### Post by Lisiano on 2011-10-12
Posting the output here from a PM. Note to OP: That information does not contain sensitive information apart from nm-tool and sudo lshw -C network, I assume you are sensitive to any private information leaking (Like your MAC address for example so I censored those) but there was no reference to any real world place like say a nearby router or even your external IP.
The reason I'm reposting here is because someone might jump into the thread and not know what is exactly going on, this will help anyone taking a look at the thread.
```
tyler@tyler-HP-G60-Notebook-PC:~$ lspci -k -nn -s 07:00.0
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
Subsystem: Hewlett-Packard Company Device [103c:137a]
Kernel driver in use: ath_pci
Kernel modules: ath_pci, ath5k
```
```
tyler@tyler-HP-G60-Notebook-PC:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wifi0 no wireless extensions.

ath0 IEEE 802.11g ESSID:"" 
Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated 
Bit Rate:0 kb/s Tx-Power:16 dBm Sensitivity=1/1 
Retry:off RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/70 Signal level=-96 dBm Noise level=-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```
```
tyler@tyler-HP-G60-Notebook-PC:~$ uname -a
Linux tyler-HP-G60-Notebook-PC 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
```
tyler@tyler-HP-G60-Notebook-PC:~$ sudo lshw -C network
[sudo] password for tyler: 
*-network 
description: Ethernet interface
product: MCP77 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: CENSORED
size: 100Mbit/s
capacity: 100Mbit/s
width: 32 bits
clock: 66MHz
capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=CENSORED latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
resources: irq:41 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
*-network
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:07:00.0
logical name: wifi0
version: 01
serial: CENSORED
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci latency=0 multicast=yes wireless=IEEE 802.11g
resources: irq:23 memory:c2000000-c200ffff

Rest got snipped due to post limit probably.
```
```
tyler@tyler-HP-G60-Notebook-PC:~$ lsmod
Module Size Used by
parport_pc 36959 0 
ppdev 17113 0 
snd_hda_codec_hdmi 28167 1 
snd_hda_codec_conexant 57511 1 
binfmt_misc 17565 1 
joydev 17606 0 
snd_hda_intel 33176 2 
snd_hda_codec 103804 3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_ intel
snd_hwdep 13604 1 snd_hda_codec
snd_pcm 96391 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi 13324 0 
nouveau 682322 2 
snd_rawmidi 30486 1 snd_seq_midi
snd_seq_midi_event 14899 1 snd_seq_midi
snd_seq 61621 2 snd_seq_midi,snd_seq_midi_event
ttm 76664 1 nouveau
hp_wmi 13706 0 
sparse_keymap 13898 1 hp_wmi
snd_timer 29602 2 snd_pcm,snd_seq
snd_seq_device 14462 3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper 42136 1 nouveau
drm 227534 4 nouveau,ttm,drm_kms_helper
i2c_algo_bit 13400 1 nouveau
uvcvideo 72195 0 
wlan_scan_sta 22407 1 
videodev 82052 1 uvcvideo
v4l2_compat_ioctl32 17078 1 videodev
ath_rate_sample 21620 1 
psmouse 73535 0 
snd 67382 14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_ intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi, snd_seq,snd_timer,snd_seq_device
serio_raw 13166 0 
soundcore 12680 1 snd
video 19438 1 nouveau
k10temp 13119 0 
i2c_nforce2 13058 0 
snd_page_alloc 18529 2 snd_hda_intel,snd_pcm
shpchp 37297 0 
ath_pci 198001 0 
wlan 252376 4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal 435109 3 ath_rate_sample,ath_pci
lp 17825 0 
parport 46458 3 parport_pc,ppdev,lp
usb_storage 53538 0 
uas 17996 0 
ahci 25951 2 
libahci 26642 1 ahci
forcedeth 63555 0 
pata_amd 14130 0 
```
```
tyler@tyler-HP-G60-Notebook-PC:~$ sudo iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wifi0 Interface doesn't support scanning.

ath0 No scan results
```
```
tyler@tyler-HP-G60-Notebook-PC:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 [Auto eth0] ----------------------------------------------------
Type: Wired
Driver: forcedeth
State: connected
Default: yes
HW Address: CENSORED

Capabilities:
Carrier Detect: yes
Speed: 100 Mb/s

Wired Properties
Carrier: on

IPv4 Settings:
Address: CENSORED
Prefix: 24 (255.255.255.0)
Gateway: CENSORED

DNS: CENSORED


- Device: ath0 -----------------------------------------------------------------
Type: 802.11 WiFi
Driver: ath_pci
State: unavailable
Default: no
HW Address: CENSORED

Capabilities:

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points
```
```
tyler@tyler-HP-G60-Notebook-PC:~$ sudo rfkill list all
0: hp-wifi: Wireless LAN
Soft blocked: yes
Hard blocked: yes
```

My findings: Your WiFi adapter is ath0, it's both soft blocked and hard blocked.

@OP
Do you have any buttons on your laptop that enable or disable wireless?
Could you try pressing it and re running this command
```
sudo rfkill list all
```
And see if it says 
```
Hard blocked: no
``` instead of Yes.
If not, could you try rebooting into Windows, enable it and reboot back into Ubuntu (DO NOT TOUCH THE BUTTON AFTER ENABLING IT) and try the above command again.

We will deal with the Soft block after we deal with the Hard block since if we can't remove it, no game and no use working on the Soft one which is a fairly easy one.

---

### Post by 13tylse on 2011-10-12
Ok, so it is soft blocked, but not hard. Either way, i don't have windows anymore because on my vista login screen i kept getting a blue screen that had some info about problems with my computer. Also, i do have a wifi button.

---

### Post by Lisiano on 2011-10-12
Sorry for the long delay. It's great news that it's now not hard blocked. To remove the soft block, just type this command and all good to go
```
sudo rfkill unblock all
```
Check it with ```
sudo rfkill list all
``` and it should say No to both Soft and Hard block.
You should be able to connect to any wireless network using the Network Manager (Looks like 2 arrows going up/down when there is a LAN cable connected, like a WiFi radio or like a paper fan.)

---

### Post by 13tylse on 2011-10-16
There is one more small issue i have, but the battery power and wireless connection buttons got removed from my panels and they are not in the add to panel menu.

---

