---
title: "Wired connection stopped working after updating"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by fknyeah on 2011-07-13
So I updated to 11.04 and fixed my wireless, but then realized that my computer wouldn't connect to the web through a cable, and now I'm perplexed to say the least.

---

### Post by varunendra on 2011-07-15
Please post the outputs of:
```
sudo lshw -C network
```
```
ifconfig
```
```
route -n
```

Before doing this, you may try to boot into recovery mode and try **dpkg **option to fix broken packages if any.

---

### Post by fknyeah on 2011-07-18
```
~$ sudo lshw -C network 

  *-network UNCLAIMED      
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:f9ffc000-f9ffffff 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list 
       configuration: latency=64 
       resources: memory:f9bfe000-f9bfffff 

~$ ifconfig 

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:2640 (2.6 KB)  TX bytes:2640 (2.6 KB) 

~$ route -n 

Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
```

---

### Post by varunendra on 2011-07-19
May be I didn't understand you correctly, but you said your wireless was fixed after the update. But your lshw output shows both your network interfaces "Unclaimed" - meaning no drivers attached with them. So are you sure the wireless is working?

If not, there are many possible fixes proposed here: [http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working](http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working)

Please confirm if it is both or only the ethernet interface not working.

---

### Post by fknyeah on 2011-07-19
The wireless was working for a little while, but now I have **no** means of getting onto the internet on my computer.

---

### Post by varunendra on 2011-07-20
For WiFi, try the link in my previous post.
For Ethernet, try this: [http://askubuntu.com/questions/14970/broadcom-bcm4401-b0-100base-tx-issues](http://askubuntu.com/questions/14970/broadcom-bcm4401-b0-100base-tx-issues)

There was a bug in natty initially which caused problems with ethernet, but it is said to be fixed in beta1 version of natty: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/738812](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/738812)

Try above suggestions first. If none of these work, please post the errors you get and the outputs of-
```
lsmod
```
and
```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by fknyeah on 2011-07-24
lsmod:

Module                  Size  Used by 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat 
usb_storage            43946  1 
uas                    17676  0 
binfmt_misc            13213  1 
rfcomm                 38125  8 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep 
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
nvidia               9766978  44 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep              13274  1 snd_hda_codec 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              28659  2 snd_pcm,snd_seq 
btusb                  18160  2 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi 
r852                   17878  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb 
uvcvideo               66851  0 
sm_common              16737  1 r852 
dell_laptop            13515  0 
nand                   49822  2 r852,sm_common 
dcdbas                 14054  1 dell_laptop 
nand_ids                8547  1 nand 
nand_ecc               13070  1 nand 
videodev               75143  1 uvcvideo 
video                  18951  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
mtd                    26720  2 sm_common,nand 
psmouse                73312  0 
serio_raw              12990  0 
firewire_sbp2          18303  0 
soundcore              12600  1 snd 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp 
usbhid                 41704  0 
hid                    77084  1 usbhid 
firewire_ohci          31504  0 
firewire_core          56138  2 firewire_sbp2,firewire_ohci 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci 
crc_itu_t              12627  1 firewire_core 



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
#blacklist bcm43xx

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

---

### Post by fknyeah on 2011-07-24
I should mention I also get this error:

 sudo apt-get remove bcmwl-kernel-source

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk2.0-0-dbg evolution-data-server-dbg kdelibs4c2a libgsf-gnome-1-114
  rhythmbox-dbg gstreamer0.10-plugins-base-dbg liboobs-1-5-dbg libatk1.0-dbg
  libgda-4.0-common libgsf-1-114-dbg libgoffice-0.8-8-common libdevhelp-2-1
  libgdata1.7-cil evince-dbg libpango1.0-0-dbg libgnomevfs2-0-dbg libopts25
  epiphany-browser-data libmono-zeroconf1.0-cil python-pyxattr kdelibs-data
  libopts25-dev evolution-dbg libgkeyfile1.0-cil autogen eog-dbg libatspi-dbg
  libgda-4.0-4-dbg liblualib50 autoconf python-dbg anjuta-common libgdl-1-dbg
  libboost-thread1.42.0 libnss3-dbg libxft2-dbg libboost-date-time1.42.0
  libubuntuone1.0-cil python-cairo-dbg libfontconfig1-dbg python-gtkspell
  libgtk-sharp-beans-cil libgoffice-0.8-8 libloudmouth1-0 libsvn1 intltool
  libtool libgoffice-dbg anjuta libgsf-gnome-1-114-dbg devhelp-common
  anjuta-dbg gstreamer0.10-plugins-ugly-dbg libgda-4.0-4 libavahi-qt3-1
  gstreamer0.10-plugins-good-dbg libtaglib2.0-cil autotools-dev
  libloudmouth1-0-dbg libnspr4-dbg libxml2-dbg gnome-panel-dbg python2.6-dbg
  libgnomecanvas2-dbg libasyncns0 nautilus-dbg rdiff-backup libgudev1.0-cil
  python-numpy-dbg automake libwebkitgtk-1.0-0-dbg libgtkhtml3.14-dbg
  python-pylibacl gnash libanjuta0 gnome-applets-dbg librsvg2-dbg
  libgnomeui-0-dbg libqt3-mt libglib2.0-0-dbg libgnome2-dbg liblua50
  gnash-common totem-dbg libltdl-dev libaprutil1 libgail-gnome-dbg librsync1
  python2.7-dbg libvala-0.12-0 libgdl-1-3 gimp-dbg python-gobject-dbg
  libnotify0.4-cil python-gtk2-dbg libgdl-1-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,597 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 242202 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Setting up firmware-b43-installer (4.150.10.5-5) ...
--2011-07-24 19:06:30--  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
Resolving mirror2.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `mirror2.openwrt.org'
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wildmanne39 on 2011-07-24
Hi, your issue looks complicated, I am going to give you a link to install the wireless driver it can be done without an internet connection.

Right now you do not have any wireless drivers being used.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

