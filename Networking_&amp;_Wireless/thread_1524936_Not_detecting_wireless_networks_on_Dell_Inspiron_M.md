---
title: "Not detecting wireless networks on Dell Inspiron Mini 10"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by CreamCheesey on 2010-07-06
Hi all,

I recently installed Ubuntu Netbook Remix on my Dell Inspiron Mini 10, and for some reason it isn't detecting any wireless networks. The wireless works perfectly fine when I boot to Windows XP on the netbook, but not when I'm using Ubuntu. 

I tried troubleshooting using this [https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)
At the "check for device recognition" step, the terminal tells me that it's disabled, but as far as I can tell there isn't a physical switch that allows me to turn the wireless on or off, and again, it works perfectly fine when I use XP. What should I do?

---

### Post by roosh on 2010-07-06
Hi,

Please open a terminal and type the following seperately and post back the output of each:
 ```
lspci
``` ```
lsusb
``` ```
lsmod
```

---

### Post by CreamCheesey on 2010-07-06
For lspci:

```

00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

For lsusb:

```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 174f:1403 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

For lsmod:

```

Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dell_wmi                1793  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
uvcvideo               56990  0 
b43                   157218  0 
compal_laptop           2034  0 
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
videodev               34361  1 uvcvideo
mac80211              204922  1 b43
softcursor              1189  1 bitblit
dcdbas                  5422  0 
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54148  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
cfg80211              126485  2 b43,mac80211
led_class               2864  1 b43
serio_raw               3978  0 
soundcore               6620  1 snd
vga16fb                11385  1 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
vgastate                8961  1 vga16fb
i2c_isch                3311  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39425  0 
r8169                  33884  0 
pata_sch                1963  2 
mii                     4381  1 r8169
ssb                    37336  1 b43

```

---

### Post by mikewhatever on 2010-07-06
It appears that the driver for BCM4312 and other Broadcom wireless cards is restricted in some way, and therefore, not enabled by default. The formal way to go about it would be to hook up an ethernet cable, then open System->Admin->Hardware-Drivers and install the driver recommended for your wireless card. Once enabled, the wireless works well.

---

### Post by roosh on 2010-07-06
If what mikewhatever said doesn't work, try this: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Keep in mind your model of wireless is Broadcom BCM4312.

---

### Post by henhen on 2010-07-06
Hello,

On my Compaq Mini I also had problems with the wireless network and have been able to resolve them.

I made a little manual. Hope it helps for you.

[FONT=Courier New]CONFIGURE BROADCAM WIRELESS on UBUNTU LUCID
-------------------------------------------

INTRODUCTION
------------
This little manual describes how to configure BROADCAM WIRELESS
on a PC on which the wireless connection is not working and
that has no other network connection. I was having this
problem on a Compaq Mini.

The procedure described here is entirely based upon the 
broadcom documentation (readme). If you have problems,
please consult this documentation. It is very good.

The procedure is tested with kernel 2.6.32-23-generic.

You need to dispose of two PC's with the same kernel version.

On one PC (with working internet connection) you download 
the necessary files and build the driver.

After this, you transfer the files to the PC without network and 
startup the driver.

SUPPORTED DEVICES
-----------------
The cards with the following PCI Device IDs are supported with this driver.
Both Broadcom and and Dell product names are described.  Cards not listed here
may also work.

       BRCM            PCI          PCI          Dell
      Product Name      Vendor ID    Device ID    Product ID
          -------------     ----------    ---------       -----------
          4311 2.4 Ghz        0x14e4    0x4311      Dell 1390
          4311 Dualband        0x14e4    0x4312      Dell 1490
          4311 5 Ghz        0x14e4        0x4313      
          4312 2.4 Ghz        0x14e4    0x4315      Dell 1395
          4313 2.4 Ghz        0x14e4    0x4727         Dell 1501
          4321 Dualband        0x14e4    0x4328      Dell 1505
          4321 Dualband        0x14e4    0x4328      Dell 1500
          4321 2.4 Ghz        0x14e4    0x4329      
          4321 5 Ghz        0x14e4    0x432a      
          4322     Dualband    0x14e4    0x432b      Dell 1510
          4322 2.4 Ghz      0x14e4     0x432c      
          4322 5 Ghz        0x14e4     0x432d      
          43224 Dualband    0x14e4    0x4353      Dell 1520
          43225 2.4 Ghz     0x14e4    0x4357      

