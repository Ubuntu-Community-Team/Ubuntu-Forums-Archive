---
title: "WiFi and Wired Connections lost"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by DaveG_123 on 2011-08-29
Hi,

I've been using Ubuntu on my Compaq Mini laptop/netbook successfully for about six months.

I mainly use it to surf the internet and to send and receive emails via a WiFi connection to my BT Home Hub. This has been working fine until the other day when it just stopped as I opened a new tab in the Cromium browser. I've tried several shut downs and restarts but with no success.

The small WiFi icon in the menu bar has an exlamation mark next to it and if I left click on it it says "No network devices are available". I used to see this icon pulsing when first trying to connect but it doesn't even do that anymore as if the WiFi is turned off somewhere but I can't find where.

My WiFi hub is still working ok as it connects to my Mac fine and I'm typing this on it. I've tried connecting the Compaq netbook to the hub directly using an ethernet cable but this doesn't work either, I'm sure it used to.

I'm not sure where to start looking in Ubuntu in order to fix this. Any help much appreciated.


Thanks,

Dave.

---

### Post by Bucky Ball on 2011-08-29
Hmm. Right click the icon. Enable Networking ticked? Untick and tick again.

---

### Post by DaveG_123 on 2011-08-29
- Yep, tried it, no luck I'm afraid.

---

### Post by Bucky Ball on 2011-08-29
Strange. You just switched on and it was like this, no network? Did you do an update or upgrade to cause it? Anything you can think of?

Perhaps open a terminal and paste this in:

```
sudo lshw -C network
```

... and paste the result back here. ;)

---

### Post by DaveG_123 on 2011-08-29
Hi,

This is the respose I get when I type that command into the terminal.

dave@Daves-Compaq-Mini:~$ sudo lshw -C network
[sudo] password for dave: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress
       configuration: latency=0
       resources: memory:feafc000-feafffff
dave@Daves-Compaq-Mini:~$ 


It was working for a while, say ten minutes or so then when I opened a new tab it stopped.

As far as I'm aware I haven't installed any new updates or other software recently.

Thanks,

Dave.

---

### Post by wildmanne39 on 2011-08-29
Hi, according to the information you posted you no longer have the driver installed.

Please run these commands and post the output here.
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by DaveG_123 on 2011-08-29
Hi here's what I got when I typed those commands, in the same order.

lspci -nn | grep 0280:
```
01:00.0 Network controller [[COLOR=Red]0280[/COLOR]]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```iwconfig:
```
lo         no wireless extensions.
```rfkill list all:
```

0: hp-wifi:Wireless LAN
            Soft blocked: no
            Hard blocked: no
1: hp-bluetooth: Bluetooth
            Soft blocked: yes
            Hard blocked: no

```lsmod:
```

Module                  Size  Used by
nls_iso8859_1           3261  0 
nls_cp437               4931  0 
vfat                    9201  0 
fat                    48240  1 vfat
usb_storage            40204  0 
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_idt      54919  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
i915                  295435  3 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
joydev                  8767  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                  5223  0 
drm                   168060  3 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
intel_agp              26566  2 i915
snd                    49038  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 i915
videodev               43098  1 uvcvideo
lp                      7342  0 
video                  18712  1 i915
v4l1_compat            13359  2 uvcvideo,videodev
soundcore                880  1 snd
led_class               2633  0 
psmouse                59033  0 
output                  1883  1 video
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
serio_raw               4022  0 
agpgart                32011  2 drm,intel_agp
parport                31492  3 parport_pc,ppdev,lp
sky2                   45127  0 

```Thanks,
Dave.

---

