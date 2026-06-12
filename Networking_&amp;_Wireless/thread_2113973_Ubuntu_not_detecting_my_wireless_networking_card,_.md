---
title: "Ubuntu not detecting my wireless networking card, ASUS PCE-N53"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by jannk on 2013-02-08
Hi all,
As title stated i have some issues with my wifi card. It's a ASUS PCE-N53 wireless networking pci-e card. Installed both Ubuntu 12.04 and 12.10 and the OS ain't detecting my wifi card.

Tried few other distro's also but the same. The card works because i tested it in w7 to be sure, works fine.

So i'm not sure what it can be, something it don't detect the card in the kernel or something?

Any help would be very much appriciated because i'am lost what to do now.

Cheers Jan

---

### Post by jannk on 2013-02-09
No one got a solution on this? Help would be much appriciated.

---

### Post by praseodym on 2013-02-09
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by chili555 on 2013-02-09
Did you see this? [http://askubuntu.com/questions/193319/missing-driver-asus-pce-n53-11n-n600-pci-e-adapter](http://askubuntu.com/questions/193319/missing-driver-asus-pce-n53-11n-n600-pci-e-adapter)

---

### Post by jannk on 2013-02-09
> **praseodym said:**
> Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```

Okei, yeah can some commands like the uname -a. Not tryed the others tbh. I see some tells some network info and hardware. Here is what i found.

```

***uname -a***
Linux jannis 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


***lspci -nnk***
00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 13)
    Subsystem: ASUSTeK Computer Inc. Device [1043:836b]
00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 13)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 13)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:07.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 [8086:340e] (rev 13)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:14.0 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 13)
    Kernel driver in use: i7core_edac
    Kernel modules: i7core_edac
00:14.1 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 13)
    Kernel modules: mce-xeon75xx
00:14.2 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 13)
00:14.3 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub Throttle Registers [8086:3438] (rev 13)
00:1a.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard [1043:82d4]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard [1043:82d4]
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard [1043:82d4]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard [1043:82d4]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ea]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3 [8086:3a44]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 [8086:3a4a]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard [1043:82d4]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard [1043:82d4]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard [1043:82d4]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard [1043:82d4]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard [1043:82d4]
    Kernel modules: lpc_ich
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
    Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard [1043:82d4]
    Kernel modules: i2c-i801
00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 [8086:3a26]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Kernel driver in use: ata_piix
01:00.0 Network controller [0280]: Ralink corp. Device [1814:5592]
    Subsystem: ASUSTeK Computer Inc. Device [1043:851a]
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Tahiti PRO [Radeon HD 7950] [1002:679a]
    Subsystem: XFX Pine Group Inc. Device [1682:3220]
    Kernel driver in use: radeon
    Kernel modules: radeon
02:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Tahiti XT HDMI Audio [Radeon HD 7970 Series] [1002:aaa0]
    Subsystem: XFX Pine Group Inc. Device [1682:aaa0]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81f8]
    Kernel driver in use: sky2
    Kernel modules: sky2
05:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6121 SATA II / PATA Controller [11ab:6121] (rev b2)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8212]
    Kernel driver in use: pata_marvell
    Kernel modules: pata_marvell
06:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81f8]
    Kernel driver in use: sky2
    Kernel modules: sky2
08:02.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0)
    Subsystem: ASUSTeK Computer Inc. M4A series motherboard [1043:81fe]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
ff:00.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers [8086:2c41] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:00.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder [8086:2c01] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:02.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QPI Link 0 [8086:2c10] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:02.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 [8086:2c11] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:03.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller [8086:2c18] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:03.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder [8086:2c19] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:03.4 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers [8086:2c1c] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:04.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers [8086:2c20] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:04.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers [8086:2c21] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:04.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers [8086:2c22] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:04.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2c23] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:05.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers [8086:2c28] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:05.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers [8086:2c29] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:05.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers [8086:2c2a] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:05.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2c2b] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:06.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers [8086:2c30] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:06.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers [8086:2c31] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:06.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers [8086:2c32] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
ff:06.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers [8086:2c33] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]

