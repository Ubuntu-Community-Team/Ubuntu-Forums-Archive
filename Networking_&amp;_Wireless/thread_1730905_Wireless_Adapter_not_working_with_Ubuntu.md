---
title: "Wireless Adapter not working with Ubuntu"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by pawan98 on 2011-04-16
Hi, my Wireless adapter is not working with ubuntu, I tried my friend's adapter, and it worked, it came up with all the router's I could connect to, but when I try my one, it doesn't come up. The model/make of my device is - Realtek RTL8191SU. Please help!

---

### Post by josephmills on 2011-04-16
> **pawan98 said:**
> Hi, my Wireless adapter is not working with ubuntu, I tried my friend's adapter, and it worked, it came up with all the router's I could connect to, but when I try my one, it doesn't come up. The model/make of my device is - Realtek RTL8191SU. Please help!

please plug in the wifi thingy and copy and paste a ```
lsusb
``` thanks

---

### Post by Hippytaff on 2011-04-16
you might want to download and run the wireless script (link below) it will return all relevant info which you can post here for people to be able to help, and it will try to fix common problems, but with ralink it's usually a driver thing.

---

### Post by pawan98 on 2011-04-16
Hi, Thanks for replying.


pawan@Pawan-Desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 001 Device 004: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pawan@Pawan-Desktop:~$

---

### Post by pawan98 on 2011-04-16
Hi Hippytaff,


Version: 1.1 (Development)
Sat Apr 16 20:31:36 BST 2011

***********************************************************************************************
Running networking services
***********************************************************************************************
NetworkManager is running
************************************
        Ubuntu release 
************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

************************************
        Kernel
************************************

Linux Pawan-Desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
************************************
          List of drivers
************************************

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
usb_storage            39425  1 
nls_utf8                1069  0 
udf                    78785  0 
crc_itu_t               1371  1 udf
snd_usb_audio          75765  1 
snd_usb_lib            15658  1 snd_usb_audio
snd_hwdep               5412  1 snd_usb_audio
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  18 snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
i915                  282354  3 
soundcore               6620  1 snd
dell_wmi                1793  0 
drm_kms_helper         29297  1 i915
parport_pc             25962  1 
gspca_zc3xx            45189  0 
gspca_main             21199  1 gspca_zc3xx
dcdbas                  5422  0 
r8192s_usb            346007  0 
psmouse                63245  0 
serio_raw               3978  0 
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24177  2 i915
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
lp                      7028  0 
videodev               34361  1 gspca_main
v4l1_compat            13251  1 videodev
video                  17375  1 i915
output                  1871  1 video
shpchp                 28820  0 
agpgart                31724  2 drm,intel_agp
parport                32635  3 ppdev,parport_pc,lp
e1000                  97396  0 
floppy                 53016  0 

************************************
        pci wireless devices
************************************


************************************
        usb wireless devices
************************************


************************************
        List of network devices
************************************

  *-network
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:0f:1f:7a:1b:b9
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:a1:b0:e1:0b:1f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g


************************************
           network info
