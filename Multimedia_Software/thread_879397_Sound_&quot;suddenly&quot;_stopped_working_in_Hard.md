---
title: "Sound &quot;suddenly&quot; stopped working in Hardy Heron"
date: 2008-08-04
forum: Multimedia Software
---

### Post by Hackmo on 2008-08-04
My sound worked fine when I first installed Heron a few days ago although I could only play from one source at a time(firefox, audacious etc) but now my sound has stopped completely.  It happened a few days ago although it seemed to sort itself out then with a reboot.  The problem has happened again however and this time three reboots, a proper "shut down" and me messing around with the sound settings wont fix it.

I tried changing the output plugin in Audacious from alsa to every other one that I could choose and none of them worked, some of them even made Audacious freeze.  (I changed from pulseaudio to alsa when I first installed Audacious)

I've checked in System > Preferences > Sound and Alsa is picked under sound capture but everything else is set to "Autodetect" and when I try to change them to Alsa I get the error:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback. Device is being used by another application
```

I've checked alsamixer and nothing is muted.

This is my lspci:
```
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
02:01.0 Ethernet controller: Intel Corporation 82547GI Gigabit Ethernet Controller
03:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:03.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
03:05.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

this is lsmod | grep snd

```
snd_ca0106             36192  1 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_intel8x0           35356  4 
snd_ac97_codec        101028  2 snd_ca0106,snd_intel8x0
snd_pcm                78596  5 snd_ca0106,snd_pcm_oss,snd_intel8x0,snd_ac97_codec
ac97_bus                3072  1 snd_ac97_codec
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  21 snd_ca0106,snd_pcm_oss,snd_mixer_oss,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_ca0106,snd_intel8x0,snd_pcm

```

this is aplay

```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
aplay: main:546: audio open error: Device or resource busy

```

Anyone got any ideas?

---

### Post by rdn2fst on 2008-08-04
I think I may have a similar or like problem with my sound.  ...Do you happen to have Virtualbox installed?  I do, and I use it daily.  from a windows VM my sound works but not from my hardy heron host.

I've had this problem twice now but the last time I just rebuilt my system because I had other issues.  It seems this sort of thing happens after I update hardy.

---

### Post by rdn2fst on 2008-08-04
ah, had to change the dropdown on System -> prefs -> sound from autodetec to "STAC92xx Analog".  I made this cahnge on the "sound events" and "music and movies" settings.

So, maybe your system is having trouble with autodetect too?

---

### Post by Hackmo on 2008-08-09
Ok, my sound sorted itself out again but alas now it has stopped working.  Reboots and shutdowns don't help...it doesn't seem to be coming back.


Now I know things like this don't happen without a reason and by the seemingly "random" times my sound does stop working it would seem like it's something i'm doing that is causing it to stop working.

here is the programs I have set up to start when the computer boots:

Xchat
Firefox
Pidgin

All updated to the latest versions that are in the repositories.

rdn2fst: i've tried changing from autodetect to intel but I just get the same error as I do with autodetect.  Thanks for the suggestion though.

---

### Post by fitzhugh on 2008-08-25
Any luck?

I'm encountering similar problems. I get the same error:

EDIT: Note that the emoticon in next line is supposed to be equivalent text - I'm leaving it as typed so it will match others' searches, though it displays wrong - at least it isn't a smiley, that would be rubbing salt in the wound...

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
aplay: main:546: audio open error: Device or resource busy

I'm unclear how it started, but in my case it was because I was tweaking around. This error is what I get at this point, and seems the most diagnostic bit of info (out of lots of stuff I'm not making heads or tails out of).

Any hints would be great!

---

### Post by tomcec on 2008-09-22
> **fitzhugh said:**
> Any luck?

I'm encountering similar problems. I get the same error:

EDIT: Note that the emoticon in next line is supposed to be equivalent text - I'm leaving it as typed so it will match others' searches, though it displays wrong - at least it isn't a smiley, that would be rubbing salt in the wound...

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
aplay: main:546: audio open error: Device or resource busy

I'm unclear how it started, but in my case it was because I was tweaking around. This error is what I get at this point, and seems the most diagnostic bit of info (out of lots of stuff I'm not making heads or tails out of).

Any hints would be great!

Ok, I had the same problem:
root@pc-cecchi:~# aplay -vv /usr/share/skype/sounds/CallRingingIn.wav
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
aplay: main:546: audio open error: Device or resource busy

With:
root@pc-cecchi:~# strace aplay -vv /usr/share/skype/sounds/CallRingingIn.wav 2>gino.oo

I found this interesting line:
open("/dev/snd/pcmC0D0p", O_RDWR|O_NONBLOCK) = -1 EBUSY (Device or resource busy)

and I found who was keeping busy that device file with:
root@pc-cecchi:~# lsof /dev|grep snd
pulseaudi 15534       act0  mem    CHR 116,16       12718 /dev/snd/pcmC0D0p
pulseaudi 15534       act0   17w   CHR  116,0       12754 /dev/snd/controlC0
pulseaudi 15534       act0   24u   CHR  116,0       12754 /dev/snd/controlC0
pulseaudi 15534       act0   39u   CHR  116,0       12754 /dev/snd/controlC0
pulseaudi 15534       act0   40u   CHR 116,16       12718 /dev/snd/pcmC0D0p
mixer_app 15716       act0   20r   CHR  116,0       12754 /dev/snd/controlC0

The way I solved has been to kill pulseaudio process and restart X server. This have restarted pulseaudio (which, by the way, is not started by /etc/init.d/pulseaudio script). I don't know if there was a smarter way to restart pulseaudio though.

After that I saw that pulseaudio was not keeping open /dev/snd/pcmC0D0p anymore:
root@pc-cecchi:~# lsof /dev|grep snd
pulseaudi 15534       act0   17w   CHR  116,0       12754 /dev/snd/controlC0
pulseaudi 15534       act0   24u   CHR  116,0       12754 /dev/snd/controlC0
mixer_app 15716       act0   20r   CHR  116,0       12754 /dev/snd/controlC0

and I saw that aplay command reported before was working great.
I also saw that pulseaudio opens pcm* file when opening the sound preferences (System -> Preferences -> Sound) and testing some sounds event (Login/Logout are enabled by Default on 8.10) and then pulseaudio closes the pcm* files.
My guess is that for some strange reason when I tested the Login event wav file (because I tested before sound stopped to work) the pulseaudio did not close properly (or not at all) the pcm* file which resulted busy for other applications.

Regards,
Tommaso

---

### Post by markbuntu on 2008-09-23
If you want to get all your sound applications to work together, you can read my guide:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by eye208 on 2008-09-23
Try this guide if you use applications not covered by the other guide:

[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