To find the Device ID's of Broadcom cards on your machines do:
# lspci -n | grep 14e4

DOWNLOAD
--------
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

There are separate tarballs for 32 bit and 64 bit x86 CPU architectures.
Make sure you use the appropriate tarball for your machine. I've only
tested the 32 bit version.

Also, download the kernel 2.6.33 patch 
(sta_5.60.48.36_2.6.33_kernel_patch.zip)

If you want you can download the readme file, although it is included in the
tarballs.

BUILD
-----
Make sure that both the pc on which you download and compile the driver
(PC1) and the pc on which you want to install the driver (PC2) have 
the same kernel version. To check:

# uname -r

On PC1 you will need headers and tools.  Try these commands:

# sudo apt-get install build-essential linux-headers-generic
# sudo apt-get build-dep linux

To check to see if you have this directory do this:

# ls /lib/modules/`uname -r`/build

BUILD INSTRUCTIONS
------------------
1. On PC1, setup the directory by untarring the proper tarball:

For 32 bit:     hybrid-portsrc.tar.gz
For 64 bit:     hybrid-portsrc-x86_64.tar.gz

# mkdir hybrid_wl
# cd hybrid_wl
# sudo tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz

2. Install the patch

On PC1, open sta_5.60.48.36_2.6.33_kernel_patch.zip
copy the file 'patch' to the top level of hybrid_wl. 
('ls' should show src, lib, Makefile, etc)

# patch -p0 < patch

3. On PC1, build the driver as a Linux loadable kernel module (LKM):

# sudo make clean   (optional)
# sudo make

When the build completes, it will produce a wl.ko file in the top level
directory.

INSTALL INSTRUCTIONS
--------------------

Fresh installation:
------------------
1: On PC2 (the PC without network connection), remove any other drivers for 
the Broadcom wireless device.

# sudo lsmod  | grep "b43\|ssb\|wl"

If any of these are installed, remove them:
# sudo rmmod b43
# sudo rmmod ssb
# suco rmmod wl

To blacklist these drivers and prevent them from loading in the future:
# sudo echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# sudo echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf

2: Transfer the driver

Using a USB stick, external HD, ..., copy the hybrid_wl directory from
PC1 to a convenient place on PC2. Check permissions of the files on PC2.

3: On PC2, insmod the driver.

If you have not previously installed a wl driver, you'll need
to add a security module before using the wl module.  Most newer systems 
use lib80211 while others use ieee80211_crypt_tkip. See which one works for 
your system.

# sudo modprobe lib80211 
  or 
# sudo modprobe ieee80211_crypt_tkip

Then:
# sudo insmod <path to hybrid_wl>/wl.ko

wl.ko is now operational.  It may take several seconds for the Network 
Manager to notice a new network driver has been installed and show the
surrounding wireless networks.

STARTUP
-------
Each time you start your PC, you'll need to execute the above 
modprobe and insmod instructions. You can - of course - make a shell
script and a starter to make it more easy.



[/FONT]

---

### Post by CreamCheesey on 2010-07-06
mikewhatever's suggestion worked. Thanks for all your help everyone!

---

### Post by Jurguens on 2010-07-06
I've just bought a Dell Inspiron Mini 1012. It came with Windows 7 but I installed the latest Ubuntu Netbook Remix. 

I'm a complete newbie with Linux. The installation went really well and I was very happy and impressed... but, the wireless connection doesn't work.

I've tried everything, and now the it recogniness my router and the connection is established, but when I open Firefox it can't even open the most basic page.

Please help

---

### Post by roosh on 2010-07-07
It could be that you don't have internet access at all. Try connecting your computer with a wired connection without the router.

---

### Post by Jurguens on 2010-07-07
Thanks for your reply. The modem/router is working fine. I can access it with windows 7 on the same computer, and with my mac. The fault is evidently with ubuntu.

I installed the os, then updated it through a wired connection. It finds the router, and it says it establishes the connection, but for some reason it doesn't read any data. 

