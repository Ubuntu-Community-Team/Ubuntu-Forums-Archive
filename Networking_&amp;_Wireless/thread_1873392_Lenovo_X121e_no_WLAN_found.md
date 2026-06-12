---
title: "Lenovo X121e no WLAN found"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by bnubu on 2011-11-01
Hello
 
A week ago I received my net subnotebook x121e from Lenovo. Windows 7 64 was preinstalled but i replaced it by ubuntu 11.10 (3.0.0-13-generic x86_64) . Now everything works fine except I can't connect to a wlan. In fact the network manager doesn't even find any network. I searched the web for a solution but I got nowhere. I need to add that I am new to the Linux world so I hope I didn't make any stupid mistake... :confused:

Here some information:

Wireless:

[PHP]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:e285 Suyin Corp. 
Bus 003 Device 002: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 004: ID 0bb4:0ffe High Tech Computer Corp. [/PHP]When I check for the devices:

 [PHP]*-network               
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: e8:9a:8f:d8:05:8c
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f0100000-f013ffff ioport:2000(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 9e:ae:c5:1a:ed:7f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.58 link=yes multicast=yes

[/PHP]When I scan for networks:

[PHP]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.[/PHP]And modules (if this is of concern...)

[PHP]Module                  Size  Used by
rndis_wlan             37554  0 
cfg80211              199587  1 rndis_wlan
rndis_host             13848  1 rndis_wlan
cdc_ether              13536  1 rndis_host
usbnet                 26212  3 rndis_wlan,rndis_host,cdc_ether
usb_storage            57901  0 
uas                    18027  0 
bnep                   18436  2 
parport_pc             36962  0 
rfcomm                 47946  8 
ppdev                  17113  0 
btusb                  18600  2 
joydev                 17693  0 
bluetooth             166112  23 bnep,rfcomm,btusb
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_codec_conexant    62197  1 
snd_hda_codec_hdmi     32040  1 
psmouse                73882  0 
serio_raw              13166  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
k10temp                13166  0 
sp5100_tco             13791  0 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
wl                   2568210  0 
i2c_piix4              13301  0 
binfmt_misc            17540  1 
rts_pstor             445246  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
snd_seq_midi_event     14899  1 snd_seq_midi
lib80211               14991  1 wl
thinkpad_acpi          81819  0 
nvram                  14413  1 thinkpad_acpi
bcma                   20219  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2929009  95 
snd                    68266  15 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
video                  19412  0 
wmi                    19256  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  3 
libahci                26861  1 ahci
atl1c                  41643  0 [/PHP]It would be great if someone could help me since I've got no plan what I could do nor where to start. By the way please excuse my english, it's not my native language.

Thank you very much.

bnubu

---

### Post by alco75 on 2011-11-01
Your laptop is *very* similar to mine (Thinkpad Edge 11").

Try [here]("http://ubuntuforums.org/showthread.php?t=1604868&page=48") for a solution that worked for me.

---

### Post by alco75 on 2011-11-01
Infact **BCM43224** is exactly the same device as mine, so I bet blacklisting **bcma** and **brcmsmac** will work on your laptop too.

---

### Post by bnubu on 2011-11-01
It worked! :)
 
Thank you so much. This ends a series of nerve-racking failled attempts.
 
Have a nice evening

---

### Post by JENSON10 on 2011-11-14
Hi, even I have a x121e i3 processor with the broadcom chip for WLAN. When I scan for iwconfig it returns no wireless connections ??

There seems to be no drivers installed. I did try to install broadcom sta drivers without succeeding. Sorry I am not familiar with how Linux works so any help will be appreciated. I have installed ubuntu 10.10 with OSIAN environment from a live USB. I believe the Atheros Ethernet port won't allow me to access internet from an Ethernet cable as well !!!

---

