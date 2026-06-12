---
title: "No sound on NVidia HDMI"
date: 2011-12-16
forum: Multimedia Software
---

### Post by aasgaa on 2011-12-16
After trying to solve this issue for quite a long time I need help from some experts.
 
The following document was a great help in building up my understanding of the concept:
[ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)
 
My last shot was going through the following procedure:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
 
All the output information from this procedure can be found here:
[http://www.alsa-project.org/db/?f=f19fc6acfb2cd26b97c14876f0aa2667ad3d1c04](http://www.alsa-project.org/db/?f=f19fc6acfb2cd26b97c14876f0aa2667ad3d1c04)
 
Sound on the Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) is ok.

Thanks!

---

### Post by BicyclerBoy on 2011-12-16
You need to upgrade the alsa kernel module from 1.0.21 --> 1.0.23

Somehow you have the correct user space at 1.0.24 (iQuik ppa ??)

You need to install the linux-backport-modules-alsa-lucid-generic package.
This package & iQuik ppa is the best solution for 10.04..

reboot
rerun the alsa info script & repost the new link..

You also appear to be using nouveau nVidia driver or you have not blacklisted it correctly.
The vga16fb should also be blacklisted.
Both should be blacklisted by nVidia driver installer script..

nVidia GPU HDMI audio will only work with nVidia proprietary driver.

---

### Post by aasgaa on 2011-12-16
Thanks BicyclerBoy!
 
Now I Can see the the card with aplay -L, and I can play sound with:
aplay -D plughw:NVidia,7 /usr/share/sounds/alsa/Front_Center.wav

Unfortunately still no sound from the applications...
 
One more valuable tip from you?

---

### Post by aasgaa on 2011-12-16
Forgot the link to the result from the new run of the alsa info script:
 
[http://www.alsa-project.org/db/?f=654b54403afb6b180610d2d7ac6b9eaf9555c5c7](http://www.alsa-project.org/db/?f=654b54403afb6b180610d2d7ac6b9eaf9555c5c7)

---

### Post by BicyclerBoy on 2011-12-16
Don't change anything in these cmd..
Try each of :
speaker-test -c 2 -r 48000 -D hw:1,7
speaker-test -c 2 -r 48000 -D hw:1,8
speaker-test -c 2 -r 48000 -D hw:1,9

close & reopen terminal after each cmd..

ls -al /proc/asound/card1/eld#*

One of above eld# files should be non-zero size...

---

### Post by aasgaa on 2011-12-17
After opening a terminal and performing the command
speaker-test -c 2 -r 48000 -D hw:1,7
the sound is working, also in other applications.
 
After reboot I need to reissue the command...
 
Some configuration missing?
 
Some additional info:
[EMAIL="olav@$"][FONT=Courier New]$[/FONT][/EMAIL][FONT=Courier New] ls -al /proc/asound/card1/eld#*
-rw-r--r-- 1 root root 0 2011-12-17 07:45 /proc/asound/card1/eld#0.0
-rw-r--r-- 1 root root 0 2011-12-17 07:45 /proc/asound/card1/eld#1.0
-rw-r--r-- 1 root root 0 2011-12-17 07:45 /proc/asound/card1/eld#2.0
-rw-r--r-- 1 root root 0 2011-12-17 07:45 /proc/asound/card1/eld#3.0
[/FONT]
[EMAIL="v@xbmc01:~$"][FONT=Courier New]$[/FONT][/EMAIL][FONT=Courier New] cat /proc/asound/card1/eld#1.0
monitor_present         1
eld_valid               1
monitor_name            SAMSUNG[/FONT]
[FONT=Courier New]connection_type         HDMI
eld_version             [0x2] CEA-861D or below
edid_version            [0x3] CEA-861-B, C or D
manufacture_id          0x2d4c
product_id              0x470
port_id                 0x10000
support_hdcp            0
support_ai              0
audio_sync_delay        0
speakers                [0x1] FL/FR
sad_count               1
sad0_coding_type        [0x1] LPCM
sad0_channels           2
sad0_rates              [0xe0] 44100 48000 88200
sad0_bits               [0xe0000] 16 20 24
[/FONT]

---

### Post by BicyclerBoy on 2011-12-17
Okay hw:1,7 is the HDMI codec; it correlates to eld#1.0..

Because you are using lucid 10.04, pulse-audio does not enumerate more than one alsa sub-device..

You add extra outputs to PulseAudio by editing /etc/pulse/default.pa, and adding line:

load-module module-alsa-sink device=hw:1,7
(make sure there is only one entry like this )
logout/login
Then run
pavucontrol 
and select the HDMI output to be default..

If you need to make some other alsa only programs default to HDMI you can edit /etc/asound.conf..but I doubt this is necessary.

---

### Post by brundles on 2012-01-14
Thanks for the info BicyclerBoy - solves the problem with HDMI audio for the Nvidia card I've got!

---