***lsusb***
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 006 Device 002: ID 046d:c066 Logitech, Inc. 
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***lsmod***
Module                  Size  Used by
snd_hda_codec_hdmi     32007  1 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
snd_hda_codec_analog    93491  1 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
mxm_wmi                12979  0 
hid_logitech_dj        18604  0 
microcode              22803  0 
snd_hda_intel          33491  4 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
psmouse                95552  0 
snd_seq_midi           13324  0 
serio_raw              13215  0 
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
lpc_ich                17061  0 
joydev                 17457  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  18 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                895653  2 
ttm                    83595  1 radeon
i7core_edac            23571  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
drm_kms_helper         46784  1 radeon
edac_core              52451  3 i7core_edac
drm                   275528  4 radeon,ttm,drm_kms_helper
asus_atk0110           17646  0 
i2c_algo_bit           13413  1 radeon
mac_hid                13205  0 
wmi                    19070  1 mxm_wmi
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
floppy                 69452  1 
usbhid                 46947  1 hid_logitech_dj
hid                   100366  3 hid_logitech_dj,hid_generic,usbhid
firewire_ohci          40401  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_marvell           12912  0 
sky2 

***iwconfig***
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

***rfkill list***
didnt show anything.

```

---

### Post by jannk on 2013-02-09
> **chili555 said:**
> Did you see this? [http://askubuntu.com/questions/193319/missing-driver-asus-pce-n53-11n-n600-pci-e-adapter](http://askubuntu.com/questions/193319/missing-driver-asus-pce-n53-11n-n600-pci-e-adapter)

Did try it but since i'm no pro with linux/ubuntu, i did not get it rite. Will try again and see if i can figure it out.

I readed this though.

*I got a response from Asus saying only kernel  version 2.6.x is supported and that newer kernel version might be  incompatible and that they do not have any timeline for when a new  driver will released. In other words the solution is probably to  downgrade Ubuntu version (not something I am willing to do) or get a new  wireless card :(*

So i'm not sure if it will work on 12.04 sadly. I got 3.5.xx. If it's my current kernel?.

Gonna check out the patch link and see.

---

### Post by chili555 on 2013-02-09
> **jannk said:**
> Did try it but since i'm no pro with linux/ubuntu, i did not get it rite. Will try again and see if i can figure it out.We will be happy to help you identify the problem if you post the error here.

---

### Post by jannk on 2013-02-09
> **chili555 said:**
> We will be happy to help you identify the problem if you post the error here.
Thanks,

Well first of all i can't install the build essential as suggested from that site the guy above suggested. I tried go to ubuntu site and dl it and ported it over to the desktop pc via USB. But when tried run it it went to the software center and no internett so can't dl it..

I have dl the asus drivers for the wifi card for linux and also downloaded the patch file and ported it into the folder. Tried that command in the terminal, that was suggested on that site.

tar -jxvf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2

Did not work though. This came up.

```

No such file or directory
tar (child): Error is not recoverable: exiting now
tar: child returned status 2
tar: Error is not recoverable: exiting now

```

So how do i get the build essential into the desktop without any form for wifi.
Can't cable i-nett to it either unfortanly.

I think it's close now, if i yust can get the drivers installed this will go good. But a little help there hehe.

---

### Post by chili555 on 2013-02-09
build-essential is a package that depends on many others; see all the red dots here: [http://packages.ubuntu.com/quantal/build-essential](http://packages.ubuntu.com/quantal/build-essential) Be sure to get the amd64, also known as 64-bit versions.

You will need to download and install all those as well. Drag and drop them from your USB key to your desktop. Then do:```
cd Desktop
sudo dpkg -i *.deb
```You will also need this: [http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17-generic](http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17-generic)

If not already installed, get those dependencies (red dots) as well. Install as above.> tar -jxvf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.b z2Is there an unneeded space in there? Does it work with:```
cd Desktop
tar -jxvf DPO_GPL_RT5592STA
```Press Tab and the rest should fill in automatically. Press Enter.

---

### Post by jannk on 2013-02-09
> **chili555 said:**
> build-essential is a package that depends on many others; see all the red dots here: [http://packages.ubuntu.com/quantal/build-essential](http://packages.ubuntu.com/quantal/build-essential) Be sure to get the amd64, also known as 64-bit versions.

You will need to download and install all those as well. Drag and drop them from your USB key to your desktop. Then do:```
cd Desktop
sudo dpkg -i *.deb
```You will also need this: [http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17-generic](http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17-generic)

If not already installed, get those dependencies (red dots) as well. Install as above.Is there an unneeded space in there? Does it work with:```
cd Desktop
tar -jxvf DPO_GPL_RT5592STA
```Press Tab and the rest should fill in automatically. Press Enter.

I belive i installed all the packages. Desktop and did the command and they installed. But, when i tried the first command the same code as i wrote above (child) appeared.

I tried the command you gave me tar etc and also tried the tab along the way but no others letters where shown.

Got the same error message as above. Hmm.

When i download the red dot packages, i went the first then the package under, i do need to do this with every package i assume?

If so i'll try again and download the packages.

---

### Post by chili555 on 2013-02-09
> I tried the command you gave me tar etc and also tried the tab along the way but no others letters where shown.Where is the package? On your desktop?```
cd Desktop
```Now let's list the contents:```
ls
```Is the file there?> DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2If so,try again:> ```
tar -jxvf DPO_GPL_RT5592STA
```

Press Tab and the rest should fill in automatically. Press Enter.If it is not on your desktop, where is it??

---

### Post by jannk on 2013-02-09
> **chili555 said:**
> 
I tried once more. Downloaded all the packages and moved the driver to the desktop and used tab and the name came up, enter and this came up.

```