************************************

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:7a:1b:b9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12792 (12.7 KB)  TX bytes:12792 (12.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:e1:0b:1f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


************************************
 Wireless specific network info
************************************

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

************************************
 Rfkill Blocks
************************************


************************************

*************************************************************************
interfaces
*************************************************************************
auto lo
iface lo inet loopback


**************************************************************************
resolv.conf
**************************************************************************

**************************************************************************
Modules file
**************************************************************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

*************************************************************************
Blacklist file
*************************************************************************
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

**************************************************************************
Files in folder /etc/modprobe.d/*
**************************************************************************
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-watchdog.conf
/etc/modprobe.d/libpisock9.conf

***************************************************************************
NetworkManager.state
***************************************************************************

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

****************************************************************************
nm_applet_file
*****************************************************************************
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

Finished <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

---

### Post by josephmills on 2011-04-16
I think that hippietaft is right that it is a driver thing. lets see a ```
ifconfig
``` please take out ip address and HWaddr thanks
EDIT: nevermind

---

### Post by josephmills on 2011-04-16
with the wifi thingy plugged in please post 
```
rfkill list
```thanks

---

### Post by pawan98 on 2011-04-16
i done the rfkill list thing nothing came up.

---

### Post by josephmills on 2011-04-16
> **pawan98 said:**
> i done the rfkill list thing nothing came up.

are you connected to you router via cat5 cable?

---

### Post by josephmills on 2011-04-16
try ```
sudo apt-get install rfkill
``` then ```
rfkill list
```

---

### Post by pawan98 on 2011-04-16
No, I do not have internet access on my other computer I am using another computer. Therefore the apt-get command will not work.

---

### Post by josephmills on 2011-04-16
darn its going to be hard to help (for me) without that. Who know's you might just have too update and upgrade and find a driver. I think that you can download the driver then bring it over to your ubuntu box via thumb drive. but am not sure (im a noob) well at any rate hope that someone else jumps in and I can learn from this too. thanks

---

### Post by walt.smith1960 on 2011-04-16
I wonder if this is related to the RTL8192SU problem?  You could run "dmesg" in a terminal and see if there are any messages about missing firmware. If not, no harm done.

---

### Post by Hippytaff on 2011-04-16
a bit late but code tags```
Version: 1.1 (Development)
Sat Apr 16 20:31:36 BST 2011

**************************************************  *********************************************
Running networking services
**************************************************  *********************************************
NetworkManager is running
************************************
        Ubuntu release 
************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

************************************
        Kernel
************************************

Linux Pawan-Desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
************************************
          List of drivers
************************************

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
usb_storage            39425  1 
nls_utf8                1069  0 
udf                    78785  0 
crc_itu_t               1371  1 udf
snd_usb_audio          75765  1 
snd_usb_lib            15658  1 snd_usb_audio
snd_hwdep               5412  1 snd_usb_audio
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_  oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
snd                    54148  18  snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ac97_code   c,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,sn   d_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
i915                  282354  3 
soundcore               6620  1 snd
dell_wmi                1793  0 
drm_kms_helper         29297  1 i915
parport_pc             25962  1 
gspca_zc3xx            45189  0 
gspca_main             21199  1 gspca_zc3xx
dcdbas                  5422  0 
r8192s_usb            346007  0 
psmouse                63245  0 
serio_raw               3978  0 
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24177  2 i915
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
lp                      7028  0 
videodev               34361  1 gspca_main
v4l1_compat            13251  1 videodev
video                  17375  1 i915
output                  1871  1 video
shpchp                 28820  0 
agpgart                31724  2 drm,intel_agp
parport                32635  3 ppdev,parport_pc,lp
e1000                  97396  0 
floppy                 53016  0 

************************************
        pci wireless devices
************************************


************************************
        usb wireless devices
************************************


************************************
        List of network devices
************************************

  *-network
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:0f:1f:7a:1b:b9
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000  driverversion=7.3.21-k5-NAPI firmware=N/A latency=64 link=no mingnt=255  multicast=yes port=twisted pair
       resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:a1:b0:e1:0b:1f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g


************************************
           network info
************************************

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:7a:1b:b9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12792 (12.7 KB)  TX bytes:12792 (12.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:e1:0b:1f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


************************************
 Wireless specific network info
************************************

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Encryption key:eek:ff
          Power Management:eek:ff
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

************************************
 Rfkill Blocks
************************************


************************************

**************************************************  ***********************
interfaces
**************************************************  ***********************
auto lo
iface lo inet loopback


**************************************************  ************************
resolv.conf
**************************************************  ************************

**************************************************  ************************
Modules file
**************************************************  ************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

**************************************************  ***********************
Blacklist file
**************************************************  ***********************
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

**************************************************  ************************
Files in folder /etc/modprobe.d/*
**************************************************  ************************
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-watchdog.conf
/etc/modprobe.d/libpisock9.conf

**************************************************  *************************
NetworkManager.state
**************************************************  *************************

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

**************************************************  **************************
nm_applet_file
**************************************************  ***************************
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

Finished  <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<    <<<<<<<<<<<<<<<<<<
```

---

### Post by Hippytaff on 2011-04-16
see if anything here [helps]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/106320")

---

### Post by pawan98 on 2011-04-16
Aaaaaaaaaah I've tried everything - NOTHING HAS WORKED!!!

---

### Post by Hippytaff on 2011-04-16
If you don't have the ability to plug the pc in via ethernet and get the driver that way...you can get it [here]("http://www.filestube.com/r/rtl8191su+linux+driver"). But bear in mind I've never used this site. Download a .deb version to a pendrive and transfer it to your pc with wireless issues. then view the readme file and follow the instructions

---

