---
title: "how to install wireless adapter driver ?"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by abdoudz on 2011-06-16
hi guys  !
can someone explain how to install wireless adapter driver ?
the adapter is : intex IT-ULC21
I use ubuntu 10.04
i have the cd driver but I have no idea how to install it 

 i tried system/admin/hardware drivers and not there. Any help as to which direction I should go ?

---

### Post by DirtyPC on 2011-06-16
ndiswrapper Windows drivers for Linux

from terminal:
sudo apt-get install ndiswrapper-utils-1.9

then once installed you'll need the windows version of the driver (.exe) extract it to desktop then go on system>administration>windows driver and search for an .inf file in the extracted .exe

---

### Post by abdoudz on 2011-06-16
hi thanks for the answer 
system>administration>windows driver ? i can't find WINDOWS DRIVER .. :(

---

### Post by DirtyPC on 2011-06-16
it'll be in preferences or adminsitration, as windows drivers or ndiswrapper or something like that, i dont use it often so i cant remember exactly

---

### Post by abdoudz on 2011-06-16
IS IT hardware drivers ? cuz if it is I can't find anydriver on it :/

---

### Post by DirtyPC on 2011-06-16
i'll install it for you :L

Gimme 2 mins

---

### Post by bkratz on 2011-06-16
> **abdoudz said:**
> IS IT hardware drivers ? cuz if it is I can't find anydriver on it :/

You will only find

system>administration>windows driver 

there if you have installed the gui called ndisgtk through synaptic.

---

### Post by DirtyPC on 2011-06-16
System > Administration menu> Windows Wireless Drivers

you may have to scroll down

---

### Post by DirtyPC on 2011-06-16
> **bkratz said:**
> You will only find

system>administration>windows driver 

there if you have installed the gui called ndisgtk through synaptic.
oops got there before me :)

---

### Post by walt.smith1960 on 2011-06-16
The brand name of an adapter isn't as useful as the output of one of these commands.  If your device is built in, try this command:  "lspci".  You're looking for a line that often starts with 'network controller'.  If your wireless adapter is a USB dongle, use the command "lsusb".  My RealTek USB WiFi adapter looks like this:
```
[/Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
```No retailer makes their own chips.  They're from RealTek or Ralink or Broadcom or somebody like that. The manufacturer releases the drivers, not the retailer.  If you can post the output of lspci or lsusb, you'll probably have get the help you need.  I think most regard NDISwrapper as a last resort if a suitable native Linux driver does not exist.

---

### Post by abdoudz on 2011-06-16
is there any software that allow to extract .exe ? cuz i couldn't with ARCHIVE MANAGER ..
THANK YOU VERY VERY MUCH [harrylucas1]("http://ubuntuforums.org/member.php?u=1174686")
THANK YOU VERY VERY MUCH [bkratz]("http://ubuntuforums.org/member.php?u=821493")

---

### Post by bkratz on 2011-06-16
You might want to post the output walt.smith1960 asked for. I have to use ndiswrapper but wouldn't if I did not have too!

---

### Post by abdoudz on 2011-06-16
@[walt.smith1960]("http://ubuntuforums.org/member.php?u=866064")

THANK YOU .. THAT'S WHAT I GOT
> abdou@abdou-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
abdou@abdou-desktop:~$ 





---

### Post by bkratz on 2011-06-16
It doesn't show in lspci, you might try the lsusb command.

---

### Post by walt.smith1960 on 2011-06-16
Thanks abdoudz.  It looks like we need lsusb.  I found your adapter and it's a USB device.  Your wired ethernet adapter is listed:

"02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)"
 
but not your wireless adapter.  Your adapter's web page  says it has Linux support but I didn't see a driver listed in the support section.  Getting wireless to work in Linux can be the most challenging part of installing but this forum is seldom stymied for long.

---

### Post by abdoudz on 2011-06-16
isusb
> abdou@abdou-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
abdou@abdou-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
abdou@abdou-desktop:~$ 


---

### Post by walt.smith1960 on 2011-06-16
There is what you need:
```
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. 
```I'm not well versed in Ralink devices.  I hope someone who has had experience with them will be along.

