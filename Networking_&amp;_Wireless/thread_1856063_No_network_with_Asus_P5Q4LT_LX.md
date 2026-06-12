---
title: "No network with Asus P5Q4LT LX"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by suxilo53 on 2011-10-07
Dears,

I'm approaching to the interesting ubuntu/linux world after losing many years of my life on Windows.
Considering that I ask you to tolerate my ignorance concerning running commands in ubuntu termnal... :D

I explain my problem.
I changed MB of my workstation due to hardware failure and when I startup the system with a new MB my network doesn't work anymore.

Old MB Asus P5Q
New MB Asus P5Q4LT LX

I searched info on the network but I didn't found any concrete solution of my problem.

This is the situation of my ubuntu concerning network.

*-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:feac0000-feafffff ioport:dc00(size=128)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

Could you kindly help me?
Thank you in advance guys....

---

### Post by praseodym on 2011-10-07
Hello,

please show the outputs of the following terminal commands (copy/paste):

```
uname -a
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by suxilo53 on 2011-10-09
Here the result of command...

    uname -a
Linux suxilo-ubuntu1 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux

   lspci  -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
04:01.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 61)
    Kernel driver in use: uhci_hcd

lsmod
Module                  Size  Used by
isofs                  29250  1 
udf                    78785  0 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vboxdrv               168753  2 vboxnetadp,vboxnetflt
vmnet                  40981  10 
ppdev                   5259  0 
parport_pc             25962  0 
vmblock                10766  1 
vsock                  37367  0 
vmci                   53002  1 vsock
vmmon                  62872  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  0 
joydev                  8740  0 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
hid_logitech            7388  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                677684  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ff_memless              4093  1 hid_logitech
ttm                    49943  1 radeon
drm_kms_helper         29329  1 radeon
asus_atk0110            9017  0 
snd                    54244  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 36110  1 hid_logitech
hid                    67096  2 hid_logitech,usbhid
psmouse                63245  0 
serio_raw               3978  0 
intel_agp              24375  0 
drm                   162377  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  3 ttm,intel_agp,drm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp

---

### Post by praseodym on 2011-10-09
You need to install the driver by hand. Download the following files and install them by double clicking:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24-generic_2.6.32-24.43_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24-generic_2.6.32-24.43_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24_2.6.32-24.43_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24_2.6.32-24.43_all.deb)

After that add the CD/DVD to your software sources and install the packages **dkms** and **build-essential**

```
sudo mkdir /usr/src/atl1e-1.0.1.14 
```
Unpack the attached driver (folder name just ".") to the folder **/usr/src/atl1e-1.0.1.14** via

```
gksu nautilus
```
and install it with dkms:

```
sudo dkms add -m atl1e -v 1.0.1.14
sudo dkms build -m atl1e -v 1.0.1.14 
sudo dkms install -m atl1e -v 1.0.1.14 
sudo depmod -a
sudo modprobe -v atl1e
```
After that you should update your system. The driver should be automatically build for the new kernel (2.6.32-34):
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic
```

---

