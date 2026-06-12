---
title: "Acer Aspire wireless card not working"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by haxifix on 2011-12-27
Hello, I have just purchased an Acer Aspire 5742G-6426 and I'm having some problems.  I can't find drivers for the "Acer Nplify 802.11 b/g/n" integrated wireless card.  I am running Ubuntu 10.10 64bit and would like to know what driver package I need and how to install it in order to get my wireless LAN working.

Thank you in advance for any help :)

---

### Post by wildmanne39 on 2011-12-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by haxifix on 2011-12-28
Here is the output of the commands in the order you gave them to me.

haxifix@haxifix-pc:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux haxifix-pc 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 x86_64 GNU/Linux
haxifix@haxifix-pc:~$ ^C
haxifix@haxifix-pc:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Kernel driver in use: tg3
    Kernel modules: tg3
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4358]
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
haxifix@haxifix-pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

haxifix@haxifix-pc:~$ rfkill list all
haxifix@haxifix-pc:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   279008  1 
snd_hda_intel          25805  2 
joydev                 11104  0 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
softcursor              1565  1 bitblit
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
vga16fb                12757  1 
snd_timer              23649  2 snd_pcm,snd_seq
uvcvideo               62851  0 
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vgastate                9857  1 vga16fb
i915                  324711  2 
videodev               40518  1 uvcvideo
nouveau               515227  0 
snd                    71283  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                65040  0 
v4l1_compat            15495  2 uvcvideo,videodev
ttm                    61007  1 nouveau
soundcore               8052  1 snd
drm_kms_helper         30742  2 i915,nouveau
v4l2_compat_ioctl32    11892  1 videodev
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
serio_raw               4918  0 
intel_agp              29319  2 i915
drm                   198886  6 i915,nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  2 i915,nouveau
led_class               3764  0 
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  3 
tg3                   122382  0

---

### Post by haxifix on 2011-12-28
Okay, so I downloaded the b43-fwcutter package from command line and had it extract and setup everything.  It then said that I need to go to Hardware Drivers application and enable them but when I go to my Hardware Drivers app, it tells me that no drivers are currently being used.  Is there anything I can do to enable the drivers?

---