Edit:  here is something easy to try.  [http://forums.opensuse.org/english/get-technical-help-here/wireless/454756-tp-link-tl-wn321g-2.html](http://forums.opensuse.org/english/get-technical-help-here/wireless/454756-tp-link-tl-wn321g-2.html) post #13.  I know there can be conflicting drivers or incorrect drivers loaded.  While you're waiting you could try this: "lsmod" and see which modules are being loaded.  I've seen many posts regarding Ralink drivers where rt 2870sta and rt2x00 and rt2800 were fighting one another.  Blacklisting one or the more of the modules was the solution but again, I have no experience with Ralink.

---

### Post by abdoudz on 2011-06-16
> I'm not well versed in Ralink devices.  I hope someone who has had experience with them will be along.
thankyou very Much sir ,

---

### Post by abdoudz on 2011-06-16
can anyone help me ?

---

### Post by bkratz on 2011-06-16
> **abdoudz said:**
> can anyone help me ?



In this thread, especially late, they seem to have what you need.

[http://ubuntuforums.org/showthread.php?t=1718254&page=3](http://ubuntuforums.org/showthread.php?t=1718254&page=3)

It looks like just blacklisting one file will take care of it.

---

### Post by abdoudz on 2011-06-16
> 

In this thread, especially late, they seem to have what you need.

[http://ubuntuforums.org/showthread.php?t=1718254&page=3](http://ubuntuforums.org/showthread.php?t=1718254&page=3)

It looks like just blacklisting one file will take care of it.
thanks but it seems like it's not the same model , didn't work for  me

---

### Post by bkratz on 2011-06-16
> **abdoudz said:**
> thanks but it seems like it's not the same model , didn't work for  me



Your device uses the same chipset that is what is important.  Try googlubuntu.com and type in 

148f:2070

for a lot of others. You seem to be the only one using that particular named device!

---

### Post by abdoudz on 2011-06-16
> 
for a lot of others. You seem to be the only one using that particular named device!
:d
what's the best wireless adapter for ubuntu (works without driver ?

---

### Post by bkratz on 2011-06-16
First let's see what modules are trying to be used (bad English!)

sudo lshw -C network

and also post the output of 

lsmod

---

### Post by abdoudz on 2011-06-16
********

---

### Post by abdoudz on 2011-06-16
> abdou@abdou-desktop:~$ sudo lshw -C network
[sudo] password for abdou: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4c:36:09:68
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.10.10.100 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:febe0000-febfffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 78:44:76:82:df:eb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
abdou@abdou-desktop:~$ 

-------
lsmod : 
> abdou@abdou-desktop:~$ lsmod
Module                  Size  Used by
rt2870sta             461811  0 
nls_utf8                1069  0 
isofs                  29250  0 
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_intel8x0           25652  3 
snd_ac97_codec        100646  1 snd_intel8x0
arc4                    1153  2 
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  2 rt2x00usb,rt2x00lib
i915                  287458  3 
ppdev                   5259  0 
drm_kms_helper         29329  1 i915
cfg80211              126528  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
parport_pc             25962  1 
drm                   162409  4 i915,drm_kms_helper
snd                    54180  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
lp                      7028  0 
soundcore               6620  1 snd
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24375  2 i915
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
parport                32635  3 ppdev,parport_pc,lp
agpgart                31724  2 drm,intel_agp
r8169                  34108  0 
mii                     4381  1 r8169
abdou@abdou-desktop:~$ 


---

### Post by bkratz on 2011-06-16
Several drivers probably colliding. This will not be permanent, just an experiment


sudo rmmod rt2800usb
sudo modprobe rt2870sta


Try wireless then if it works we can make it permanent.

---

### Post by abdoudz on 2011-06-16
> several drivers probably colliding. This will not be permanent, just an experiment


sudo rmmod rt2800usb
sudo modprobe rt2870sta


try wireless then if it works we can make it permanent.
it's working ! :) yeaaaaaaah ! Thakyou thakyou ... Now what should i do ?

---

### Post by abdoudz on 2011-06-16
> Try wireless then if it works we can make it permanent.
how to make it permanent sir ?

---

### Post by bkratz on 2011-06-16
> **abdoudz said:**
> it's working ! :) yeaaaaaaah ! Thakyou thakyou ... Now what should i do ?

Congratulations!  I think all you will have to do is blacklist the one driver, the other should load at boot time--if not we will fix that later. Anyway,

```


echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf


```

Try a reboot and make sure it works next.  If it does go to the thread tools above and mark as solved to help someone else.

---

### Post by abdoudz on 2011-06-17
> Congratulations!  I think all you will have to do is blacklist the one  driver, the other should load at boot time--if not we will fix that  later. Anyway,

 	Code:
 	echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf 
Try a reboot and make sure it works next.  If it does go to the thread tools above and mark as solved to help someone else.
hi ! sorry for being late ..
aactually after rebooting ; the adapter didn't work ;

---

### Post by abdoudz on 2011-06-17
up........

---

### Post by chili555 on 2011-06-17
Let's see:```
cat /etc/modprobe.d/blacklist.conf
lsmod | grep rt2
```We'll get this tweaked in a few steps.

---

### Post by abdoudz on 2011-06-17
thank you that's what i got : 
> abdou@abdou-desktop:~$ cat /etc/modprobe.d/blacklist.conf
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
blacklist rt3070sta
blacklist rt2800usb
blacklist rt2800usb
blacklist rt2800usb
blacklist rt2070usb
blacklist rt2070usb
blacklist rt2800usb
blacklist rt3070sta
blacklist rt2800usb
blacklist rt2800usb
blacklist rt2800usb

blacklist rt2800usb
abdou@abdou-desktop:~$ lsmod | grep rt2
rt2870sta             461811  1 
abdou@abdou-desktop:~$ 


---

### Post by abdoudz on 2011-06-17
up ...........

---

### Post by bkratz on 2011-06-17
> **abdoudz said:**
> hi ! sorry for being late ..
aactually after rebooting ; the adapter didn't work ;



Sorry, actually had to work, but you are in the most qualified hands there is--Dr. Chili so I think I will fix dinner!

---

### Post by abdoudz on 2011-06-17
> Sorry, actually had to work, but you are in the most qualified hands there is--Dr. Chili so I think I will fix dinner!
thank you so much sir ! :)

---

### Post by chili555 on 2011-06-17
After rebooting and it isn't working, is the rt2870sta module loaded?```
lsmod | grep rt2
```Is the ethernet cable detached so that Network Manager takes control of your wireless? Is the wireless switch set to 'On?'```
rfkill list all
```We can tweak some files if needed.

---

### Post by abdoudz on 2011-06-17
> abdou@abdou-desktop:~$ lsmod | grep rt2
rt2870sta             461811  1 
abdou@abdou-desktop:~$ 




+-------------

> Is the wireless switch set to 'On?'
no
-----------
> abdou@abdou-desktop:~$ lsmod | grep rt2
rt2870sta             461811  1 
abdou@abdou-desktop:~$ rfkill list all
abdou@abdou-desktop:~$ rfkill list all
abdou@abdou-desktop:~$ 




---

### Post by chili555 on 2011-06-17
> Quote:
Is the wireless switch set to 'On?'
noPlease explain. How is the wireless going to work if the switch is off? Does it not function in Ubuntu? If not, please post:```
lsmod
```

---

### Post by abdoudz on 2011-06-18
when i reboot ; the wireless adapter doesn't work ; every time i swich on the pc i have to write  in terminal to make it works :
> 
sudo rmmod rt2800usb
sudo modprobe rt2870sta

--------------------------------------------------------------------------
lsmod

> abdou@abdou-desktop:~$ lsmod
Module                  Size  Used by
rt2870sta             461811  1 
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
fbcon                  35102  72 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  287810  3 
drm_kms_helper         29329  1 i915
snd_intel8x0           25652  3 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
psmouse                63245  0 
intel_agp              24375  2 i915
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
ppdev                   5259  0 
video                  17375  1 i915
serio_raw               3978  0 
snd_pcm                70694  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
parport_pc             25962  1 
output                  1871  1 video
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
parport                32635  3 lp,ppdev,parport_pc
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
r8169                  34140  0 
mii                     4381  1 r8169
abdou@abdou-desktop:~$ 


---

### Post by abdoudz on 2011-06-18
when i reboot ; the wireless adapter doesn't work ; every time i swich on the pc i have to write  in terminal to make it works :
> 
sudo rmmod rt2800usb
sudo modprobe rt2870sta

--------------------------------------------------------------------------
lsmod

> abdou@abdou-desktop:~$ lsmod
Module                  Size  Used by
rt2870sta             461811  1 
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
fbcon                  35102  72 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  287810  3 
drm_kms_helper         29329  1 i915
snd_intel8x0           25652  3 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
psmouse                63245  0 
intel_agp              24375  2 i915
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
ppdev                   5259  0 
video                  17375  1 i915
serio_raw               3978  0 
snd_pcm                70694  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
parport_pc             25962  1 
output                  1871  1 video
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
parport                32635  3 lp,ppdev,parport_pc
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
r8169                  34140  0 
mii                     4381  1 r8169
abdou@abdou-desktop:~$ 


---

### Post by chili555 on 2011-06-18
> when i reboot ; the wireless adapter doesn't work ; every time i swich on the pc i have to write in terminal to make it works :
```
sudo rmmod rt2800usb
sudo modprobe rt2870sta
``` You have rt2800usb blacklisted; several times in fact. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change these lines:> # really needed.
blacklist amd76x_edac
blacklist rt3070sta
blacklist rt2800usb
blacklist rt2800usb
blacklist rt2800usb
blacklist rt2070usb
blacklist rt2070usb
blacklist rt2800usb
blacklist rt3070sta
blacklist rt2800usb
blacklist rt2800usb
blacklist rt2800usb

blacklist rt2800usbTo this:```
# really needed.
blacklist amd76x_edac

blacklist rt2800usb
```Proofread, save and close gedit. Now reboot. Before you do your terminal commands, see if rt2800usb is actually loaded:```
lsmod | grep rt2
```If it's not loaded, there is no need to rmmod it. 

Do you now need to modprobe rt2870sta to get your wireless working? If so, we can tweak a bit more.

---

### Post by abdoudz on 2011-06-18
> If it's not loaded, there is no need to rmmod it. 

Do you now need to modprobe rt2870sta to get your wireless working? If so, we can tweak a bit more.
thank you
ok .. now i don't need to rmmod
but i still need to modprobe rt287sta

---

### Post by chili555 on 2011-06-18
Let's see if we can fix that. Please do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Now does it work as expected?

---

### Post by abdoudz on 2011-06-18
still need to :
sudo modprobe rt2870sta

---

### Post by chili555 on 2011-06-18
Something is very wrong. Please reboot and before you modprobe rt2870sta, run:```
dmesg > abdoudz.txt
lsmod >> abdoudz.txt
sudo modprobe rt2870sta
dmesg >> abdoudz.txt
zip abdoudz.zip abdoudz.txt
```You will find a file abdoudz.zip in your user directory. Please attach it to your reply using the paperclip at the top of the reply box.

---

### Post by abdoudz on 2011-06-18
i got qn .txt file not zip :(  :

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-32-generic (buildd@roseapple) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 (Ubuntu 2.6.32-32.62-generic 2.6.32.38+drm33.16)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f6d0000 - 000000003f6de000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6de000 - 000000003f6f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6f0000 - 000000003f6fe000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3f6d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 03F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f6d0000 (usable)
[    0.000000]  modified: 000000003f6d0000 - 000000003f6de000 (ACPI data)
[    0.000000]  modified: 000000003f6de000 - 000000003f6f0000 (ACPI NVS)
[    0.000000]  modified: 000000003f6f0000 - 000000003f6fe000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 2f1c4000 - 2f95b71d
[    0.000000] ACPI: RSDP 000f9b00 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3f6d0000 00038 (v01 121609 RSDT1847 20091216 MSFT 00000097)
[    0.000000] ACPI: FACP 3f6d0200 00084 (v01 121609 FACP1847 20091216 MSFT 00000097)
[    0.000000] ACPI: DSDT 3f6d0440 05546 (v01  Z31BI Z31BI205 00000205 INTL 20051117)
[    0.000000] ACPI: FACS 3f6de000 00040
[    0.000000] ACPI: APIC 3f6d0390 0006C (v01 121609 APIC1847 20091216 MSFT 00000097)
[    0.000000] ACPI: MCFG 3f6d0400 0003C (v01 121609 OEMMCFG  20091216 MSFT 00000097)
[    0.000000] ACPI: OEMB 3f6de040 00071 (v01 121609 OEMB1847 20091216 MSFT 00000097)
[    0.000000] ACPI: GSCI 3f6de0c0 02024 (v01 121609 GMCHSCI  20091216 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008deef8]    TEXT DATA BSS ==> [0000100000 - 00008deef8]
[    0.000000]   #4 [002f1c4000 - 002f95b71d]          RAMDISK ==> [002f1c4000 - 002f95b71d]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008df000 - 00008e2193]              BRK ==> [00008df000 - 00008e2193]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f6d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f6d0
[    0.000000] On node 0 totalpages: 259679
[    0.000000] free_area_init_node: node 0, pgdat c07987c0, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32212 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f6fe000 (gap: 3f6fe000:bf702000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36312 r0 d21032 u1048576
[    0.000000] pcpu-alloc: s36312 r0 d21032 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257649
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-32-generic root=UUID=7bbfaa49-f921-4de3-914f-b7a08dafe712 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 5195520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f6d0)
[    0.000000] Memory: 1007960k/1039168k available (4674k kernel code, 30120k reserved, 2120k data, 668k init, 129864k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc084a000   ( 668 kB)
[    0.000000]       .data : 0xc0590ad7 - 0xc07a2d88   (2120 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590ad7   (4674 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2593.401 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5186.80 BogoMIPS (lpj=10373604)
[    0.004015] Security Framework initialized
[    0.004030] AppArmor: AppArmor initialized
[    0.004035] Mount-cache hash table entries: 512
[    0.004128] Initializing cgroup subsys ns
[    0.004131] Initializing cgroup subsys cpuacct
[    0.004134] Initializing cgroup subsys memory
[    0.004139] Initializing cgroup subsys devices
[    0.004141] Initializing cgroup subsys freezer
[    0.004142] Initializing cgroup subsys net_cls
[    0.004159] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004161] CPU: L2 cache: 2048K
[    0.004164] CPU: Physical Processor ID: 0
[    0.004165] CPU: Processor Core ID: 0
[    0.004168] mce: CPU supports 6 MCE banks
[    0.004174] CPU0: Thermal monitoring enabled (TM2)
[    0.004178] using mwait in idle threads.
[    0.004181] Performance Events: Core2 events, Intel PMU driver.
[    0.004187] ... version:                2
[    0.004188] ... bit width:              40
[    0.004190] ... generic registers:      2
[    0.004191] ... value mask:             000000ffffffffff
[    0.004192] ... max period:             000000007fffffff
[    0.004194] ... fixed-purpose events:   3
[    0.004195] ... event mask:             0000000700000003
[    0.004200] Checking 'hlt' instruction... OK.
[    0.022356] ACPI: Core revision 20090903
[    0.032007] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032012] ftrace: allocating 21723 entries in 43 pages
[    0.036052] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036357] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076786] CPU0: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
[    0.080001] APIC calibration not consistent with PM-Timer: 140ms instead of 100ms
[    0.080001] APIC delta adjusted to PM-Timer: 1246872 (1745721)
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 2048K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.164067] CPU1: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
[    0.164074] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168017] Brought up 2 CPUs
[    0.168019] Total of 2 processors activated (10373.74 BogoMIPS).
[    0.168894] CPU0 attaching sched-domain:
[    0.168898]  domain 0: span 0-1 level MC
[    0.168899]   groups: 0 1
[    0.168904] CPU1 attaching sched-domain:
[    0.168906]  domain 0: span 0-1 level MC
[    0.168907]   groups: 1 0
[    0.168963] devtmpfs: initialized
[    0.168963] regulator: core version 0.5
[    0.168963] Time:  1:51:05  Date: 06/19/11
[    0.168963] NET: Registered protocol family 16
[    0.168963] Trying to unpack rootfs image as initramfs...
[    0.168963] EISA bus registered
[    0.168963] ACPI: bus type pci registered
[    0.168963] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.168963] PCI: Not using MMCONFIG.
[    0.168963] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.168963] PCI: Using configuration type 1 for base access
[    0.172080] bio: create slab <bio-0> at 0
[    0.172722] ACPI: EC: Look up EC in DSDT
[    0.174964] ACPI: Executed 1 blocks of module-level executable AML code
[    0.178460] ACPI: Interpreter enabled
[    0.178465] ACPI: (supports S0 S1 S4 S5)
[    0.178483] ACPI: Using IOAPIC for interrupt routing
[    0.178526] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.181108] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.181110] PCI: Using MMCONFIG for extended config space
[    0.186865] ACPI Warning: Incorrect checksum in table [OEMB] - 94, should be 8F (20090903/tbutils-314)
[    0.187668] ACPI: No dock devices found.
[    0.187920] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.188009] pci 0000:00:02.0: reg 10 32bit mmio: [0xfea80000-0xfeafffff]
[    0.188014] pci 0000:00:02.0: reg 14 io port: [0xdc00-0xdc07]
[    0.188018] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.188022] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.188115] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.188118] pci 0000:00:1c.0: PME# disabled
[    0.188177] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.188180] pci 0000:00:1c.1: PME# disabled
[    0.188224] pci 0000:00:1d.0: reg 20 io port: [0xd880-0xd89f]
[    0.188268] pci 0000:00:1d.1: reg 20 io port: [0xd800-0xd81f]
[    0.188313] pci 0000:00:1d.2: reg 20 io port: [0xd480-0xd49f]
[    0.188357] pci 0000:00:1d.3: reg 20 io port: [0xd400-0xd41f]
[    0.188405] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfea7bc00-0xfea7bfff]
[    0.188452] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.188456] pci 0000:00:1d.7: PME# disabled
[    0.188525] pci 0000:00:1e.2: reg 10 io port: [0xd000-0xd0ff]
[    0.188531] pci 0000:00:1e.2: reg 14 io port: [0xcc00-0xcc3f]
[    0.188536] pci 0000:00:1e.2: reg 18 32bit mmio: [0xfea7b800-0xfea7b9ff]
[    0.188541] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xfea7b400-0xfea7b4ff]
[    0.188566] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.188570] pci 0000:00:1e.2: PME# disabled
[    0.188647] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.188656] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.188695] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.188701] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.188707] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.188712] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.188718] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.188756] pci 0000:00:1f.2: reg 10 io port: [0xc880-0xc887]
[    0.188761] pci 0000:00:1f.2: reg 14 io port: [0xc800-0xc803]
[    0.188766] pci 0000:00:1f.2: reg 18 io port: [0xc480-0xc487]
[    0.188772] pci 0000:00:1f.2: reg 1c io port: [0xc400-0xc403]
[    0.188777] pci 0000:00:1f.2: reg 20 io port: [0xc080-0xc08f]
[    0.188799] pci 0000:00:1f.2: PME# supported from D3hot
[    0.188802] pci 0000:00:1f.2: PME# disabled
[    0.188845] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.188949] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.188968] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xfdfff000-0xfdffffff]
[    0.188981] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfdfe0000-0xfdfeffff]
[    0.188989] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfebe0000-0xfebfffff]
[    0.189026] pci 0000:02:00.0: supports D1 D2
[    0.189028] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.189032] pci 0000:02:00.0: PME# disabled
[    0.189085] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
[    0.189089] pci 0000:00:1c.1: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.189094] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.189141] pci 0000:00:1e.0: transparent bridge
[    0.189161] pci_bus 0000:00: on NUMA node 0
[    0.189165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.189276] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.189394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.189441] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.196335] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.196425] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.196512] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.196602] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.196688] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.196774] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.196862] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.196948] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.197037] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.197046] vgaarb: loaded
[    0.197153] SCSI subsystem initialized
[    0.197233] libata version 3.00 loaded.
[    0.197296] usbcore: registered new interface driver usbfs
[    0.197305] usbcore: registered new interface driver hub
[    0.197325] usbcore: registered new device driver usb
[    0.197431] ACPI: WMI: Mapper loaded
[    0.197433] PCI: Using ACPI for IRQ routing
[    0.197557] NetLabel: Initializing
[    0.197558] NetLabel:  domain hash size = 128
[    0.197559] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.197570] NetLabel:  unlabeled traffic allowed by default
[    0.197683] hpet clockevent registered
[    0.197686] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.197691] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.197695] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.200107] Switching to clocksource tsc
[    0.201730] AppArmor: AppArmor Filesystem Enabled
[    0.201744] pnp: PnP ACPI init
[    0.201759] ACPI: bus type pnp registered
[    0.204803] pnp: PnP ACPI: found 17 devices
[    0.204805] ACPI: ACPI bus type pnp unregistered
[    0.204809] PnPBIOS: Disabled by ACPI PNP
[    0.204819] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.204826] system 00:0a: ioport range 0xa00-0xa0f has been reserved
[    0.204829] system 00:0a: ioport range 0xa10-0xa1f has been reserved
[    0.204833] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.204835] system 00:0b: ioport range 0x800-0x87f has been reserved
[    0.204837] system 00:0b: ioport range 0x480-0x4bf has been reserved
[    0.204840] system 00:0b: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.204842] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.204847] system 00:0d: iomem range 0xffc00000-0xfff7ffff has been reserved
[    0.204851] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.204853] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.204857] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.204862] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.204864] system 00:10: iomem range 0xc0000-0xcffff could not be reserved
[    0.204867] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.204869] system 00:10: iomem range 0x100000-0x3f6fffff could not be reserved
[    0.239569] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.239573] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.239577] pci 0000:00:1c.0:   MEM window: 0x40000000-0x401fffff
[    0.239581] pci 0000:00:1c.0:   PREFETCH window: 0x00000040200000-0x000000403fffff
[    0.239587] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.239590] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
[    0.239594] pci 0000:00:1c.1:   MEM window: 0xfeb00000-0xfebfffff
[    0.239598] pci 0000:00:1c.1:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.239603] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.239605] pci 0000:00:1e.0:   IO window: disabled
[    0.239609] pci 0000:00:1e.0:   MEM window: disabled
[    0.239612] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.239625] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.239632]   alloc irq_desc for 16 on node -1
[    0.239634]   alloc kstat_irqs on node -1
[    0.239642] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.239646] pci 0000:00:1c.0: setting latency timer to 64
[    0.239654]   alloc irq_desc for 17 on node -1
[    0.239655]   alloc kstat_irqs on node -1
[    0.239658] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.239661] pci 0000:00:1c.1: setting latency timer to 64
[    0.239667] pci 0000:00:1e.0: setting latency timer to 64
[    0.239671] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.239672] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.239675] pci_bus 0000:01: resource 0 io:  [0x1000-0x1fff]
[    0.239676] pci_bus 0000:01: resource 1 mem: [0x40000000-0x401fffff]
[    0.239678] pci_bus 0000:01: resource 2 pref mem [0x40200000-0x403fffff]
[    0.239681] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.239683] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.239685] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.239687] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.239689] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.239723] NET: Registered protocol family 2
[    0.239810] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.240088] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.240603] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.240850] TCP: Hash tables configured (established 131072 bind 65536)
[    0.240852] TCP reno registered
[    0.240929] NET: Registered protocol family 1
[    0.240949] pci 0000:00:02.0: Boot video device
[    0.241197] cpufreq-nforce2: No nForce2 chipset.
[    0.241219] Scanning for low memory corruption every 60 seconds
[    0.241313] audit: initializing netlink socket (disabled)
[    0.241323] type=2000 audit(1308448265.239:1): initialized
[    0.249109] highmem bounce pool size: 64 pages
[    0.249113] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.250324] VFS: Disk quotas dquot_6.5.2
[    0.250372] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.250844] fuse init (API version 7.13)
[    0.250910] msgmni has been set to 1716
[    0.251083] alg: No test for stdrng (krng)
[    0.251128] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.251131] io scheduler noop registered
[    0.251132] io scheduler anticipatory registered
[    0.251134] io scheduler deadline registered
[    0.251163] io scheduler cfq registered (default)
[    0.251272]   alloc irq_desc for 24 on node -1
[    0.251274]   alloc kstat_irqs on node -1
[    0.251283] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.251290] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.251394]   alloc irq_desc for 25 on node -1
[    0.251395]   alloc kstat_irqs on node -1
[    0.251401] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.251407] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.251477] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.251492] Firmware did not grant requested _OSC control
[    0.251506] Firmware did not grant requested _OSC control
[    0.251527] Firmware did not grant requested _OSC control
[    0.251536] Firmware did not grant requested _OSC control
[    0.251563] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.251646] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.251649] ACPI: Power Button [PWRB]
[    0.251687] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.251689] ACPI: Power Button [PWRF]
[    0.251914] processor LNXCPU:00: registered as cooling_device0
[    0.251941] processor LNXCPU:01: registered as cooling_device1
[    0.254932] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.255022] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.255308] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.256261] brd: module loaded
[    0.256632] loop: module loaded
[    0.256698] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.256775] ata_piix 0000:00:1f.1: version 2.13
[    0.256787]   alloc irq_desc for 18 on node -1
[    0.256789]   alloc kstat_irqs on node -1
[    0.256794] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.256830] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.256912] scsi0 : ata_piix
[    0.256971] scsi1 : ata_piix
[    0.257918] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.257920] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.257938]   alloc irq_desc for 19 on node -1
[    0.257939]   alloc kstat_irqs on node -1
[    0.257943] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.257946] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.257975] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.258017] scsi2 : ata_piix
[    0.258057] scsi3 : ata_piix
[    0.258122] isapnp: Scanning for PnP cards...
[    0.259126] ata3: SATA max UDMA/133 cmd 0xc880 ctl 0xc800 bmdma 0xc080 irq 19
[    0.259128] ata4: SATA max UDMA/133 cmd 0xc480 ctl 0xc400 bmdma 0xc088 irq 19
[    0.259386] Fixed MDIO Bus: probed
[    0.259413] PPP generic driver version 2.4.2
[    0.259444] tun: Universal TUN/TAP device driver, 1.6
[    0.259446] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.259510] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.259524]   alloc irq_desc for 23 on node -1
[    0.259525]   alloc kstat_irqs on node -1
[    0.259529] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.259561] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.259564] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.259588] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.259607] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.259616] ehci_hcd 0000:00:1d.7: debug port 1
[    0.263484] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.263496] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfea7bc00
[    0.275816] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.275910] usb usb1: configuration #1 chosen from 1 choice
[    0.275932] hub 1-0:1.0: USB hub found
[    0.275939] hub 1-0:1.0: 8 ports detected
[    0.275997] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.276010] uhci_hcd: USB Universal Host Controller Interface driver
[    0.276046] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.276052] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.276055] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.276081] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.276103] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    0.276171] usb usb2: configuration #1 chosen from 1 choice
[    0.276190] hub 2-0:1.0: USB hub found
[    0.276195] hub 2-0:1.0: 2 ports detected
[    0.276230] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.276235] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.276237] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.276260] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.276280] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    0.276350] usb usb3: configuration #1 chosen from 1 choice
[    0.276371] hub 3-0:1.0: USB hub found
[    0.276376] hub 3-0:1.0: 2 ports detected
[    0.276408] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.276412] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.276415] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.276439] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.276465] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    0.276533] usb usb4: configuration #1 chosen from 1 choice
[    0.276554] hub 4-0:1.0: USB hub found
[    0.276559] hub 4-0:1.0: 2 ports detected
[    0.276592] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.276596] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.276599] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.276625] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.276650] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d400
[    0.276715] usb usb5: configuration #1 chosen from 1 choice
[    0.276733] hub 5-0:1.0: USB hub found
[    0.276738] hub 5-0:1.0: 2 ports detected
[    0.276816] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.279077] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.279082] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.279183] mice: PS/2 mouse device common for all mice
[    0.279278] rtc_cmos 00:03: RTC can wake from S4
[    0.279311] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.279332] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.279410] device-mapper: uevent: version 1.0.3
[    0.294634] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.311202] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.337229] Freeing initrd memory: 7773k freed
[    0.340930] device-mapper: multipath: version 1.1.0 loaded
[    0.340934] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.341099] EISA: Probing bus 0 at eisa.0
[    0.341105] Cannot allocate resource for EISA slot 1
[    0.341123] EISA: Detected 0 cards.
[    0.341185] cpuidle: using governor ladder
[    0.341187] cpuidle: using governor menu
[    0.341527] TCP cubic registered
[    0.341650] NET: Registered protocol family 10
[    0.342047] lo: Disabled Privacy Extensions
[    0.342308] NET: Registered protocol family 17
[    0.342360] Using IPI No-Shortcut mode
[    0.342447] PM: Resume from disk failed.
[    0.342458] registered taskstats version 1
[    0.342687]   Magic number: 15:867:862
[    0.342765] rtc_cmos 00:03: setting system clock to 2011-06-19 01:51:05 UTC (1308448265)
[    0.342768] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.342769] EDD information not available.
[    0.451895] ata3.00: ATA-8: Hitachi HDP725025GLA380, GM2OA5CA, max UDMA/133
[    0.451897] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.451925] ata3.01: ATAPI: ATAPI   iHDS118   4, FL05, max UDMA/100
[    0.467907] ata3.00: configured for UDMA/133
[    0.483746] ata3.01: configured for UDMA/100
[    0.599565] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.615048] isapnp: No Plug & Play device found
[    0.615178] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDP72502 GM2O PQ: 0 ANSI: 5
[    0.615272] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.615283] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    0.615310] sd 2:0:0:0: [sda] Write Protect is off
[    0.615312] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.615390] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.616753] scsi 2:0:1:0: CD-ROM            ATAPI    iHDS118   4      FL05 PQ: 0 ANSI: 5
[    0.616775]  sda: sda1 sda2 < sda5 >
[    0.677325] sr0: scsi3-mmc drive: 48x/16x cd/rw xa/form2 cdda tray
[    0.677328] Uniform CD-ROM driver Revision: 3.20
[    0.677384] sr 2:0:1:0: Attached scsi CD-ROM sr0
[    0.677416] sr 2:0:1:0: Attached scsi generic sg1 type 5
[    0.677494] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.677507] Freeing unused kernel memory: 668k freed
[    0.677838] Write protecting the kernel text: 4676k
[    0.677869] Write protecting the kernel read-only data: 1844k
[    0.690057] udev: starting version 151
[    0.729666] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.729685] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.729718] r8169 0000:02:00.0: setting latency timer to 64
[    0.729759]   alloc irq_desc for 26 on node -1
[    0.729761]   alloc kstat_irqs on node -1
[    0.729774] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    0.730292] eth0: RTL8102e at 0xf805c000, 00:e0:4c:36:09:68, XID 14c00000 IRQ 26
[    0.750168] usb 1-1: configuration #1 chosen from 1 choice
[    1.067138] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.067142] EXT4-fs (sda1): write access will be enabled during recovery
[    1.147577] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    1.279657] usb 4-1: configuration #1 chosen from 1 choice
[    1.616436] EXT4-fs (sda1): orphan cleanup on readonly fs
[    1.616443] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 10749240
[    1.616517] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 10748812
[    1.616530] EXT4-fs (sda1): 2 orphan inodes deleted
[    1.616532] EXT4-fs (sda1): recovery complete
[    1.730085] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   10.594355] udev: starting version 151
[   10.715652] Linux agpgart interface v0.103
[   10.720085] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[   10.720606] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[   10.745932] lp: driver loaded but no devices found
[   10.761649] Adding 2978808k swap on /dev/sda5.  Priority:-1 extents:1 across:2978808k 
[   10.781571] intel_rng: FWH not detected
[   10.793979] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   10.796595] [drm] Initialized drm 1.1.0 20060810
[   10.801413] parport_pc 00:07: reported by Plug and Play ACPI
[   10.801456] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   10.839491] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.839496] i915 0000:00:02.0: setting latency timer to 64
[   10.843978]   alloc irq_desc for 27 on node -1
[   10.843981]   alloc kstat_irqs on node -1
[   10.843989] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[   10.844025] [drm] set up 7M of stolen space
[   10.844532] [drm] initialized overlay support
[   10.847759] ppdev: user-space parallel port driver
[   10.886425] type=1505 audit(1308448276.041:2):  operation="profile_load" pid=655 name="/sbin/dhclient3"
[   10.886976] type=1505 audit(1308448276.041:3):  operation="profile_load" pid=655 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.887280] type=1505 audit(1308448276.041:4):  operation="profile_load" pid=655 name="/usr/lib/connman/scripts/dhclient-script"
[   10.888421] type=1505 audit(1308448276.041:5):  operation="profile_replace" pid=663 name="/sbin/dhclient3"
[   10.888977] type=1505 audit(1308448276.045:6):  operation="profile_replace" pid=663 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.889283] type=1505 audit(1308448276.045:7):  operation="profile_replace" pid=663 name="/usr/lib/connman/scripts/dhclient-script"
[   10.889988] lp0: using parport0 (interrupt-driven).
[   10.960299] psmouse serio1: ID: 10 00 64
[   11.009606] fb0: inteldrmfb frame buffer device
[   11.009609] registered panic notifier
[   11.009688] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.009723] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.009741] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   11.011594] vga16fb: initializing
[   11.011598] vga16fb: mapped to 0xc00a0000
[   11.011600] vga16fb: not registering due to another framebuffer present
[   11.068270] Console: switching to colour frame buffer device 170x48
[   11.336517] intel8x0_measure_ac97_clock: measured 54400 usecs (2621 samples)
[   11.336520] intel8x0: clocking to 48000
[   11.445998] r8169: eth0: link down
[   11.446109] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.471554] type=1505 audit(1308448276.625:8):  operation="profile_replace" pid=919 name="/sbin/dhclient3"
[   11.472116] type=1505 audit(1308448276.629:9):  operation="profile_replace" pid=919 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.473944] type=1505 audit(1308448276.629:10):  operation="profile_load" pid=918 name="/usr/share/gdm/guest-session/Xsession"
[   11.474713] type=1505 audit(1308448276.629:11):  operation="profile_replace" pid=919 name="/usr/lib/connman/scripts/dhclient-script"
[   11.507296] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   12.045591] CPU0 attaching NULL sched-domain.
[   12.045596] CPU1 attaching NULL sched-domain.
[   12.064558] CPU0 attaching sched-domain:
[   12.064561]  domain 0: span 0-1 level MC
[   12.064563]   groups: 0 1
[   12.064568] CPU1 attaching sched-domain:
[   12.064569]  domain 0: span 0-1 level MC
[   12.064571]   groups: 1 0
[   13.933273] CPU0 attaching NULL sched-domain.
[   13.933278] CPU1 attaching NULL sched-domain.
[   13.956571] CPU0 attaching sched-domain:
[   13.956574]  domain 0: span 0-1 level MC
[   13.956577]   groups: 0 1
[   13.956581] CPU1 attaching sched-domain:
[   13.956583]  domain 0: span 0-1 level MC
[   13.956585]   groups: 1 0
Module                  Size  Used by
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
i915                  287810  3 
drm_kms_helper         29329  1 i915
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             25962  1 
psmouse                63245  0 
serio_raw               3978  0 
drm                   162377  4 i915,drm_kms_helper
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
lp                      7028  0 
output                  1871  1 video
parport                32635  3 ppdev,parport_pc,lp
r8169                  34140  0 
mii                     4381  1 r8169
```

---

### Post by chili555 on 2011-06-19
May I please see:```
cat /etc/modules
```Thanks.

---