### Post by wildmanne39 on 2011-08-29
Hi, try this and and see if it comes back on.
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer
```
then unplug your wired connection and restart your computer.
Thank you

---

### Post by DaveG_123 on 2011-08-29
- My wired connection doesn't seem to be working either so when I run this command it gets so far and then says "E: Unable to locate package br3-fwcutter"

Dave.

---

### Post by wildmanne39 on 2011-08-29
Hi, try this first then run the other command again if this succeeds.
```
sudo apt-get update && sudo apt-get upgrade
```if it does not work please post the errors here.
Thank you

---

### Post by DaveG_123 on 2011-08-29
- Before going any further are you assuming my wired connection is working? Unfortunately it doesn't work either.

Dave.

---

### Post by wildmanne39 on 2011-08-29
Hi, that is what I was trying to find out with the last command I gave you.
Ok lets try this.

Down load the zip file on a computer with an internet connection to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. 

Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
see if that works.
Thank you

---

### Post by DaveG_123 on 2011-08-29
The B43 folder already exists but it won't let me delete it or put anything into it. It says permission denied even though I'm an admin on this machine.

---

### Post by wildmanne39 on 2011-08-29
Hi, ok just run these commands then and it should work.
```
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thank you

---

### Post by DaveG_123 on 2011-08-29
When I type the 2nd line (sudo rmmod -f b43) I get the response "ERROR: Removing 'b43' : No such file or directory" and yet I can see it in the finder but with a small 'x' on the folder icon.

---

### Post by wildmanne39 on 2011-08-29
Hi, ok just continue and see what happens when you get finished.
Thank you

---

### Post by DaveG_123 on 2011-08-29
Ok, I've entered all those commands and nothing seems to have happened, will it need a restart?

Thanks.

---

### Post by wildmanne39 on 2011-08-29
Hi, post the results of these commands please:
```
dmesg | grep wlan0
```
```
dmesg | grep b43
```
```
lsmod | grep b43
```
```
sudo iwlist scan
```
```
rfkill list all
```
Thank you

---

### Post by DaveG_123 on 2011-08-29
I get no response for the first three commands but for "sudo iwlist scan" returns:

```
 lo      Interface doesn't support scanning
```
and for "rfkill list all" returns:
```

0: hp-wifi: Wireless LAN
            Soft blocked: no
            Hard blocked: no
1: hp-bluetooth: Bluetooth
            Soft blocked: yes
            Hard blocked: no

```
Thanks,
Dave.

---

### Post by wildmanne39 on 2011-08-29
Hi, try this please and post the outcome.
```
lsmod
```
Also did you use to connect with bluetooth?
Thank you

---

### Post by Bucky Ball on 2011-08-29
What about System>Administration>Additional Drivers. For some reason the B43 drivers are possibly switched off. Tick it and enable. If you didn't uninstall the B43 drivers they should still be there.

Wildmanne, if you'd have read first post you would realise OP clearly states they have NO wired or wireless connection, no connection to the internet, therefore a lot of your instructions were redundant. ;)

PS: Not sure why you'd want to remove the B43 stuff only to reinstall it again. It's already there. Look elsewhere for the problem.

---

### Post by wildmanne39 on 2011-08-29
Hi, Bucky Ball if you look at his lsmod information there is no broadcom drivers loaded.

---

### Post by wildmanne39 on 2011-08-29
Hi, if the driver is still there but just not loading try this:
```
sudo modprobe b43
```
if that does not work please post the results of 
```
cat /etc/modprobe.d/blacklist.conf

```
Thank you

---

### Post by Bucky Ball on 2011-08-29
Also, is there a button or combination of keys on your laptop that switches wireless off and on? May sound like a silly question but ...

---

### Post by DaveG_123 on 2011-08-30
Response to lsmod:

```

Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_idt      54919  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
i915                  295435  3 
snd_seq_midi_event      6047  1 snd_seq_midi
joydev                  8767  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         30200  1 i915
uvcvideo               55847  0 
hp_wmi                  5223  0 
videodev               43098  1 uvcvideo
drm                   168060  3 i915,drm_kms_helper
snd                    49038  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13359  2 uvcvideo,videodev
led_class               2633  0 
psmouse                59033  0 
i2c_algo_bit            5168  1 i915
intel_agp              26566  2 i915
video                  18712  1 i915
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
output                  1883  1 video
parport                31492  3 parport_pc,ppdev,lp
sky2                   45127  0 

```

