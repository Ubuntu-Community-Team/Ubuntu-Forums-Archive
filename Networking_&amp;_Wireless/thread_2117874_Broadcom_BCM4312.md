---
title: "Broadcom BCM4312"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by freezoid on 2013-02-19
hello!
My problem is I cant use wifi. I dont know if its system problem or my knowledge....
i've checked other topics and a lot of different solutions but result is usually the same... I cannot install any pack.

Its fresh installation of Lubuntu 12.10 on Lenovo ideapad s10.

I'm new to linux.

some needed informations that could help...
```

bartek@bartek-Lenovo:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux bartek-Lenovo 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux
bartek@bartek-Lenovo:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GSE Express Memory Controller Hub [8086:27ac] (rev 03)
	Subsystem: Lenovo Device [17aa:386f]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
	Subsystem: Lenovo Device [17aa:3870]
	Kernel driver in use: i915
	Kernel modules: intelfb, i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Lenovo Device [17aa:3870]
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: Lenovo Device [17aa:3bf8]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
	Subsystem: Lenovo Device [17aa:3807]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
	Subsystem: Lenovo Device [17aa:3808]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
	Subsystem: Lenovo Device [17aa:3809]
	Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
	Subsystem: Lenovo Device [17aa:380a]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
	Subsystem: Lenovo Device [17aa:380b]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
	Subsystem: Lenovo Device [17aa:380d]
	Kernel modules: leds-ss4200, lpc_ich, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
	Subsystem: Lenovo Device [17aa:3810]
	Kernel driver in use: ata_piix
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 02)
	Subsystem: Lenovo Device [17aa:3835]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
	Subsystem: Lenovo Device [17aa:380f]
	Kernel modules: i2c-i801
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Lenovo IdeaPad S10e [17aa:3a23]
	Kernel driver in use: tg3
	Kernel modules: tg3
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04b5]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
bartek@bartek-Lenovo:~$ lsusb
Bus 001 Device 002: ID 5986:0241 Acer, Inc BisonCam, NB Pro
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
bartek@bartek-Lenovo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

bartek@bartek-Lenovo:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
bartek@bartek-Lenovo:~$ 
bartek@bartek-Lenovo:~$ lsmod
Module                  Size  Used by
coretemp               13168  0 
joydev                 17161  0 
microcode              18209  0 
snd_hda_codec_realtek    63356  1 
psmouse                84843  0 
serio_raw              13031  0 
b43                   347284  0 
ums_realtek            17669  0 
uas                    17556  0 
snd_hda_intel          32515  1 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
mac80211              461161  1 b43
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
snd_seq_midi           13132  0 
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
btusb                  17950  0 
snd_rawmidi            25382  1 snd_seq_midi
lpc_ich                16925  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
ideapad_laptop         13670  0 
cfg80211              175375  2 b43,mac80211
bcma                   34483  1 b43
sparse_keymap          13658  1 ideapad_laptop
bnep                   17707  2 
rfcomm                 37276  12 
parport_pc             31968  0 
bluetooth             183228  22 btusb,bnep,rfcomm
ppdev                  12817  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  457161  2 
snd                    61991  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45271  1 i915
mac_hid                13037  0 
drm                   230463  3 i915,drm_kms_helper
soundcore              14599  1 snd
i2c_algo_bit           13197  1 i915
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
usb_storage            39350  1 ums_realtek
ssb                    50087  1 b43
tg3                   130448  0 
bartek@bartek-Lenovo:~$ 

```

---

### Post by kc1di on 2013-02-19
Hello freezoid and welcome to ubuntu/lubuntu,

in order to get your wireless going you will need to temporarily connect via erthernet Lan (hardwire)

The go to a terminal and type the following commands one at a time
you can copy and past them if you want.

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

That should get it going you may have to reboot also.
good luck :)

---

### Post by freezoid on 2013-02-19
hi and thanks for reply
another problem is I have no access to internet via cable...
can it be fixed diferent way?

---

### Post by kc1di on 2013-02-19
can you down load files on another machine that is connected?
if so you can download the files you need from [here]("http://packages.ubuntu.com/quantal/allpackages")

then install them with gdebi or dpkg from a terminal you'll have to transfer them to the laptop with a usb stick or disk. 

down load linux-headers-generic and bcmwl-kernel-source
Install linux-headers-generic first then bcmwl-kernel-source.
in a terminal the command to install them would be as follows
first cd to the director where you've placed them:
```
sudo dpkg -i linux-heders-generic
sudo dpkg -i bcmwl-kernel-source
```
**Note:** you will have to enter the complete file name example the bcmwl-kernel-soruce complete file name will look something like: 
**bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb**
once that's done run the following command in the terminal:
```
sudo modprobe wl
```

---

### Post by UltimateCat on 2013-02-19
> the install them with gdebi or dpkg from a terminal you'll have to transfer them to the laptop with a usb stick or disk. 


That's what I did and it worked for me.
I used my USB flash drive

---

### Post by freezoid on 2013-02-20
there are few different versions... distributions?
after trying with some I got msg like: newer version of headers is already installed

then i tryied kernel: dkms error...

I cant belive its so hard to start an "advanture" with linux for beginers...!
please help :O

---

### Post by freezoid on 2013-02-20
ops> posted by accident

---

### Post by wildmanne39 on 2013-02-20
Download the b43 zip file to a usb stick then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
cd Desktop
sudo mv b43/* /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
if you have other drivers installed uninstall them first.
Thanks

---

### Post by chili555 on 2013-02-20
If I may respectfully offer a suggestion to my esteemed colleague Wild Man; the driver b43 looks for firmware in /lib/frmware/b43 according to modinfo:> $ modinfo b43
filename:       /lib/modules/3.5.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       [COLOR="Red"]b43[/COLOR]/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
 Therefor, I think a very slight adjustment to his instructions is in order:```
[COLOR="Red"]sudo mkdir /lib/firmware/b43[/COLOR]
cd Desktop
sudo mv b43/* /lib/firmware/[COLOR="Red"]b43[/COLOR]
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```We now return you to your regularly scheduled guru.

---

### Post by wildmanne39 on 2013-02-20
Thanks chili555 for catching the error.

---

### Post by freezoid on 2013-02-21
So after few days in pain its at last solved!

your solution fixed it
```
sudo mkdir /lib/firmware/b43
cd Desktop
sudo mv b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```

Thank you guys! You're awesome!

---

