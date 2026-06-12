---
title: "Headphones and HP dv6"
date: 2009-10-23
forum: Multimedia Software
---

### Post by Neezer on 2009-10-23
Hi all,

I have a bit of a situation here. When I plug my headphones into the jack, my speakers on my HP dv6 don't turn off. I tried both speaker ports and the same thing happens with both. Any I deas?

---

### Post by Ulysses361 on 2009-10-23
Hi,

Please execute step 1 (ALSA upgrade) , reboot and then send us output from step 3 and step 4 from the following procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Regards,

Mark Rijckenberg

---

### Post by Neezer on 2009-10-23
Thanks for the help.

I am still having the headphone problem, and the volume is really low. I can barely hear the lappy speakers, and I can't get my headphones very loud either. 

When I did the ALSA config at the end of step one, It had me chose between 2 sound devices.....an intel one, and a legacy one. I chose the intel one.

here is the output from the first command in step 3.
```

nathan@lappy:~$ wget -O alsa-info.sh http://212.20.107.51/alsa-info.sh 
--2009-10-23 09:23:41--  http://212.20.107.51/alsa-info.sh
Connecting to 212.20.107.51:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2009-10-23 09:23:42--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to 212.20.107.51:80.
HTTP request sent, awaiting response... 200 OK
Length: 26584 (26K) [text/plain]
Saving to: `alsa-info.sh'

100%[======================================>] 26,584      20.8K/s   in 1.2s    

2009-10-23 09:24:00 (20.8 KB/s) - `alsa-info.sh' saved [26584/26584]


```

here is the second part of step 3
```

nathan@lappy:~$ bash alsa-info.sh --pastebin 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
ALSA Information Script v 0.4.58
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
Automatically upload ALSA information to pastebin? [y/N] : y
Uploading information to www.pastebin.ca ...  Done!

Your ALSA information is located at http://pastebin.ca/1640307

Please inform the person helping you.

```

For some reason they want you to run the same command again I think....so here goes.
```

nathan@lappy:~$ bash alsa-info.sh --pastebin 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
ALSA Information Script v 0.4.58
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
Automatically upload ALSA information to pastebin? [y/N] : y
Uploading information to www.pastebin.ca ...  Done!

Your ALSA information is located at http://pastebin.ca/1640318

Please inform the person helping you.

```

