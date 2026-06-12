---
title: "Wireless Network On Laptop (RT2860)"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by QUIKI on 2011-10-25
Hello Ubuntees!

I have laptop (Zepto FL90) with RT2860 wireless card. I used Ubuntu for 6 months more or less and from first ever install I had problems with Wireless. Somehow I always fixed it and my wireless was working perfectly. 

After upgrading to Ubuntu 11.10 my wireless went down again and not like before:

Ubuntu starts normally and Network-Manager is on. When I press the icon on right top corner I cannot see any wireless networks. Writing "ifconfig" in terminal gives me Interfaces of eth0 and Loopback, but no wireless. Trying to find wireless Interface gives me no success. First I thought it was because of the drivers. New Kernel so old drivers would not work. Could not install new drivers because there are none. After few weeks of megaresearch on Internet I just decide that if I just write

"auto wlan0
iface wlan0 inet dhcp"

in sudo gedit /etc/network/interfaces

After restart my wireless was back and I was happy, but my booting was slower, because now everytime on Ubuntu logo with the five balls blinking I get the text
"Waiting for network configurations" ---after 30sec--> "Waiting up to 60 seconds for network configurations" and after this Ubuntu starts normally and I can use my laptop and wireless normally.

After 2-3 weeks:

Never the less the reason I write this thread is because today after the perfectly normal Update that comes almost every week my wireless is not working again. I restart my laptop and notice that now the booting goes like this

"Waiting for network configuration" ---after 30sec--> "Waiting up to 60 seconds for network configuration" --after 60sec--> "Booting system without full network configuration"

I get to Ubuntu and my wireless interface is nowhere to be found :cry:
Wired network works fine.

quiki@quiki-ZNOTE:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:6a:e5:f6
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=sb v2.09 latency=0 multicast=yes port=twisted pair
       resources: irq:49 memory:f0000000-f000ffff
  *-network UNCLAIMED
       description: Network controller
       product: RT2860
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f8000000-f800ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
quiki@quiki-ZNOTE:~$ 


quiki@quiki-ZNOTE:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric
quiki@quiki-ZNOTE:~$ 

uname -r
3.0.0 -13-generic

(Try already different network managers, but no help)
So should I just try to reinstall whole thing clean?

Thank you for the help and sorry for my English.

---

### Post by praseodym on 2011-10-25
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by QUIKI on 2011-10-25
> **praseodym said:**
> Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

quiki@quiki-ZNOTE:~$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: COMPAL Electronics Inc Device [14c0:0025]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]
    Subsystem: Ralink corp. Device [1814:2790]
    Kernel modules: rt2800pci
quiki@quiki-ZNOTE:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
vesafb                 13809  1 
nvidia              11713772  43 
snd_hda_codec_si3054    13008  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  5 
snd_hda_codec         104802  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
joydev                 17693  0 
snd_pcm                96755  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
tpm_infineon           17536  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
compal_laptop          20011  0 
snd                    68266  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_tis                18546  0 
psmouse                73882  0 
serio_raw              13166  0 
video                  19412  0 
wmi                    19256  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
ahci                   26002  6 
libahci                26861  1 ahci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
tg3                   147729  0 
quiki@quiki-ZNOTE:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

quiki@quiki-ZNOTE:~$ rfkill list
0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
quiki@quiki-ZNOTE:~$

---

### Post by praseodym on 2011-10-25
The driver is not loaded:

```
sudo modprobe -v rt2800pci
```
If it doesnt "survive" a reboot, force the module to load:

```
echo rt2800pci | sudo tee -a /etc/modules
```
Maybe this module is still blacklisted from Natty:

```
grep rt28 /etc/modprobe.d/*
```

---

### Post by QUIKI on 2011-10-25
> **praseodym said:**
> The driver is not loaded:

```
sudo modprobe -v rt2800pci
```If it doesnt "survive" a reboot, force the module to load:

```
echo rt2800pci | sudo tee -a /etc/modules
```Maybe this module is still blacklisted from Natty:

```
grep rt28 /etc/modprobe.d/*
```

(sudo modprobe -v rt2800pci) worked for me!
Well thank you very much sir! Would give you a hug, but kinda impossible so I'll give you this smile :popcorn:. Now I see the wireless, but when try to join it say that password is incorrect even when it is correct. I know this issue and I had it before so I can take it over from here. 

Thank you again and have a nice day.

---

