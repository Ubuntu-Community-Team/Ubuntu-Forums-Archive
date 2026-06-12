---
title: "RNX-N250PC on Ubuntu 11.10"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by virtuo on 2011-11-16
Hi:

Been an Ubuntu user for a few years now and have been wired, just purchased a router with wireless card.  The Rosewill RNX-N250 PC is what I have and I installed it, but cannot get a connection to the router with my computer.  The router is connected to DSL on another computer, in the other room and I can get a wireless connection via my smart phone no problem.  Any help?

---

### Post by praseodym on 2011-11-16
Hi,

which chipset is used? Please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by virtuo on 2011-11-16
> **praseodym said:**
> Hi,

which chipset is used? Please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82c6]
	Kernel driver in use: r8169
--
04:06.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Ralink corp. Device [1814:3062]
	Kernel driver in use: rt2800pci
:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0821 Logitech, Inc. 
Bus 001 Device 003: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 004 Device 002: ID 046d:c012 Logitech, Inc. Mouseman Dual Optical
:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40253  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
vesafb                 13809  1 
nvidia              11713772  40 
usbhid                 47198  0 
hid                    95463  1 usbhid
ppdev                  17113  0 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_usb_audio         118064  1 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm                96755  3 snd_hda_intel,snd_usb_audio,snd_hda_codec
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
k10temp                13166  0 
rt2800pci              18715  0 
rt2800lib              54306  1 rt2800pci
edac_core              53746  0 
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
edac_mce_amd           23709  0 
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              310872  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
snd                    68266  17 snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6           12725  1 rt2800pci
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
soundcore              12680  1 snd
v4l2_compat_ioctl32    17083  1 videodev
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sp5100_tco             13791  0 
i2c_piix4              13301  0 
parport_pc             36962  1 
asus_atk0110           18078  0 
wmi                    19256  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
binfmt_misc            17540  1 
usb_storage            57901  1 
uas                    18027  0 
pata_atiixp            13164  0 
floppy                 70365  0 
ahci                   26002  3 
libahci                26861  1 ahci
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  52788  0 
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by praseodym on 2011-11-16
First you can try to shut off the hardware encryption of the driver rt2800pci:

```
echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
```
and reboot.

If it is not working, remove the file again, install a Ralink driver (copy/paste those lines) and blacklist the other one:
```
sudo rm /etc/modprobe.d/rt2800pci.conf
sudo apt-get install linux-headers-$(uname -r) build-essential 
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. Check after that:
```
uname -a
lsmod
dmesg | egrep 'rt2|rt3'
iwconfig
sudo iwlist scan
```
Dont remove the driver folder, you need to compile again, if a kernel upgrade occurs:
```
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make clean
sudo make
sudo make install
```

---

### Post by virtuo on 2011-11-16
> **praseodym said:**
> First you can try to shut off the hardware encryption of the driver rt2800pci:

```
echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
```
and reboot.

If it is not working, remove the file again, install a Ralink driver (copy/paste those lines) and blacklist the other one::
```
sudo rm /etc/modprobe.d/rt2800pci.conf
sudo apt-get install linux-headers-$(uname -r) build-essential 
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Check after that:
```
uname -a
lsmod
dmesg | egrep 'rt2|rt3'
iwconfig
sudo iwlist scan
```
Dont remove the driver folder, you need to compile again, if a kernel upgrade occurs:
```
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make clean
sudo make
sudo make install
```

i shall try that and repost results.  :)

---

### Post by praseodym on 2011-11-16
I edited the post before, reboot after the blacklist-line.

---

### Post by virtuo on 2011-11-16
> **praseodym said:**
> I edited the post before, reboot after the blacklist-line.

Looks like that worked!  Excellent.  Thank you for your help!

---

### Post by praseodym on 2011-11-16
You should install the metapackage for the kernel headers, so please show:

```
uname -a
```

for the headers being updates automatically with the kernel itself. Then the (new) driver installlation is as easy as shown above. Otherwise you are updating somewhere/somehow and the wireless driver cannot be build

---

### Post by virtuo on 2012-04-27
i just upgrade to ubuntu 12.04 and as a result, had to reinstall the driver.  although, when using the same codes, it would not work at all.  please advise...

---

### Post by praseodym on 2012-04-28
Try the native driver:

```
sudo modprobe rt2800pci
```

---

### Post by virtuo on 2012-04-28
thanks!  that worked.  everytime there is an update or i upgrade, i lose the wifi binding; any way to keep it so it doesn't?

> **praseodym said:**
> Try the native driver:

```
sudo modprobe rt2800pci
```

---

### Post by praseodym on 2012-04-28
Check the black- and whitelists:

> grep rt2 /etc/modprobe.d/*
cat /etc/modules
lsmod

---

### Post by virtuo on 2012-04-30
Doesn't seem to hold a connection at all... strange...

> **virtuo said:**
> thanks!  that worked.  everytime there is an update or i upgrade, i lose the wifi binding; any way to keep it so it doesn't?

---

### Post by virtuo on 2012-08-18
Now having same issue where there's a weak connection and appears to cut connection now and again.  Run tablet off same wi-fi, so think it's driver perhaps?  Any input?

---

