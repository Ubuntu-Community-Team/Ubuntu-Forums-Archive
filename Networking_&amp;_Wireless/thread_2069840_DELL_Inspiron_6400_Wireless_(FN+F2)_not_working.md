---
title: "DELL Inspiron 6400 Wireless (FN+F2) not working"
date: 2012-10-11
forum: Networking &amp; Wireless
---

### Post by danesp1 on 2012-10-11
Hi guys, just installed ubuntu, went to system settings > additional drivers, I then enabled and restarted Broadcom STA proprietary driver. Currently 'the driver is activated and currently in use', however I can't turn on the wireless and connect. I only get internet through ethernet.

Total noob, would appreciate any help. THanks!!

---

### Post by wildmanne39 on 2012-10-11
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by danesp1 on 2012-10-11
#!/bin/bash
#Script created by anewguy, tested by chili555 and edited by krytarik, llua and wildmanne39
exec > netinfo.txt 2> /dev/null
echo -e "\n*************** info trace ****************\n"
echo -e "\n\n**** uname -a ****\n\n"
uname -a
echo -e "\n\n**** lsb-release ****\n\n"
cat /etc/lsb-release
echo -e "\n\n**** lspci ****\n\n"
lspci -nnk | grep -iA2 net
echo -e "\n\n**** lsusb ****\n\n"
lsusb
echo -e "\n\n**** iwconfig ****\n\n"
iwconfig
echo -e "\n\n**** rfkill ****\n\n"
rfkill list all
echo -e "\n\n**** lsmod ****\n\n"
lsmod
echo -e "\n\n**** nm-tool ****\n\n"
nm-tool
echo -e "\n\n**** NetworkManager.state ****\n\n"
cat /var/lib/NetworkManager/NetworkManager.state
echo -e "\n\n**** NetworkManager.conf ****\n\n"
cat /etc/NetworkManager/NetworkManager.conf
echo -e "\n\n**** NetworkManager.conf-10.04 ****\n\n"
cat /etc/NetworkManager/nm-system-settings.conf
echo -e "\n\n**** interfaces ****\n\n"
cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
echo -e "\n\n**** iwlist ****\n\n"
[ -t 0 ] && sudo iwlist scan
[ ! -t 0 ] && gksudo iwlist scan
echo -e "\n\n**** resolv ****\n\n"
cat /etc/resolv.conf
echo -e "\n\n**** blacklist.conf ****\n\n"
cat /etc/modprobe.d/blacklist.conf
echo -e "\n\n**** dmesg ****\n\n"
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
echo -e "\n\n**************** done ********************\n\n"
sed -i 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' netinfo.txt

---

### Post by danesp1 on 2012-10-11
Sorry I think you want this:


*************** info trace ****************



**** uname -a ****


Linux Tarquin 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****




**** rfkill ****


0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes


**** lsmod ****


Module                  Size  Used by
parport_pc             32114  0 
rfcomm                 38139  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
snd_hda_codec_idt      60251  1 
b44                    31364  0 
joydev                 17393  0 
dell_wmi               12601  0 
ssb                    50691  1 b44
sparse_keymap          13658  1 dell_wmi
wl                   2646601  0 
snd_hda_intel          32765  3 
dell_laptop            17767  0 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
dcdbas                 14098  1 dell_laptop
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  414739  3 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                72919  0 
drm_kms_helper         45466  1 i915
serio_raw              13027  0 
drm                   197692  4 i915,drm_kms_helper
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
i2c_algo_bit           13199  1 i915
r592                   17808  0 
lib80211               14040  1 wl
memstick               15857  1 r592
wmi                    18744  1 dell_wmi
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
video                  19068  1 i915
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.3.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.3.1

    DNS:             192.168.3.250




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search chilecopper.local


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[   12.514797] wmi: Mapper loaded
[   13.219561] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.245189] wl 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.245200] wl 0000:0b:00.0: setting latency timer to 64
[   13.324761] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[   13.356243] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   13.356260] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   13.356276] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   13.356287] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   13.412184] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[   13.491161] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.508137] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   13.508149] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   13.508158] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   13.548170] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   13.548205] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[   13.569071] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   17.816227] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[   17.816233] b44 ssb1:0: eth0: Flow control is off for TX and off for RX
[   33.676962] type=1400 audit(1349960357.769:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1692 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1010.000146] b44 ssb1:0: eth0: Link is down
[ 3501.275722] b44 ssb1:0: eth0: powering down PHY
[ 4719.000260] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[ 4719.000271] b44 ssb1:0: eth0: Flow control is off for TX and off for RX


**************** done ********************

---

### Post by wildmanne39 on 2012-10-11
Hi you posted the actual script we need to see the netinfo.txt in your home folder that it created.
Thanks

---

### Post by wildmanne39 on 2012-10-11
Hi please do:
```
echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
make sure your wireless is turned on with the hardware switch.
Then:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot, Thanks

---

### Post by danesp1 on 2012-10-11
daniel@Tarquin:~$ echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for daniel: 
blacklist dell_laptop
daniel@Tarquin:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package broadcom-sta-common
E: Unable to locate package broadcom-sta-source
daniel@Tarquin:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree
daniel@Tarquin:~$

---

### Post by wildmanne39 on 2012-10-11
Hi, were you connected to the internet by wire when you ran these commands.
Thanks

---

### Post by danesp1 on 2012-10-11
yes correct, shall i try without wire?

---

### Post by wildmanne39 on 2012-10-11
Hi, with a wired connection please do:

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

### Post by danesp1 on 2012-10-11
mkdir: cannot create directory `/lib/firmware/b43': File exists

---

### Post by wildmanne39 on 2012-10-11
Hi, go on and run the other commands and it should work.
Thanks

---

### Post by danesp1 on 2012-10-11
sorry, which commands, I pasted in everything you gave me?

---

### Post by danesp1 on 2012-10-11
It's alive!!!

---

### Post by wildmanne39 on 2012-10-11
Hi, that is what I thought, great! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by danesp1 on 2012-10-11
thanks so much mate, really appreciate

---

### Post by wildmanne39 on 2012-10-11
Your welcome!
Enjoy

---