And on to step 4 I guess. It is pretty long, and I hope I'm not breaking any rules by posting it, but here goes....
```

nathan@lappy:~$ cat /proc/asound/cards;  sudo aptitude install gnome-alsamixer asoundconf-gtk alsa-utils flashplugin-nonfree-extrasound;  asoundconf list;  aplay -l;  sudo lshw -C sound;  ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn;  sudo which alsactl;  lsmod | grep snd
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdd000000 irq 2294
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "flashplugin-nonfree-extrasound"
Couldn't find any package whose name or description matched "flashplugin-nonfree-extrasound"
The following NEW packages will be installed:
  asoundconf-gtk gnome-alsamixer libgconfmm-2.6-1c2{a} 
  libglademm-2.4-1c2a{a} libpulse-mainloop-glib0{a} padevchooser{a} 
  paman{a} paprefs{a} pavucontrol{a} pavumeter{a} 
  pulseaudio-module-zeroconf{a} 
0 packages upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 417kB of archives. After unpacking 2818kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com jaunty/universe asoundconf-gtk 1.6-0ubuntu1 [6444B]
Get:2 http://us.archive.ubuntu.com jaunty/universe gnome-alsamixer 0.9.7~cvs.20060916.ds.1-2 [56.6kB]
Get:3 http://us.archive.ubuntu.com jaunty/main libgconfmm-2.6-1c2 2.24.0-0ubuntu1 [30.3kB]
Get:4 http://us.archive.ubuntu.com jaunty/main libglademm-2.4-1c2a 2.6.7-1 [21.9kB]
Get:5 http://us.archive.ubuntu.com jaunty-updates/main libpulse-mainloop-glib0 1:0.9.14-0ubuntu20.2 [34.6kB]
Get:6 http://us.archive.ubuntu.com jaunty/universe pavumeter 0.9.3-1ubuntu1 [30.1kB]
Get:7 http://us.archive.ubuntu.com jaunty/universe pavucontrol 0.9.7-1ubuntu3 [67.2kB]
Get:8 http://us.archive.ubuntu.com jaunty/universe paman 0.9.4-1ubuntu2 [92.5kB]
Get:9 http://us.archive.ubuntu.com jaunty-updates/main pulseaudio-module-zeroconf 1:0.9.14-0ubuntu20.2 [20.5kB]
Get:10 http://us.archive.ubuntu.com jaunty/universe paprefs 0.9.7-0ubuntu1 [35.2kB]
Get:11 http://us.archive.ubuntu.com jaunty/universe padevchooser 0.9.3-2ubuntu4 [21.6kB]
Fetched 417kB in 21s (19.2kB/s)                                                 
Selecting previously deselected package asoundconf-gtk.
(Reading database ... 148257 files and directories currently installed.)
Unpacking asoundconf-gtk (from .../asoundconf-gtk_1.6-0ubuntu1_all.deb) ...
Selecting previously deselected package gnome-alsamixer.
Unpacking gnome-alsamixer (from .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_amd64.deb) ...
Selecting previously deselected package libgconfmm-2.6-1c2.
Unpacking libgconfmm-2.6-1c2 (from .../libgconfmm-2.6-1c2_2.24.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.7-1_amd64.deb) ...
Selecting previously deselected package libpulse-mainloop-glib0.
Unpacking libpulse-mainloop-glib0 (from .../libpulse-mainloop-glib0_1%3a0.9.14-0ubuntu20.2_amd64.deb) ...
Selecting previously deselected package pavumeter.
Unpacking pavumeter (from .../pavumeter_0.9.3-1ubuntu1_amd64.deb) ...
Selecting previously deselected package pavucontrol.
Unpacking pavucontrol (from .../pavucontrol_0.9.7-1ubuntu3_amd64.deb) ...
Selecting previously deselected package paman.
Unpacking paman (from .../paman_0.9.4-1ubuntu2_amd64.deb) ...
Selecting previously deselected package pulseaudio-module-zeroconf.
Unpacking pulseaudio-module-zeroconf (from .../pulseaudio-module-zeroconf_1%3a0.9.14-0ubuntu20.2_amd64.deb) ...
Selecting previously deselected package paprefs.
Unpacking paprefs (from .../paprefs_0.9.7-0ubuntu1_amd64.deb) ...
Selecting previously deselected package padevchooser.
Unpacking padevchooser (from .../padevchooser_0.9.3-2ubuntu4_amd64.deb) ...
Processing triggers for man-db ...
Setting up asoundconf-gtk (1.6-0ubuntu1) ...
Setting up gnome-alsamixer (0.9.7~cvs.20060916.ds.1-2) ...

Setting up libgconfmm-2.6-1c2 (2.24.0-0ubuntu1) ...

Setting up libglademm-2.4-1c2a (2.6.7-1) ...

Setting up libpulse-mainloop-glib0 (1:0.9.14-0ubuntu20.2) ...

Setting up pavumeter (0.9.3-1ubuntu1) ...

Setting up pavucontrol (0.9.7-1ubuntu3) ...

Setting up paman (0.9.4-1ubuntu2) ...

Setting up pulseaudio-module-zeroconf (1:0.9.14-0ubuntu20.2) ...
Setting up paprefs (0.9.7-0ubuntu1) ...

Setting up padevchooser (0.9.3-2ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Names of available sound cards:
Intel
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
total 0
crw-rw----+  1 root audio 116, 33 2009-10-23 09:16 timer
crw-rw----+  1 root audio 116,  1 2009-10-23 09:16 seq
crw-rw----+  1 root audio 116, 17 2009-10-23 09:16 pcmC0D1p
crw-rw----+  1 root audio 116,  6 2009-10-23 09:16 hwC0D2
crw-rw----+  1 root audio 116,  5 2009-10-23 09:16 hwC0D1
crw-rw----+  1 root audio 116,  4 2009-10-23 09:16 hwC0D0
crw-rw----+  1 root audio 116,  0 2009-10-23 09:16 controlC0
drwxr-xr-x   2 root root      220 2009-10-23 09:16 .
crw-rw----+  1 root audio 116, 24 2009-10-23 09:16 pcmC0D0c
crw-rw----+  1 root audio 116, 16 2009-10-23 09:22 pcmC0D0p
drwxr-xr-x  16 root root     4220 2009-10-23 09:34 ..
Sound Driver:3.8.1a-980706 (ALSA v1.0.21 emulation code)
Kernel: Linux lappy 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xdd000000 irq 2294

Audio devices:
0: STAC92xx Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Nvidia ID 3
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 9200M GS [10de:06e8] (rev a1)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
06:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technologies, Inc. IEEE 1394 Host Controller [197b:2380]
06:00.1 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
06:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
06:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
06:00.4 System peripheral [0880]: JMicron Technologies, Inc. xD Host Controller [197b:2384]
/usr/sbin/alsactl
snd_hda_codec_idt      75664  1 
snd_hda_intel          40288  3 
snd_hda_codec          97408  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              16904  1 snd_hda_codec
snd_pcm_oss            51872  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99464  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          11652  0 
snd_seq_oss            40320  0 
snd_seq_midi           15936  0 
snd_rawmidi            34080  1 snd_seq_midi
snd_seq_midi_event     16640  2 snd_seq_oss,snd_seq_midi
snd_seq                66976  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              33168  2 snd_pcm,snd_seq
snd_seq_device         16532  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    83144  20 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18960  2 snd_hda_intel,snd_pcm

```