Weird. 

So for the moment I'm stuck with the pretty horrible and slow windows 7. 

Any ideas will be much appreciated.

---

### Post by roosh on 2010-07-07
Ok. Please open a terminal, and run each of the following commands; then post back the output:
```
lsusb
``` ```
lspci
``` ```
lsmod
```

---

### Post by Jurguens on 2010-07-07
Thanks Roosh! Here it goes...

lsusb: 

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 413c:8160 Dell Computer Corp. 
Bus 004 Device 004: ID 413c:8162 Dell Computer Corp. 
Bus 004 Device 003: ID 413c:8161 Dell Computer Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 0c45:641d Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lspci:
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


lsmod:
Module                  Size  Used by
ipt_MASQUERADE          1407  1 
xt_state                1098  1 
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          2271  1 
nf_nat_h323             5077  0 
nf_conntrack_h323      46926  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4413  1 nf_nat_pptp
nf_conntrack_proto_gre     4021  1 nf_conntrack_pptp
nf_nat_proto_gre        1259  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
iptable_nat             4414  1 
nf_nat                 15735  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat
nf_conntrack           61583  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9991  2 iptable_filter,iptable_nat
x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
michael_mic             1732  4 
arc4                    1153  2 
binfmt_misc             6587  1 
ppdev                   5259  0 
rfcomm                 33421  4 
sco                     7885  2 
snd_hda_codec_realtek   203310  1 
bridge                 45582  0 
stp                     1655  1 bridge
joydev                  8708  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
bnep                    9436  2 
snd_hda_intel          21941  2 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
l2cap                  30624  16 rfcomm,bnep
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi                1793  0 
lib80211_crypt_tkip     7596  0 
i915                  285076  4 
uvcvideo               56990  0 
dell_laptop             6856  0 
soundcore               6620  1 snd
wl                   1959598  0 
drm_kms_helper         29297  1 i915
intel_agp              24119  2 i915
dcdbas                  5422  1 dell_laptop
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63245  0 
serio_raw               3978  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
drm                   162377  5 i915,drm_kms_helper
agpgart                31724  2 intel_agp,drm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
usb_storage            39425  0 
ahci                   32168  2 
r8169                  34076  0 
mii                     4381  1 r8169

---

### Post by roosh on 2010-07-08
It looks like you have the exact same problem as the author of this thread. All you should need to do is make sure you're connected to the Internet with a wired connection and go to system --> administration --> hardware drivers and then install the driver it recommends.

---

### Post by roosh on 2010-07-08
Out of curiosity, is Windows 7 really that slow and horrible? I thought it was Vista that had all of the problems.

---

### Post by Jurguens on 2010-07-08
I did that. The Broadcom STA proprietary wireless driver is active. The problem remains.

I also tried connecting at different wi-fi spots (work and at a friend's house). The same thing happened, it establishes the connection, it shows a healthy signal, but the internet doesn't work. 

Any other ideas?

In regards to windows 7 - from what I've heard from friends, it works fine with normal computers. I found it slow on the netbook. Ubuntu works better - apart from this problem I'm having that is.

---

### Post by Jurguens on 2010-07-08
I forgot to say I had two options for drivers: 

Broadcom B43 wireless driver
Broadcom STA wireless driver

Which one would you recommend?

---

### Post by roosh on 2010-07-09
I really don't know which one. Why don't you try the other one and then see what happens. If both of them don't work, try this guide while keeping in mind your card is BCM4312: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Chris1274 on 2010-07-09
I had that problem earlier (driver enabled, wifi working, but no internet). Try configuring Firestarter, then reboot. That's what worked for me at any rate.

As for which drivers, I have a weird story. When I first installed 10.04, the B43 driver worked. Then I had to reinstall (don't ask why, I'll only say that newbies should think twice about playing with sudo commands), and discovered that the B43 driver no longer worked, only the STA driver.

---

### Post by bkratz on 2010-07-09
You also may want to check into this posting ... It was still good last time I tried.

[http://ubuntuforums.org/showpost.php?p=9134672&postcount=6](http://ubuntuforums.org/showpost.php?p=9134672&postcount=6)

---