jannis@jannis:~/Desktop$ tar -jxvf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tar (child): DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/: Cannot read: Is a directory
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error is not recoverable: exiting now

```

---

### Post by jannk on 2013-02-09
> **chili555 said:**
> If so,try again:If it is not on your desktop, where is it??
Yeah, it was in my download folder, my mistake sry. Moved to desktop as stated over. :)

The wireless icon on top right courner went to a traffic sign, red with white line across. Says an error occurd, please run package manager...

Might done some **** here. Meh. I have the packages and the drivers so ill stick it to a usb and reinstall ubuntu and try again and see what happends.

---

### Post by jannk on 2013-02-09
> **chili555 said:**
> .

Okey, reinstalled ubuntu 12.04 and reinstalled all the packages and the drivers from the desktop.

It worked flawlessly.

Now, i have come to the point to 

*quote* Enter the new directory and start make.

make

How do i do that exaclty?

*edit* Tried to write "make" after the last command. But only came up , make: *** No targets specified and no makefile found.  stop.

Guess i have to direct it somewhere but little clueless here, on the site that that guy got a solution, it only say "enter the new directory and start make"  And in grey dye under it is written "make"  but as writed nothing happends.  I'm learning tho. I will do some more research untill you gte back to me.

---

### Post by chili555 on 2013-02-09
> *quote* Enter the new directory and start make.

make

How do i do that exaclty?When you extracted the tar.bz2, it created a folder and we will enter that folder in the terminal:```
cd ~/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326
```And now simply do:```
make
```And then complete the instructions from the link I gave you. If you get an error, stop and post it here. There is no point in continuing after you see that awful word: ERROR.

---

### Post by jannk on 2013-02-09
> **chili555 said:**
> When you extracted the tar.bz2, it created a folder and we will enter that folder in the terminal:```
cd ~/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326
```And now simply do:```
make
```And then complete the instructions from the link I gave you. If you get an error, stop and post it here. There is no point in continuing after you see that awful word: ERROR.

Worked it seemed. Rebooted but no network so. Though the patch file aint in .tar folder most likely. Possible to find the folder and yust put it in there?

If not then i'll guess no wifi. Anyways thanks for the help man.

---

### Post by chili555 on 2013-02-09
> If not then i'll guess no wifi. Anyways thanks for the help man.*I guess no wifi?* Giving up so soon? Not me. Let me study this a bit and I'll post back in a few minutes.

We're not even up to 100 posts yet!!

EDIT: Before we worry about the patch, were there any errors in make or sudo make install? What is the result of:```
sudo modprobe rt5592sta
```After you rebooted, if you load the module, does it work?```
sudo modprobe rt5592sta
```Are there any interesting clues here?```
dmesg | grep rt5
```

---

### Post by praseodym on 2013-02-09
Did you install the kernel-headers?

```
sudo apt-get install linux-headers-generic linux-headers-$(uname -r)
```
Also try the installation as "root":
```

make clean
sudo su
make
make install
exit
```

---

### Post by jannk on 2013-02-09
> **chili555 said:**
> *I guess no wifi?* Giving up so soon? Not me. Let me study this a bit and I'll post back in a few minutes.

We're not even up to 100 posts yet!!

Na not really giving up, kinda lost for options hehe. But i don't want to bother you with this you know if your busy. :)

---

### Post by jannk on 2013-02-09
> **praseodym said:**
> Did you install the kernel-headers?

```
sudo apt-get install linux-headers-generic linux-headers-$(uname -r)
```Also try the installation as "root":
```

make clean
sudo su
make
make install
exit
```

Since i not got wifi on the desktop pc i cant sudo apt-get install it.
But i think i got all the packages.

In total i got 9 packages i downloaded. I assume the underlying folders of the red dots was in thoose?

*edit* 
I see now i might have downloaded to little packages.

Correct me if i'm wrong.

1. I went to the [http://packages.ubuntu.com/quantal/build-essential](http://packages.ubuntu.com/quantal/build-essential)
2.downloaded the bottom amd63
3.Hit'd the first red dot and more dots appeared.
4. went to bottom and download the 64.
5.went back and did the same with the 4 rest spots on the main page.

Do i need to get every induvidial package under every induvidial red dot? or do the apply and it's ok that i did from point 1-5 ?

---