So there is that....Now what?


**EDIT:** I did some digging, and found the alsamixer. I was able to turn the master volume and other settings to a higher volume....Is there a problem if I turn them all to 100%? 

I still am having the headphones problem though.

---

### Post by Ulysses361 on 2009-10-23
Hi,

a) Open a terminal and edit /etc/modprobe.d/alsa-base.conf as follows:

sudo gedit /etc/modprobe.d/alsa-base.conf

Remove the following lines from the /etc/modprobe.d/alsa-base.conf file:

snd_hda_intel: model=hp-dv5
snd_hda_intel: model=hp-dv5
snd-hda-intel: model=hp-m4 enable_msi=1

Add the following 4 lines to the end of the file after "options snd-pcsp index=-2"

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-m4

b) Save change to file /etc/modprobe.d/alsa-base.conf , reboot and retest sound

c) Make sure to increase volume on the Master, Front, PCM and surround channel to 100% 
If 100% sound volume causes distortion, please decrease volume to 77%

Regards,

Mark Rijckenberg

---

### Post by Neezer on 2009-10-23
Still getting the same problem...but I didn't have the first two lines you suggested in there....I just commented out the third one with a #.

---

### Post by markbuntu on 2009-10-23
Here are all the options from the snd-hda-intel database that people have reported to work with the DV-6. Some of them require a newer alsa version as noted. 

 
HP dv6 1100.EO
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

HP DV6z
ALSA 1.0.20
options snd-hda-intel model=dell-m4 enable_msi=1

hp dv6-1007tx
alsa 1.0.21
options snd_hda_intel model=hp-dv5

HPdv6t-1200
option snd-hda-intel model=dell-m4-1

Hp Pavilion Dv6-1108sl
alsa 1.0.20
snd-hda-intel model=dell-m4-3 enable_msi=1
(no headphone/ext mic)

The snd-hda-intel database is here

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