### Post by wildmanne39 on 2011-12-28
Hi, please remove b43-fwcutter you do not need it and then run these commands one line at a time:
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```
Then unplug your wired connection and reboot.
Thanks

---

### Post by haxifix on 2011-12-29
I just did what you told me and after i rebooted I still wasn't connected to the Internet -_-

I went to the Hardware Drivers too after I rebooted and there was nothing there either.

---

### Post by wildmanne39 on 2011-12-29
Hi, please post the output of:
```
lsmod
```
```
iwconfig
rfkill list all
nm-tool
```
```
sudo iwlist scan
```
```
cat /etc/modprobe.d/blacklist.conf
```
I know some of the commands you have all ready run but I need to see them again since we changed drivers.
Thanks

---

### Post by haxifix on 2011-12-29
haxifix@haxifix-pc:~$ lsmod
Module                  Size  Used by
joydev                 11104  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   279104  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
i915                  326140  2 
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
uvcvideo               62915  0 
snd_timer              23681  2 snd_pcm,snd_seq
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
softcursor              1565  1 bitblit
videodev               40550  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
vga16fb                12757  1 
vgastate                9857  1 vga16fb
v4l2_compat_ioctl32    11892  1 videodev
snd                    71283  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               515227  0 
psmouse                65040  0 
ttm                    61039  1 nouveau
soundcore               8052  1 snd
led_class               3764  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
drm_kms_helper         30742  2 i915,nouveau
serio_raw               4918  0 
drm                   200384  6 i915,nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  2 i915,nouveau
intel_agp              29319  2 i915
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38350  2 
tg3                   122382  0 
haxifix@haxifix-pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

haxifix@haxifix-pc:~$ rfkill list all
haxifix@haxifix-pc:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        B8:70:F4:FD:ED:61

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.130
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


haxifix@haxifix-pc:~$ sudo iwlist scan
[sudo] password for haxifix: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

haxifix@haxifix-pc:~$ cat /etc/modprobe.d/blacklist.conf
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


I had my ethernet cord plugged into during these commands so I don't know if that would affect the output.  Let me know if you would like me to run them again without my ethernet cord plugged in.

---

### Post by wildmanne39 on 2011-12-29
Hi, we are getting closer please post:
```
dmesg | egrep 'wl|firm|radio|switch|wlan0|etork'
```
Thanks

---

### Post by haxifix on 2011-12-29
haxifix@haxifix-pc:~$ dmesg | egrep 'wl|firm|radio|switch|wlan0|etork'
[   13.224843] Console: switching to colour frame buffer device 80x30
[   13.518952] elantech.c: assuming hardware version 2, firmware version 4.2.19
[  383.453800] SMP alternatives: switching to UP code
[  383.459158] SMP alternatives: switching to SMP code

---

### Post by wildmanne39 on 2011-12-29
Hi, lets run these commands again make sure you are connected to the internet then run:
```
sudo apt-get update
```
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Watch for errors as the command runs.
When it is done unplug your wired connection and reboot if it does not come on please post:
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by haxifix on 2011-12-29
When I try to reinstall bcmwl-kernel-source it tells me: E: Couldn't find package reinstall

Any help?

---

### Post by wildmanne39 on 2011-12-29
Hi, sorry I am getting tired and I missed putting the two dashes in front of the reinstall command but I fixed it just copy and paste, now it should work.
Thanks

---

### Post by haxifix on 2011-12-29
It did not come on -_-

Here is the lsmod output:

haxifix@haxifix-pc:~$ lsmod
Module                  Size  Used by
joydev                 11104  0 
binfmt_misc             7960  1 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   279104  1 
ppdev                   6375  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
i915                  326140  2 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71283  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  1 
vgastate                9857  1 vga16fb
soundcore               8052  1 snd
uvcvideo               62915  0 
videodev               40550  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
led_class               3764  0 
nouveau               515227  0 
ttm                    61039  1 nouveau
drm_kms_helper         30742  2 i915,nouveau
psmouse                65040  0 
intel_agp              29319  2 i915
serio_raw               4918  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
drm                   200384  6 i915,nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  2 i915,nouveau
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38350  2 
tg3                   122382  0

---

### Post by wildmanne39 on 2011-12-29
Hi, please try:
```
sudo modprobe wl
```
Thanks

---

### Post by haxifix on 2011-12-29
I typed that into the console and it didn't output anything.  Do you want me to unplug my wireless connection and reboot again?

---

### Post by wildmanne39 on 2011-12-29
Hi, it would not show any output but if it worked your wireless would have come on.

With your wired connection plugged in go to additional drivers and see if there is a driver for your card there now if so activate it and then reboot.
Thanks

---

### Post by haxifix on 2011-12-29
It did not turn on my wireless and my application isn't called Additional Drivers it's called Hardware Drivers.  Don't know if it's the same thing or not, but it says that there are no proprietary drivers in use on the system.

---

### Post by wildmanne39 on 2011-12-29
Hi, yes it is the same thing and there are no drivers to activate in there?
Thanks

---

### Post by haxifix on 2011-12-29
Nope, or at least I can't see them.  The entire application is empty except for on the top it says "No Proprietary Drivers are in use on this system".

---

### Post by wildmanne39 on 2011-12-29
Hi, open synaptic type broadcom and see if bcmwl-kernel-source is installed if not install it, also after you install it and reboot with wired connection unplugged if it does not come on take a screenhot of what is installed under broadcom in synaptic and post it here you can do that by alt+printscreen button.
Thanks

---

### Post by haxifix on 2011-12-29
It did not come on, here is the screenshot.

[IMG]file:///home/haxifix/Desktop/Screenshot-Synaptic%20Package%20Manager%20.png[/IMG]

---

### Post by wildmanne39 on 2011-12-29
Hi, ok post the output of:
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wmi -e etork | tail -n75
```
Thanks

---

### Post by haxifix on 2011-12-29
This is with my wired connection plugged in, don't know if it makes a difference:

haxifix@haxifix-pc:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wmi -e etork | tail -n75
[sudo] password for haxifix: 
Sorry, try again.
[sudo] password for haxifix: 
Jan  1 10:03:46 haxifix-pc kernel: [    8.342716] acer-wmi: Acer Laptop ACPI-WMI Extras
Jan  1 10:03:46 haxifix-pc kernel: [    8.343581] acer-wmi: Unable to detect available WMID devices
Jan  1 10:03:46 haxifix-pc kernel: [    9.418506] elantech.c: assuming hardware version 2, firmware version 4.2.19
Jan  1 10:10:33 haxifix-pc kernel: [   10.248224] acer-wmi: Acer Laptop ACPI-WMI Extras
Jan  1 10:10:33 haxifix-pc kernel: [   10.249076] acer-wmi: Unable to detect available WMID devices
Jan  1 10:10:33 haxifix-pc kernel: [   12.771871] elantech.c: assuming hardware version 2, firmware version 4.2.19
Jan  1 10:13:45 haxifix-pc kernel: [   13.079161] acer-wmi: Acer Laptop ACPI-WMI Extras
Jan  1 10:13:45 haxifix-pc kernel: [   13.079899] acer-wmi: Unable to detect available WMID devices
Jan  1 10:13:45 haxifix-pc kernel: [   13.518952] elantech.c: assuming hardware version 2, firmware version 4.2.19
Jan  1 05:09:40 haxifix-pc kernel: [   14.090808] acer-wmi: Acer Laptop ACPI-WMI Extras
Jan  1 05:09:40 haxifix-pc kernel: [   14.105569] acer-wmi: Unable to detect available WMID devices
Jan  1 05:09:40 haxifix-pc kernel: [   14.510046] elantech.c: assuming hardware version 2, firmware version 4.2.19
Dec 29 20:03:11 haxifix-pc kernel: [  234.133029] wl: module license 'MIXED/Proprietary' taints kernel.
Jan  1 05:28:22 haxifix-pc kernel: [   13.890928] acer-wmi: Acer Laptop ACPI-WMI Extras
Jan  1 05:28:22 haxifix-pc kernel: [   13.891711] acer-wmi: Unable to detect available WMID devices
Jan  1 05:28:22 haxifix-pc kernel: [   14.595148] elantech.c: assuming hardware version 2, firmware version 4.2.19

---

### Post by wildmanne39 on 2011-12-29
Hi, I have to get off for a little while to eat supper.

Also with the last command there should have been 75 lines.
Thanks

---

### Post by haxifix on 2011-12-29
This is all that comes up in the console when i run the command:

haxifix@haxifix-pc:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wmi -e etork | tail -n75
Jan  1 10:03:46 haxifix-pc kernel: [    8.342716] acer-wmi: Acer Laptop ACPI-WMI Extras
Jan  1 10:03:46 haxifix-pc kernel: [    8.343581] acer-wmi: Unable to detect available WMID devices
Jan  1 10:03:46 haxifix-pc kernel: [    9.418506] elantech.c: assuming hardware version 2, firmware version 4.2.19
Jan  1 10:10:33 haxifix-pc kernel: [   10.248224] acer-wmi: Acer Laptop ACPI-WMI Extras
Jan  1 10:10:33 haxifix-pc kernel: [   10.249076] acer-wmi: Unable to detect available WMID devices
Jan  1 10:10:33 haxifix-pc kernel: [   12.771871] elantech.c: assuming hardware version 2, firmware version 4.2.19
Jan  1 10:13:45 haxifix-pc kernel: [   13.079161] acer-wmi: Acer Laptop ACPI-WMI Extras
Jan  1 10:13:45 haxifix-pc kernel: [   13.079899] acer-wmi: Unable to detect available WMID devices
Jan  1 10:13:45 haxifix-pc kernel: [   13.518952] elantech.c: assuming hardware version 2, firmware version 4.2.19
Jan  1 05:09:40 haxifix-pc kernel: [   14.090808] acer-wmi: Acer Laptop ACPI-WMI Extras
Jan  1 05:09:40 haxifix-pc kernel: [   14.105569] acer-wmi: Unable to detect available WMID devices
Jan  1 05:09:40 haxifix-pc kernel: [   14.510046] elantech.c: assuming hardware version 2, firmware version 4.2.19
Dec 29 20:03:11 haxifix-pc kernel: [  234.133029] wl: module license 'MIXED/Proprietary' taints kernel.
Jan  1 05:28:22 haxifix-pc kernel: [   13.890928] acer-wmi: Acer Laptop ACPI-WMI Extras
Jan  1 05:28:22 haxifix-pc kernel: [   13.891711] acer-wmi: Unable to detect available WMID devices
Jan  1 05:28:22 haxifix-pc kernel: [   14.595148] elantech.c: assuming hardware version 2, firmware version 4.2.19

Don't know what is going on if there is supposed to be 75 lines.

---

### Post by wildmanne39 on 2011-12-29
Hi, I think the problem is that you are using ubuntu 10.04 is there any reason you are not using 11.10 the reason I ask is your wireless card is fairly new it shows it is supported but it has and asterik by it.

I also notice that you have not ran updates you might run:
```
sudo apt-get update && sudo apt-get upgrade
```
then reboot, then run:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Then go into your hardware drivers and see if the driver is there if so install and reboot.
Thanks

---

### Post by haxifix on 2011-12-29
I am actually running this because it was the only disk I currently have, because it is LTS and because I was having problems with 11.10.  I also do not like Unity and didn't want to mess around with removing it because the last time I tried, it failed and my computer wouldn't boot.  I will try what you said and repost back if it worked or not.

---