---

### Post by wildmanne39 on 2011-08-30
Hi, the lsmod information you just posted is that after you ran the commands in post 23 or before?
Thank you

---

### Post by DaveG_123 on 2011-08-30
- It's before. Shall I try it again after the commands in post 23?

---

### Post by wildmanne39 on 2011-08-30
Hi, yes if it does not start working after you run the first command in that post. Then let us see the results of the second command in that post please, and the lsmod again.
Thank you

---

### Post by DaveG_123 on 2011-08-30
Hi, I don't seem to get any response from "sudo modprobe b43".

cat /etc/modprobe.d/blacklist.conf returns

```

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
```


The lsmod command then returns
```

Module                  Size  Used by
b43                   168681  0 
ssb                    39320  1 b43
mac80211              231959  1 b43
cfg80211              144694  2 b43,mac80211
nls_iso8859_1           3261  0 
nls_cp437               4931  0 
vfat                    9201  0 
fat                    48240  1 vfat
usb_storage            40204  0 
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_idt      54919  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
i915                  295435  3 
snd_seq_midi_event      6047  1 snd_seq_midi
joydev                  8767  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         30200  1 i915
uvcvideo               55847  0 
hp_wmi                  5223  0 
videodev               43098  1 uvcvideo
drm                   168060  3 i915,drm_kms_helper
snd                    49038  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13359  2 uvcvideo,videodev
led_class               2633  1 b43
psmouse                59033  0 
i2c_algo_bit            5168  1 i915
intel_agp              26566  2 i915
video                  18712  1 i915
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
output                  1883  1 video
parport                31492  3 parport_pc,ppdev,lp
sky2                   45127  0 

```

I can't see a key combination that would turn the wifi on and off.  There's a button for turning the bluetooth on and off on the front but I  can't see anything for the wifi.


Thanks,

Dave.

---

### Post by wildmanne39 on 2011-08-30
Hi, the first command I gave you loaded the driver,go to the top right of your screen and click on the network icon and make sure there is a check by enable wireless. Then see if the network you want to connect to is listed and enter the password for it and you should be able to connect.
you can not have any other connection connected when you do this.
Thank you

---

### Post by DaveG_123 on 2011-08-30
- Still not working I'm affraid.

I can't find an enable wireless checkbox, there's an enable networking one and this is checked.

Thanks.

---

### Post by wildmanne39 on 2011-08-30
Hi, are you using network manager? or wicd? this is what mine looks like, if you do not figure it out post a screen shot of yours please, it is possible that you need to reinstall network manager.
Thank you

---

### Post by Bucky Ball on 2011-08-31
> **Bucky Ball said:**
> What about System>Administration>Additional Drivers? 

...? Is there anything there? Just a shot. If the B43 drivers are then you just need to enable them. If not, then not installed and that is strange they should up and disappear like that. You will have something in there if you are using the B43 drivers (or STA). One of those drivers is on the install CD, one not. Can't remember which. ;)

---

### Post by DaveG_123 on 2011-08-31
Hi, sorry for the slow reply.

I'm not sure what I'm using so I've attached a screen shot.

Thanks,

Dave.

---

### Post by wildmanne39 on 2011-08-31
Hi, I want to check a few things now that your driver is loaded.
```
ps aux | grep nm-apple
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
dmesg | grep wlan0
```
```
dmesg | grep b43
```
```
lsmod | grep b43
```
```
dmesg | egrep 'b43|firm'
```
```
sudo lshw -C network
```
```
iwconfig
```
I know some of these commands have been ran before but that was before the driver was loaded.

I am checking to see if network manager is running, and if the driver is still loaded, and several other things.
Thank you

---