You can find the scripts to upgrade ALSA here:

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by Keronn on 2009-11-12
You can also check this : [http://newyork.ubuntuforums.org/showpost.php?p=8305411&postcount=4](http://newyork.ubuntuforums.org/showpost.php?p=8305411&postcount=4)

---

### Post by Neezer on 2009-11-12
> **markbuntu said:**
> Here are all the options from the snd-hda-intel database that people have reported to work with the DV-6. Some of them require a newer alsa version as noted. 

 
HP dv6 1100.EO
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

HP DV6z
ALSA 1.0.20
options snd-hda-intel model=dell-m4 enable_msi=1

hp dv6-1007tx
alsa 1.0.21
options snd_hda_intel model=hp-dv5

HPdv6t-1200
option snd-hda-intel model=dell-m4-1

Hp Pavilion Dv6-1108sl
alsa 1.0.20
snd-hda-intel model=dell-m4-3 enable_msi=1
(no headphone/ext mic)

The snd-hda-intel database is here

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

You can find the scripts to upgrade ALSA here:

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)



I know it seems strange, but how do I determine which dv6 version I have?

---

### Post by Keronn on 2009-11-12
> **Neezer said:**
> I know it seems strange, but how do I determine which dv6 version I have?

It must be written under your laptop.

---

### Post by Neezer on 2009-11-13
well, I think I have the dv6-1050us. Not really sure where to go from here though.

---

### Post by Ulysses361 on 2009-11-13
Please try the workaround solution from forumuser paoloci at this location:

[http://forum.ubuntu-it.org/index.php?topic=280780.msg2167873](http://forum.ubuntu-it.org/index.php?topic=280780.msg2167873)

---

### Post by Neezer on 2009-11-13
When I try that I get error messages.

```

nathan@lappy:~$ sudo ./hda-verb /dev/snd/hwC0D0 0x1 set_gpio_data 1
[sudo] password for nathan: 
sudo: ./hda-verb: command not found

```

I just copied and pasted his command into a terminal...

---

### Post by Ulysses361 on 2009-11-13
The following link includes the download location for the hda-verb program:

[http://digitizor.com/2009/10/22/fix-headphone-sound-problem-hp-laptop-linux/](http://digitizor.com/2009/10/22/fix-headphone-sound-problem-hp-laptop-linux/)

---

### Post by Neezer on 2009-11-13
sorry to be such a noob, but I have no idea what to do with this once it is downloaded. I extracted it to /home/nathan/hda-verb, but now what??

From reading it looks like a set of commands that I can use to either turn the speakers off or on when I want to use them or my headphones? It is not something that will automatically detect that my headphones are in and shut off the speakers right?

---

### Post by Ulysses361 on 2009-11-13
No, as I wrote before, it is a workaround, not a permanent solution. Still, better than nothing, I guess.

It is not a tool that will automatically run or automatically detect when the headphones are connected.

---

### Post by chrizzler on 2009-12-09
> **Ulysses361 said:**
> Hi,

a) Open a terminal and edit /etc/modprobe.d/alsa-base.conf as follows:

sudo gedit /etc/modprobe.d/alsa-base.conf

Remove the following lines from the /etc/modprobe.d/alsa-base.conf file:

snd_hda_intel: model=hp-dv5
snd_hda_intel: model=hp-dv5
snd-hda-intel: model=hp-m4 enable_msi=1

Add the following 4 lines to the end of the file after "options snd-pcsp index=-2"

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-m4

b) Save change to file /etc/modprobe.d/alsa-base.conf , reboot and retest sound

c) Make sure to increase volume on the Master, Front, PCM and surround channel to 100% 
If 100% sound volume causes distortion, please decrease volume to 77%

Regards,

Mark Rijckenberg

After installing alsa 1.0.21 from a ppa repository, these configuration options did fix the sound for me (HP DV6-2030sd).

Then I noticed that the speakers were still on when I plugged in a headphone. 

>>> This was fixed by selecting the "Analog output" connector in sound preferences on the output tab.

GREAT!

ps. the ppa repository: [http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html](http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html)

---