### Post by wildmanne39 on 2011-12-29
Hi, you can also run xubuntu or lubuntu they do not use unity.
Thanks

---

### Post by haxifix on 2011-12-29
Is there anything wrong with Ubuntu 10.04?

---

### Post by wildmanne39 on 2011-12-29
Hi, no but I think it is not supporting your wireless card correctly but run those commands and see what happens.

I know your wireless card is newer so the driver that was made back then did not know anything about that card.

Is this a fairly new computer?
Thanks

---

### Post by haxifix on 2011-12-29
Oh and I just updated and upgraded and then rebooted, ran the command and checked the hardware drivers again and there is nothing.  What is xubuntu and lubuntu?

---

### Post by wildmanne39 on 2011-12-29
Hi, they are just another distribution of ubuntu, they are lighter on resources and do not use unity, is this a new computer?

I am tired tonight maybe I am missing something but I suspect it is the version of ubuntu with your card.
Thanks

---

### Post by haxifix on 2011-12-29
Well, I just reisntalled Ubuntu 10.04 from 12.04.  I had wireless working on 12.04 with the b43-fwcutter library but there were a lot of things I didn't like and a lot of problems that I would have to fix.

Would downloading the newest version of xubuntu and reformatted and installing it be the best option do you think?

---

### Post by wildmanne39 on 2011-12-29
Hi, 12.04 has just been under testing for 2 months you should have installed 11.10 but if you do not like unity you can run xubuntu or Lubuntu just make sure to run 11.10 so you will have the latest drivers and the b43 driver is the one I prefer but it is not tested for your card yet so it may have issues but the sta driver should work it is called wl driver but we will have to blacklist a few thing to make it work.
Thanks

---

### Post by haxifix on 2011-12-29
Can I upgrade to 11.10 and then install xubuntu without reformatting and having to reinstall ubuntu all over again?

---

### Post by wildmanne39 on 2011-12-29
Hi, you can but there are such big differences in 10.04 and 11.10 it usually causes a lot of problems. Plus unless you are going to do it from the livecd you would have upgrade from 10.04 to 11.04 then to 11.10.
Thanks

---

### Post by haxifix on 2011-12-29
So, what I should do is go on my desktop, download the newest version (11.10) of xbuntu off of their website, burn it to my flash drive and then install it over my current install of ubuntu?  If so, will it automatically have support for my graphics card or do I have to enable the drivers and stuff like now?

---

### Post by wildmanne39 on 2011-12-29
Hi, you will still have to enable the drivers.

Yes that is how to do it and make sure you reformat the partitions.

If you want you can wait until tomorrow and I will ask someone to take a look.
Thanks

---

### Post by haxifix on 2011-12-29
I will reformat and install it tonight and then look at what commands you told me to enable it and I will try it.  If it doesn't work I will repost on this tomorrow so that you see it.

Thank you for all your help :)

---

### Post by wildmanne39 on 2011-12-29
Hi, ok like I said we may have to blacklist a few drivers.
Thanks

---

### Post by haxifix on 2011-12-30
Hello, so I put Xubuntu 11.10 on my flashdrive and when I boot into it, it just says SYSLINUX then some other stuff and it just sits there and blinks.  I let it sit there for about 10min before shutting it off and trying it again but it did the same thing.  How can I fix this problem?

---

### Post by haxifix on 2011-12-30
Okay, so I'm just using my current Ubuntu 10.04 install to upgrade to 11.10.  Once it is done upgrading, what should I do to get my wireless working?

---

### Post by wildmanne39 on 2011-12-30
Hi, install all updates then reboot go to this link:
[http://ubuntuforums.org/showthread.php?p=11573648#post11573648](http://ubuntuforums.org/showthread.php?p=11573648#post11573648)
run the commands in post 4 then reboot and it should work.

Also if you had issues with installing you will probably have issues with it when it is installed, here is a link for what is the most likely cause.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
if you need more help with that issue you will need to start another thread in general or beginners section then come back if you need more help with internet and please let me know if it works.
Thanks

---

### Post by rpc101 on 2012-02-28
I just purchased an Acer Aspire that has the same Broadcom wireless chipset as yours (based on the lspci output).  Last night I installed Ubuntu 10.10 on it and the wireless network interface was also not working for me.  After trying several other things that didn't work, I did find a solution which I will pass along in case it might still be useful to you and/or others.

I located the official web site for the Broadcom 802.11 Linux STA driver at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).  This driver is distributed in a form that allows it to be compatible with a variety of Linux kernels and distributions.  I downloaded the 64 bit version and followed the directions in the README file to build and install the driver. This was simple process and my wireless interface has been working perfectly since the new driver was installed.

---

