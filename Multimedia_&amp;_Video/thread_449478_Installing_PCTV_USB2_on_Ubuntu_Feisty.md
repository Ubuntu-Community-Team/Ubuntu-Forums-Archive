---
title: "Installing PCTV USB2 on Ubuntu Feisty"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by Bodifar on 2007-05-20
Hey all!

First off, I'm a n00b in Ubuntu Linux. Yes, a newbie, but with two big zero's in the middle. So please bear with me if I'm asking stupid questions :-)

Second, I'm trying to install my Pinnacle PCTV USB2 on Ubuntu Feisty. I searched the internet, and found some very good tutorials on how to do it ( [http://ubuntuforums.org/showthread.php?p=1137844](http://ubuntuforums.org/showthread.php?p=1137844) ) - unfortunately, they were all for Ubuntu 5.10, and that's exactly my problem. 

See, the kernel has changed since then (duh), but the video4linux drivers are older than the changes to the Linux kernel. Trouble ahead!

My first error was this: 

```
/home/gerre/v4l-dvb/v4l/v4l1-compat.c:20:26: error: linux/config.h: No such file or directory
```

I could work around it by creating a symbolic link in my linux-header folder to the autoconf.h file. I thought: hey, my problems are solved! 

*Puuuuut*

Not!

Next error: 

```
/home/gerre/v4l-dvb/v4l/videodev.c:29:35: error: linux/devfs_fs_kernel.h: No such file or directory
/home/gerre/v4l-dvb/v4l/videodev.c: In function 'video_open':
/home/gerre/v4l-dvb/v4l/videodev.c:130: warning: assignment discards qualifiers from pointer target type
/home/gerre/v4l-dvb/v4l/videodev.c: In function 'video_register_device':
/home/gerre/v4l-dvb/v4l/videodev.c:343: warning: implicit declaration of function 'devfs_mk_cdev'
/home/gerre/v4l-dvb/v4l/videodev.c: In function 'video_unregister_device':
/home/gerre/v4l-dvb/v4l/videodev.c:388: warning: implicit declaration of function 'devfs_remove'
```

Do any of you have any thoughts on how to work around this problem?

Thanks!

---

### Post by Bodifar on 2007-05-25
*bump*

Doesn't anybody know what to do about the devfs_fs_kernel.h error?

---

### Post by korna on 2007-06-02
I got the Pinnacle PCTV USB2 working on Feisty. Getting the image was not difficult, the sound is a different story..

I installed tvtime and I checked in synaptic if video4linux was installed (libpt-plugins-4vl and libpt-plugins-4vl2). After starting tvtime you probably need to search for channels, I disabled signal detection under channel management and used my scrollwheel to manualy search for channels. Finding channels was not a problem at all, only the audio didn't work.

