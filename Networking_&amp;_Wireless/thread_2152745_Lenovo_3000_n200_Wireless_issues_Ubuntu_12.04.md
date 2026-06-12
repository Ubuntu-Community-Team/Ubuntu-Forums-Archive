---
title: "Lenovo 3000 n200 Wireless issues Ubuntu 12.04"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by colleps1 on 2013-06-08
Hi forumers, 

I can not get my wireless to work on my laptop after a fresh install. I have tried all solustions on all of the other known issue threads. I can see the "enable wireless" option. My wireless switch is on and and I have used my "Fn + F5". Here is all my info. 


*************** info trace ***************

***** uname -a *****

Linux kevo-Ubuntu 3.5.0-32-generic #53~precise1-Ubuntu SMP Wed May 29 20:35:31 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise

***** lspci *****

04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0465]
	Kernel modules: ssb
06:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Lenovo Device [17aa:3861]
	Kernel driver in use: tg3

***** lsusb *****

Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 006 Device 002: ID 4168:1004  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** iwconfig *****


***** rfkill *****


***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.116
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             65.32.5.111
    DNS:             65.32.5.112



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1
search tampabay.rr.com

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist bcma
blacklist brcm80211
blacklist acer-wmi

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

***** dmesg *****


****************** done ******************

---

### Post by colleps1 on 2013-06-08
*-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:0a:bf:d4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=sb v3.03 ip=192.168.1.116 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:c8000000-c800ffff

---

### Post by colleps1 on 2013-06-08
paste.ubuntu.com/5746621 &#8211; user165487 1 hour ago 
	
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) Subsystem: Broadcom Corporation Device [14e4:0465] 06:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)

---

### Post by Hadaka on 2013-06-08
Hi, please do
```
sudo modprobe -rf ssb
sudo apt-get install linux-firmware-nonfree
sudo modprobe ssb
sudo modprobe b43
```
thanks.

---

### Post by colleps1 on 2013-06-08
Ok. Done. and thanks for the response. It installed the sta driver and is now active. Still no "enable wireless" and my wifi light is not on.

kevo@kevo-Ubuntu:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Hadaka on 2013-06-08
ok, lets take a look at a couple things..
please Copy and paste the following..
```
lsmod
lspci -nnk | grep -iA3 net
rfkill list all
```
post the output
thanks.

---

### Post by colleps1 on 2013-06-08
kevo@kevo-Ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   17791  2 
rfcomm                 38104  0 
bluetooth             189585  10 bnep,rfcomm
parport_pc             32115  0 
ppdev                  12850  0 
snd_hda_codec_realtek    64959  1 
coretemp               13362  0 
wl                   3032548  1 
microcode              18396  0 
psmouse                91381  0 
joydev                 17394  0 
snd_hda_intel          32983  3 
snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
serio_raw              13032  0 
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
cfg80211              181041  1 wl
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
r852                   17906  0 
sm_common              16773  1 r852
nand                   49703  2 r852,sm_common
nand_ids                8548  1 nand
mtd                    38671  2 sm_common,nand
nand_bch               13004  1 nand
bch                    21768  1 nand_bch
snd_timer              28932  2 snd_pcm,snd_seq
nand_ecc               13106  1 nand
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211               14041  1 wl
r592                   17809  0 
wmi                    18745  0 
memstick               15886  1 r592
snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13078  0 
i915                  479158  3 
lpc_ich                16993  0 
soundcore              14636  1 snd
drm_kms_helper         47459  1 i915
drm                   240232  4 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
video                  19117  1 i915
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
firewire_ohci          36110  0 
ahci                   25621  2 
libahci                26166  1 ahci
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
tg3                   141761  0

---

### Post by colleps1 on 2013-06-08
kevo@kevo-Ubuntu:~$ lspci -nnk | grep -iA3 net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0465]
	Kernel driver in use: wl
	Kernel modules: wl, ssb
06:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Lenovo Device [17aa:3861]
	Kernel driver in use: tg3
	Kernel modules: tg3

---

### Post by colleps1 on 2013-06-08
rfkill list all displays nothing.

---

### Post by Hadaka on 2013-06-08
Hi, please do..
```
sudo modprobe -rf wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt get install --reinstall linux-firmware-nonfee
sudo modprobe b43
```
Please dont load the sta driver again.its not the correct driver.
thanks.

---

### Post by colleps1 on 2013-06-08
ok....
"sudo apt get install --reinstall linux-firmware-nonfee" produces "sudo: apt: command not found
"
I copied and pasted....

did you mean "sudo apt-get install linux-firmware-nonfree"?

---

### Post by colleps1 on 2013-06-08
n/m. I see what i did wrong there. a dash was missing....

---

### Post by colleps1 on 2013-06-08
ok I did all of the afore mentioned:
sudo modprobe -rf wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install --reinstall linux-firmware-nonfree
sudo modprobe b43

Then I rebooted and no wireless.

---

### Post by Hadaka on 2013-06-08
ok..lets where we are then..
please do..
```
lsmod
sudo modprobe b43
dmesg | grep b43
```
thanks.

---

### Post by colleps1 on 2013-06-08
kevo@kevo-Ubuntu:~$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek    64959  1 
coretemp               13362  0 
parport_pc             32115  0 
ppdev                  12850  0 
rfcomm                 38104  0 
bnep                   17791  2 
bluetooth             189585  10 rfcomm,bnep
microcode              18396  0 
psmouse                91381  0 
serio_raw              13032  0 
snd_hda_intel          32983  3 
snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
joydev                 17394  0 
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
r852                   17906  0 
sm_common              16773  1 r852
nand                   49703  2 r852,sm_common
nand_ids                8548  1 nand
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
wmi                    18745  0 
mtd                    38671  2 sm_common,nand
nand_bch               13004  1 nand
bch                    21768  1 nand_bch
nand_ecc               13106  1 nand
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13078  0 
r592                   17809  0 
snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               15886  1 r592
i915                  479158  3 
drm_kms_helper         47459  1 i915
lpc_ich                16993  0 
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
drm                   240232  4 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
video                  19117  1 i915
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
firewire_ohci          36110  0 
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
ahci                   25621  2 
libahci                26166  1 ahci
tg3                   141761  0 
kevo@kevo-Ubuntu:~$ sudo modprobe b43

WARNING: All config files need .conf: /etc/modprobe.d/Untitled Document 1, it will be ignored in a future release.
kevo@kevo-Ubuntu:~$ dmesg | grep b43
[  328.822220] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  329.054224] Registered led device: b43-phy0::tx
[  329.054259] Registered led device: b43-phy0::rx
[  329.054288] Registered led device: b43-phy0::radio
[  329.220071] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)

---

### Post by colleps1 on 2013-06-08
I am a filthy Liar. It worked!! Thank you! [SOLVED]

---

### Post by Hadaka on 2013-06-08
Glad its working !
please mark this thread solved

How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

be sure to do the edit on your First post.
thanks.

---

### Post by colleps1 on 2013-06-08
All done Again I thank you you. Hooray for Uuntu community.

---

### Post by colleps1 on 2013-06-09
Ok... reopened it. So I left for a while and went and got me aa anchovy, herring and squid pizza.....with clam sauce... yum. I came home and wireless was gone again. I left PC up n running whilst I retrieved this tasty deliciousness.... So i scratched my dome for a bit.... I opened up a terminal and did lsmod. I looked through that for a while and realized after a slice or two I had no idea what I was looking at. So for fun I did sudo modprobe b43. Boom it came back. Any ideas?

---

