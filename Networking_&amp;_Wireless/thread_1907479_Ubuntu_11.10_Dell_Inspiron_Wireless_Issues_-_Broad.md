---
title: "Ubuntu 11.10 Dell Inspiron Wireless Issues - Broadcom BCM4312"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by redeemer on 2012-01-11
Hi,

I upgraded to 11.10 recently from 10.04 (incremental upgrades through each version). Facing the wireless issues that everyone else has -- if I click on the networking icon in the top right, "Enable Wireless" is greyed out and unclickable. Wired ethernet connectivity is fine. 

I've seemingly followed most of the steps from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") and [http://ubuntuforums.org/showthread.php?t=1604868]("http://ubuntuforums.org/showthread.php?t=1604868").

Here are some outputs that cover the approaches outlined in the above two links:

```

tom@squires:~$ uname -a && lsmod && lspci -vnn | grep 14e4
Linux squires 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
binfmt_misc            17292  1 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
psmouse                63474  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
wmi                    18744  1 dell_wmi
snd_timer              28932  2 snd_pcm,snd_seq
video                  18908  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                961834  3 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
b43                   318816  0 
drm                   196290  5 radeon,ttm,drm_kms_helper
mac80211              393459  1 b43
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 radeon
cfg80211              172392  2 b43,mac80211
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
ahci                   21634  2 
libahci                25761  1 ahci
ssb                    50682  1 b43
sky2                   49304  0 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [**14e4:4315**] (rev 01)
tom@squires:~$ 

```

```

tom@squires:~$ sudo apt-get install firmware-b43-installer
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**firmware-b43-installer is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
tom@squires:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**b43-fwcutter is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
tom@squires:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Package bcmwl-kernel-source is not installed, so not removed**
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
tom@squires:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
**b43**
tom@squires:~$

```

```

tom@squires:~$ cat /etc/modprobe.d/blacklist.conf 
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
tom@squires:~$

```

```

tom@squires:~$ sudo lshw -C network 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:3d:15:85
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f6bfc000-f6bfffff ioport:ce00(size=256)
  *-network** DISABLED**
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:b0:94:f9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-14-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
tom@squires:~$

```

[IMG]http://img.photobucket.com/albums/v28/causticwindow/Screenshotat2012-01-11183505.png[/IMG]

It could be that I've setup a bad combination of a number of solutions, or that I'm missing something. I read in one post that the order in which I install/uninstall the drivers (firmware-b43-installer, b43-fwcutter, bcmwl-kernel-source) could be relevant? Dumb question, but once they are installed, what do I need to do to activate them? I don't see them listed on Additional Drivers (see above screenshot). Is there a command I need to manually issue? What about my blacklist file?

Either way - I would really appreciate some help with this! Very frustrating. :(

---

### Post by redeemer on 2012-01-11
Some more command outputs:

```

tom@squires:~$ sudo iwconfig && sudo ifconfig -a wlan0 && sudo iwlist wlan0 scanning
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
wlan0     Link encap:Ethernet  HWaddr 00:22:5f:b0:94:f9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Interface doesn't support scanning : Network is down

tom@squires:~$

```

---

### Post by redeemer on 2012-01-11
Oh man... FML! So, I solved it.

I stumbled upon [**this thread**]("http://ubuntuforums.org/showthread.php?t=1780261"). My Dell Inspiron laptop has a bunch of mappings for the F-keys that override the usual functionality. My F2 key is set (out of the box) to toggle wireless on and off. I must have hit it at some point which disabled wireless.

After I pressed it once, a popup appeared in the top right on the toolbar saying there were new drivers available for my device. I went to the 'Additional Drivers' section and activated the 'Broadcom STA proprietary wireless driver' section - my device woke up instantly (without reboot) and I am now successfully surfing wirelessly!

Sheesh.... :oops:

---

