---
title: "bc4318 no longer works with 11.10 update"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by RiskyShift on 2011-10-16
I had some trouble getting wireless to work with 11.04 but fwcutter  fixed it. Then I just updated to 11.10 and now the wireless isn't  working again.

I tried blacklisting all kinds of stuff listed in these forums but none helped.

I also uninstalled and reinstalled b43-fwcutter.

Still not working... (BTW during the update process it errored several times about my broadcom card or drivers or something)

Here are some outputs:

```
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````

$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x1068 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*",  ATTR{address}=="00:14:22:c2:d8:ee", ATTR{dev_id}=="0x0",  ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4318 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*",  ATTR{address}=="00:14:a5:3d:86:e2", ATTR{dev_id}=="0x0",  ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```Any ideas?

---

### Post by RiskyShift on 2011-10-16
I just tried the following...

> Hi, let&#347; do this please:
     Code:
     sudo apt-get --purge remove b43-fwcutter firmware-b43-installer 
Then restart your computer and do this.
     Code:
     sudo apt-get update 
     Code:
     sudo apt-get install bcmwl-kernel-source 
Then go to Additional Drivers, the STA driver activate it. 

Then
     Code:
     sudo su echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf exit 
Then restart your computer after you unplug your wired connection.
Thank youI did all of it but I knew it probably wasn't working when Additional Drivers found nothing. After a restart it has now gone from showing I have wireless but firmware missing, to not recognizing I have wireless at all.

Here is some more info:

```
$ lspci -nnk | grep -iA2 net
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
    Kernel modules: ssb
02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 03)
    Subsystem: Dell Device [1028:01a4]
    Kernel driver in use: e100

``````

$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
joydev                 17393  0 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39822  0 
i915                  505108  3 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
yenta_socket           27428  0 
serio_raw              12990  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
binfmt_misc            17292  1 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
e100                   36289  0 

```

---

### Post by wildmanne39 on 2011-10-16
Hi, please run this command then report back here.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

Watch for errors.

Then restart your computer with your wired connection unplugged.

If it does not work post the results of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thank you

---

### Post by PBiz on 2011-10-16
I did the same upgrade and have the same issue however I can get my wireless working if I issue these two commands in a terminal window. 

                                 ~$ sudo modprobe -r b43 ssb ~$ sudo modprobe b43

But I have to do this after every reboot. I sure would like to solve this.

---

### Post by wildmanne39 on 2011-10-16
Hi PBiz, this should work.

Please do:
```
gksudo gedit /etc/rc.local
```
```
rmmod -f b43 ssb
modprobe b43
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thank you

---

### Post by RiskyShift on 2011-10-16
> **wildmanne39 said:**
> Hi, please run this command then report back here.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Watch for errors.

Then restart your computer with your wired connection unplugged.

If it does not work post the results of:
```
cat /etc/modprobe.d/blacklist.conf
```Thank you


It didn't work...

I tried to run "rfkill list" again and it returned nothing so it seems that it doesn't know I have a wireless card anymore.

```
$ cat /etc/modprobe.d/blacklist.conf
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

blacklist bcma
```

---

### Post by RiskyShift on 2011-10-16
I just tried to remove "blacklist bcma" and restart with no result.

---

### Post by wildmanne39 on 2011-10-16
Hi, did you get any errors during the install of the driver and firmware?

Try this please:
```
sudo modprobe b43
```
if that does not work please post the results of the commands:
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
ndiswrapper -l
```
```
lsmod | grep b43
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan0 | tail -n25 
```
Thank you

---

### Post by wildmanne39 on 2011-10-16
Hi, just leave it blacklisted and please do not try things on your own it will make the process much harder.
Thank you

---

### Post by RiskyShift on 2011-10-16
The "sudo modprobe b43" did the job!'

Thank you for the help I will mark this solved.

---

### Post by wildmanne39 on 2011-10-16
Hi, I am glad it worked, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by RiskyShift on 2011-10-17
> **RiskyShift said:**
> The "sudo modprobe b43" did the job!'

Thank you for the help I will mark this solved.


LOL... I just realized I have to do this every time I want to "turn on" my wireless card.

Is there anyway to make it turn on by it's self?

---

### Post by wildmanne39 on 2011-10-17
Hi, this should take care of that issue.
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thank you

---

