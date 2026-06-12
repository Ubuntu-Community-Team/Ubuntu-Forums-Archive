---
title: "SoundMAX (82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97)"
date: 2005-12-27
forum: Multimedia &amp; Video
---

### Post by gray380 on 2005-12-27
Hi all,

as usual trouble with sound.

I had fresh-installed Ubuntu 5.10. The system recognized my audio-card like:

$ lspci | grep -i multimedia
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

In the M$WinXP it seems like SoundMAX.

When I move a volume-jack the system reacts (some picture has appeared on the screen). But I can't hear any sound (in the offtopic with sound everything is ok).
The solution described at 

[http://ubuntuforums.org/archive/index.php/t-32063.html](http://ubuntuforums.org/archive/index.php/t-32063.html)

does not help me.

Everything is unmuted.

Any suggestions?

Additional information:

**$ cat /proc/asound/version**
Advanced Linux Sound Architecture Driver Version 1.0.9 (Sun May 29 07:31:02 2005 UTC).

**$ cat /proc/asound/oss/sndstat**
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux Cherpatyuk 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Intel 82801DB-ICH4 with AD1981B at 0xd0100c00, irq 10

Audio devices:
0: Intel 82801DB-ICH4 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Analog Devices AD1981B

**$ lsmod |grep snd**
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

**$ modinfo soundcore**
filename:       /lib/modules/2.6.12-9-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.12-9-386 386 gcc-3.4
depends:
srcversion:     E11490DC3F523551C4C2A6D

**$ modinfo snd_intel8x0**
filename:       /lib/modules/2.6.12-9-386/kernel/sound/pci/snd-intel8x0.ko
author:         Jaroslav Kysela <perex@suse.cz>
description:    Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7012; Ali 5455
license:        GPL
vermagic:       2.6.12-9-386 386 gcc-3.4
depends:        snd-ac97-codec,snd-pcm,snd-page-alloc,snd
alias:          pci:v00008086d00002415sv*sd*bc*sc*i*
alias:          pci:v00008086d00002425sv*sd*bc*sc*i*
alias:          pci:v00008086d00002445sv*sd*bc*sc*i*
alias:          pci:v00008086d00002485sv*sd*bc*sc*i*
alias:          pci:v00008086d000024C5sv*sd*bc*sc*i*
alias:          pci:v00008086d000024D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000025A6sv*sd*bc*sc*i*
alias:          pci:v00008086d0000266Esv*sd*bc*sc*i*
alias:          pci:v00008086d000027DEsv*sd*bc*sc*i*
alias:          pci:v00008086d00002698sv*sd*bc*sc*i*
alias:          pci:v00008086d00007195sv*sd*bc*sc*i*
alias:          pci:v00001039d00007012sv*sd*bc*sc*i*
alias:          pci:v000010DEd000001B1sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000003Asv*sd*bc*sc*i*
alias:          pci:v000010DEd0000006Asv*sd*bc*sc*i*
alias:          pci:v000010DEd00000059sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000008Asv*sd*bc*sc*i*
alias:          pci:v000010DEd000000DAsv*sd*bc*sc*i*
alias:          pci:v000010DEd000000EAsv*sd*bc*sc*i*
alias:          pci:v00001022d0000746Dsv*sd*bc*sc*i*
alias:          pci:v00001022d00007445sv*sd*bc*sc*i*
alias:          pci:v000010B9d00005455sv*sd*bc*sc*i*
srcversion:     BE1F3A44BD71061F26545D6
parm:           xbox:Set to 1 for Xbox, if you have problems with the AC'97 codec detection. (array of bool)
parm:           buggy_irq:Enable workaround for buggy interrupts on some motherboards. (array of bool)
parm:           ac97_quirk:AC'97 workaround for strange hardware. (array of charp)
parm:           ac97_clock:AC'97 codec clock (0 = auto-detect). (array of int)
parm:           enable:Enable Intel i8x0 soundcard. (array of bool)
parm:           id:ID string for Intel i8x0 soundcard. (array of charp)
parm:           index:Index value for Intel i8x0 soundcard. (array of int)

I tried even the following:
$ sudo /etc/init.d/alsa-utils stop
$ sudo /etc/init.d/alsa force-unload
$ sudo modprobe i810_audio

No sound ;(



Best regards,
Serhiy.

PS sorry for my mad-bad english

---

### Post by barfos on 2005-12-30
I ran all those commands on my dell inspiron 8500, and i get all the same results!  Except that in winxp, it called my sound card 'sigmatel audio.'  I am able to play sounds, but often only one app can play sound at a given time.  Also midi doesn't work at all unless i used timidity at the command line.  So I'm in the same boat as you, almost.  

Another difference between us is that we might have installed different packages from the package manager.  I've got these sound related things installed

linux-sound-base
alsa-base
alsa-utils
alsa-oss

libsdl1.2debian-alsa
libasound2
libao2
libopenal0

libesd-alsa0
gstreamer0.8-oss
gstreamer0.8-esd
timidity

I dont know if any of this stuff is unnecessary or actually messing me up.  See if installing some of these packages gets your sound working.

Another thing I found while trying to get sound to fully work is this file /etc/asound.conf which for me currently contains this.

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1024
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

When I change the period_size and buffer_size, this has an effect on my visualboyadvance emulation sound (but i can't get it right no matter what the numbers are), and on the sound test in system->preferences->multimedia system selector.  Currently I have both source and sink set to alsa there.  

Also see if your applications have sound configuration, like in xmms you can choose between oss and alsa.  Try everything!

Theres probably a million other methods of configuration that I dont know about yet.  

anyone who knows a lot about sound, please help!

barfos

---

### Post by gray380 on 2006-01-03
Hi,

seems that I have found the solution:

[https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html](https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html)

yes, on the rh.

brg,
Serhiy.

---