I tried the following from an earlier guide for ubuntu 5.10 [(http://ubuntuforums.org/showthread.php?t=166605&highlight=pctv+usb2)]("http://ubuntuforums.org/showthread.php?t=166605&highlight=pctv+usb2").

```

sudo gedit /etc/modprobe.d/pctv
insert line: options snd-usb-audio enable=1 index=1 nrpacks=10

Run in console:
sox -r 44100 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp&tvtime --mixer=/dev/mixer:vol&

```

Unfortunaley again I saw everything but heard nothing..

I replaced dsp1 with dsp2 after a tip at the V4LWiki [(http://www.linuxtv.org/v4lwiki/index.php/Talk:Em2820#PCTV_USB2)]("http://www.linuxtv.org/v4lwiki/index.php/Talk:Em2820#PCTV_USB2") and it works!

```

sox -r 44100 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp&tvtime --mixer=/dev/mixer:vol&

```

At the V4Lwiki a number of different options are used with sox (setting sample rate 48000 instead of 41000 and 2 audio channels instead of 1). I still got to find out what kind of output the PCTV USB2 actually supports.

---

### Post by korna on 2007-06-02
Maybe someone could help me with the following .. the audio is delayed! There is a clear delay between the picture and the audio. Someone got a solution?

---

### Post by Bodifar on 2007-06-09
Well, I did check if I had the v4l-libraries, and I did ... However, TVTime cannot find my device :-( Your commands did not work, and it's not located at /dev/video0 either ... 

Is there a way to show which devices are located where? I used the "mount" command, but I cannot make out which device is my PCTV ...

---

### Post by korna on 2007-06-10
Unfortunately I am not at the right computer at the moment, so I can't help you. I think i do remember that neither my device is on video0 ! But tvtime picked that up automatically, when im back at the other pc ill have a look.

---

### Post by karhulitos on 2007-06-20
I have Pinnacle PCTV USB Stick (eb1a:2870, Zarlink ZL10353 DVB-T).

I have installed it using [http://www.marcushellberg.com/pages/projects/digital-tv-in-linux.php]("http://www.marcushellberg.com/pages/projects/digital-tv-in-linux.php")

All appears to be OK, my dmesg looks like this after inserting the stick:
```

[ 5454.320000] usb 3-1: USB disconnect, address 2
[ 5454.320000] em28xx-input.c: remote control handler detached
[ 5457.008000] usb 3-1: new high speed USB device using ehci_hcd and address 3
[ 5457.140000] usb 3-1: configuration #1 chosen from 1 choice
[ 5457.140000] em28xx new video device (eb1a:2870): interface 0, class 255
[ 5457.140000] em28xx: device is attached to a USB 2.0 bus
[ 5457.140000] em28xx: you're using the experimental/unstable tree from mcentral.de
[ 5457.140000] em28xx: there's also a stable tree available but which is limited to
[ 5457.140000] em28xx: linux <=2.6.19.2
[ 5457.140000] em28xx: it's fine to use this driver but keep in mind that it will move
[ 5457.140000] em28xx: to http://mcentral.de/hg/~mrec/v4l-dvb-kernel as soon as it's
[ 5457.140000] em28xx: proved to be stable
[ 5457.140000] em28xx #0: Alternate settings: 8
[ 5457.140000] em28xx #0: Alternate setting 0, max size= 0
[ 5457.140000] em28xx #0: Alternate setting 1, max size= 0
[ 5457.140000] em28xx #0: Alternate setting 2, max size= 1448
[ 5457.140000] em28xx #0: Alternate setting 3, max size= 2048
[ 5457.140000] em28xx #0: Alternate setting 4, max size= 2304
[ 5457.140000] em28xx #0: Alternate setting 5, max size= 2580
[ 5457.140000] em28xx #0: Alternate setting 6, max size= 2892
[ 5457.140000] em28xx #0: Alternate setting 7, max size= 3072
[ 5457.528000] input: em2880/em2870 remote control as /class/input/input8
[ 5457.528000] em28xx-input.c: remote control handler attached
[ 5457.528000] attach_inform: eeprom detected.
[ 5457.556000] em28xx #0: i2c eeprom 00: 1a eb 67 95 1a eb 70 28 c0 12 81 00 6a 22 00 00
[ 5457.556000] em28xx #0: i2c eeprom 10: 00 00 04 57 02 0d 00 00 00 00 00 00 00 00 00 00
[ 5457.556000] em28xx #0: i2c eeprom 20: 44 00 00 00 f0 10 02 00 00 00 00 00 5b 00 00 00
[ 5457.556000] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 79 7a e6 46
[ 5457.556000] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 5457.556000] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 5457.556000] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 22 03 55 00 53 00
[ 5457.556000] em28xx #0: i2c eeprom 70: 42 00 20 00 32 00 38 00 37 00 30 00 20 00 44 00
[ 5457.556000] em28xx #0: i2c eeprom 80: 65 00 76 00 69 00 63 00 65 00 00 00 00 00 00 00
[ 5457.556000] em28xx #0: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 5457.556000] em28xx #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 5457.556000] em28xx #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 5457.556000] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 5457.556000] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 5457.556000] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 5457.556000] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 5457.556000] EEPROM ID= 0x9567eb1a
[ 5457.556000] Vendor/Product ID= eb1a:2870
[ 5457.556000] No audio on board.
[ 5457.556000] 500mA max power
[ 5457.556000] Table at 0x04, strings=0x226a, 0x0000, 0x0000
[ 5457.560000] tuner 1-0060: Chip ID is not zero. It is not a TEA5767
[ 5457.560000] tuner 1-0060: chip found @ 0xc0 (em28xx #0)
[ 5457.560000] attach inform (default): detected I2C address c0
[ 5457.560000] /tmp/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[ 5457.560000] /tmp/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[ 5457.564000] tuner 1-0060: Tuner has no way to set tv freq
[ 5457.564000] em2880-dvb.c: DVB Init
[ 5457.568000] MT2060: successfully identified (IF1 = 1220)
[ 5458.040000] DVB: registering new adapter (em2880 DVB-T)
[ 5458.040000] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
[ 5458.040000] em28xx #0: Found Pinnacle PCTV DVB-T

```

But when I'm supposed to scan, neither Kaffeine nor dvb-utils scan gives me joy.

Kaffeine:
```

Not able to lock to the signal on the given frequency
Frontend closed
dvbsi: Cant tune DVB
Using DVB device 0:0 "Zarlink ZL10353 DVB-T"
tuning DVB-T to 674000000 Hz
inv:2 bw:0 fecH:2 fecL:9 mod:3 tm:1 gi:2 hier:0
...............
Not able to lock to the signal on the given frequency
Frontend closed
dvbsi: Cant tune DVB
Transponders: 3
dvbsi: The end :)
Channels found: 0

```

dvbutils:
```

# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/fi-Espoo > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/fi-Espoo
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 562000000 0 2 9 3 1 2 0
initial transponder 658000000 0 2 9 3 1 2 0
initial transponder 674000000 0 2 9 3 1 2 0
>>> tune to: 562000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 562000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 658000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 658000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 674000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 674000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

Pinnacle PCTV DVB-T should be supported as what I've understood. Some say they got it rolling and  [some say]("http://www.mail-archive.com/em28xx@mcentral.de/msg00122.html") they couldn't.

Anyone with deeper knowledge could help me out? I just can't find any info to progress with this.. :(

---

### Post by korna on 2007-06-21
Ill see if this tutorial will improve in anyway my audiosync problem. (guess not)

I could scan using tvtime but it could not find all channels, you can insert a manual channel list but even then some channels could not be received.

---

### Post by karhulitos on 2007-06-21
I brought the stick to work where I have one clean Feisty laptop, did all same steps as at home and for my surpise I could scan & watch DVB.

I'm starting to suspect that I get too much signal from my house's central aerial and too low with bundled antenna.
Here at work (closer to transmitter than home) I can list all channels with the bundled aerial.

Or my home computer (Edgy -> Feisty upgrade) is having some sort of problems.

And, just checked, yes there seems to be some sync probs with sound but not too bad

---

### Post by karhulitos on 2007-06-25
Came back to confirm that my home communal aerial gives too much signal for Pinnacle PVTV USB Stick. With dedicated aerial it tuned ok and shows TV.

---

### Post by Bodifar on 2007-08-19
*bump*

Just wondering if anyone has a solution for this problem yet. Mind you: it's NOT, I repeat, NOT the USB-stick - the USB2 is something different. 

And it still doesn't work ... :-(

---

### Post by sharris203 on 2008-04-28
> **korna said:**
> Maybe someone could help me with the following .. the audio is delayed! There is a clear delay between the picture and the audio. Someone got a solution?

Below is the code i use. If I just run the command, the audio is a bit delayed BUT when i put it in a script file (linked to a button for easy access) and execute it, it works PERFECT. I hope it helps.

```

#!/bin/bash
  sox -q -c 2 -s -w -r 48000 -v 1 -t ossdsp /dev/dsp1 -t ossdsp -w -r 48000 /dev/dsp
```

---

### Post by anandbabu20 on 2008-07-06
Hi all, 

I have Pinnacle PCTV USB2 (not stick) -- Analog device. 

I went easily thru the installation of v4l with mercurial, set up the drivers.. everything looked fine, created the video0 and vbi0 devices. 

TV time did not complain anything....

But I don't get any signal from my cable... 

Could this be a problem with tuner. Do I need to specify the tuner or something like that?

I don't know where to start. I use hardy fresh install.

Please give some hint..

Thanks a lot!

---

### Post by anandbabu20 on 2008-07-07
:)Got it to work finally.

Picture perfect. Sound not.

tried the

> sox -q -c 2 -s -w -r 48000 -v 1 -t ossdsp /dev/dsp1 -t ossdsp -w -r 48000 /dev/dsp

emitted the following error:

```
$ sox -q -c 2 -s -w -r 48000 -v 1 -t ossdsp /dev/dsp1 -t ossdsp -w -r 48000 /dev/dsp
sox soxio: Failed reading `/dev/dsp1': unknown file type `ossdsp'

```

Need help.... 

:sad:

Thanks again...

---

### Post by anandbabu20 on 2008-07-07
Oh! found the answer.

Stupid me did not do enough search!

[http://ubuntuforums.org/showthread.php?t=740612](http://ubuntuforums.org/showthread.php?t=740612)

It was there!

Any thanks for all, let me watch some programmes now!

---

