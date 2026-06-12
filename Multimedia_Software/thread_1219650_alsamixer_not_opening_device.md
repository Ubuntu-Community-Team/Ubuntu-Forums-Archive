---
title: "alsamixer not opening device"
date: 2009-07-22
forum: Multimedia Software
---

### Post by BeardedLinuxGeek on 2009-07-22
To start, let me say that I did read the Sound Problems Solution thread at the top.

I'm running a headless Ubuntu Server 9.04

Anyways, here is what I have:

**aplay -l**
```

aplay: device_list:217: no soundcards found...

```[B]

lspci -v[/B]
```

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Dell Device 0174
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ee00 [size=256]
        I/O ports at edc0 [size=64]
        Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
        Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

```So ubuntu detects it, that's good.

And I have the modules
**lsmod | grep snd**
```

snd_emu10k1x           23812  0
snd_intel8x0           37532  0
snd_ac97_codec        112292  2 snd_emu10k1x,snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_emu10k1x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
snd_seq_midi           14336  0
snd_rawmidi            29696  2 snd_emu10k1x,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  11 snd_emu10k1x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  3 snd_emu10k1x,snd_intel8x0,snd_pcm

```Also,
**sudo modprobe snd-intel8x0**
Doesn't return any errors

However,
**alsamixer**
```

alsamixer: function snd_ctl_open failed for default: No such device

```and when I try to play a file with
**cvlc *filename.mp3***
```


[00000382] inhibit interface error: Failed to connect to the D-Bus session daemon: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.

[00000382] main interface error: no suitable interface module
[00000001] main libvlc error: interface "inhibit,none" initialization failed
[00000384] main interface error: no interface module matched "screensaver,none"
[00000384] main interface error: no suitable interface module
[00000001] main libvlc error: interface "screensaver,none" initialization failed
[00000387] dummy interface: using the dummy interface module...
ALSA lib confmisc.c:768:(parse_card) cannot find card 'Live'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
[00000467] oss audio output error: cannot open audio device (/dev/dsp)
[00000467] main audio output error: couldn't find a filter for the conversion
[00000467] main audio output error: couldn't create audio output pipeline

```I've just spent several hours on google trying to figure out what is wrong and I just can't get it.

Thanks

EDIT:

 I added
[FONT=monospace]```

options snd-intel8x0 ac97_quirk=3

```to /etc/modprobe.d/alsa-base.conf (the thread leaves out the .conf and that threw me off at first)
[/FONT][FONT=monospace]And now I can open alsamixer. I turned up everything.

[/FONT]**sudo aplay -l**[FONT=monospace]
```

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I'd also like to point out that "sudo aplay -l" lists all of the devices but "aplay -l" says no soundcards found. The thread should be updated to include the sudo
[/FONT]

---

### Post by BeardedLinuxGeek on 2009-07-22
I still can't hear anything.

**cat /proc/asound/cards**
```

 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1980 at irq 17
 1 [Live           ]: EMU10K1X - Dell Sound Blaster Live!
                      Dell Sound Blaster Live! at 0xdf20 irq 17

```

And VLC still gives the error
```


[00000382] main interface error: no suitable interface module
[00000001] main libvlc error: interface "inhibit,none" initialization failed
[00000384] main interface error: no interface module matched "screensaver,none"
[00000384] main interface error: no suitable interface module
[00000001] main libvlc error: interface "screensaver,none" initialization failed
[00000387] dummy interface: using the dummy interface module...
ALSA lib confmisc.c:768:(parse_card) cannot find card 'Live'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
[00000467] oss audio output error: cannot open audio device (/dev/dsp)
[00000467] main audio output error: couldn't find a filter for the conversion
[00000467] main audio output error: couldn't create audio output pipeline

```

---

### Post by igorzwx on 2009-07-22
[B]lsmod | grep oss
[/B]

---

### Post by BeardedLinuxGeek on 2009-07-22
**lsmod | grep oss**
```

snd_pcm_oss            46336  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_emu10k1x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            37760  0
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  11 snd_emu10k1x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

---

### Post by igorzwx on 2009-07-22
This is the answer, perhaps.
They do not like each other.
Martin has already explained this phenomenon here.

---

### Post by martinbaselier on 2009-07-22
> 
Re: alsamixer not opening device
This is the answer, perhaps.
They do not like each other.
Martin has already explained this phenomenon here.


This is something different. "lsmod | grep oss" shows the alsa frontend for oss emulation in this case. Your drivers are ok. By the way most users won't know me and I could also be wrong. It's not that it's true if I say it. 

The last line in your first post shows the probable root of the cause. (no pun intended). Nice post by the way, full of details and showing what you already tested. 

> 
I'd also like to point out that "sudo aplay -l" lists all of the devices but "aplay -l" says no soundcards found. The thread should be updated to include the sudo

This is not normal. Normal users should have the right to use the soundcard. sudo alsamixer will probably work too. I do not know how you managed to do that. 

Just did a quick google search
if you open a terminal and type:
**groups `whoami`**
, it should show the audio group among other things. 
If it doesn't add the user to it.
go to user/groups in your settings) it should show audio under groups, and you can add the user there.

---

### Post by BeardedLinuxGeek on 2009-07-22
Hmm, you're probably right, its most likely something to do with permissions.

I can only open alsamixer with "sudo alsamixer"

I added myself to the audio group, but I still don't have the permissions.
```

colin@torrentfreak:~$ sudo adduser colin audio
Adding user `colin' to group `audio' ...
Adding user colin to group audio
Done.
colin@torrentfreak:~$ groups colin
colin adm dialout cdrom audio plugdev sambashare lpadmin admin
colin@torrentfreak:~$ aplay -l
aplay: device_list:217: no soundcards found...

```

I made sure that the audio group has permission to use the soundcard

**ls -l /dev/dsp***
```

crw-rw---- 1 root audio 14,  3 2009-07-22 01:41 /dev/dsp
crw-rw---- 1 root audio 14, 19 2009-07-22 01:41 /dev/dsp1

```

But check this out

**mpg321 105753_Heaven_remix.mp3**
```

High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
Title  : ~EnV~Heaven Rd. 2 (Ng mix) (ID  Artist: Envy
Album  : Newgrounds Audio Portal - http  Year  :
Comment: This track can be found at: ht  Genre :

Playing MPEG stream from 105753_Heaven_remix.mp3 ...
MPEG 1.0 layer III, 256 kbit/s, 44100 Hz joint-stereo
ALSA lib confmisc.c:768:(parse_card) cannot find card 'Live'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
ALSA snd_pcm_open error: No such device
Can't find a suitable libao driver. (Is device in use?)

```However,

**sudo ****mpg321 105753_Heaven_remix.mp3**
```

High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
Title  : ~EnV~Heaven Rd. 2 (Ng mix) (ID  Artist: Envy
Album  : Newgrounds Audio Portal - http  Year  :
Comment: This track can be found at: ht  Genre :

Playing MPEG stream from 105753_Heaven_remix.mp3 ...
MPEG 1.0 layer III, 256 kbit/s, 44100 Hz joint-stereo
ALSA: underrun, at least 0ms.


```Then the cursor just floats at the bottom as if the program was still running. I'm not at home right now so I can't be sure if any sound is coming out, but it sure does look like the permissions is the problem.

So how I can I get my permissions back?

---

### Post by igorzwx on 2009-07-22
QUOTE:
"I can only open alsamixer with "sudo alsamixer""

I have a question, "Why is it so?"
Was it deliberately designed for a purpose?
Was it because of pulse?

---

### Post by BeardedLinuxGeek on 2009-07-22
I have no idea why its like that.

I just installed Ubuntu Server 9.04 last night.

I set up LAMP, FTP, OpenSSH, and then I was going to setup the audio when I ran into this problem.

---

### Post by igorzwx on 2009-07-22
if you have pulse there, it might not be good for security.
I have already changed to OSS4.
It may work much better on a server, I presume.
You can ask on OSS4 forum.
They know everything (about alsa too).

see wikipedia -> OSS

---

### Post by martinbaselier on 2009-07-22
[http://alsa.opensrc.org/index.php/TroubleShooting](http://alsa.opensrc.org/index.php/TroubleShooting)

There's a section there concerning this problem.

Check if 
ls /dev/snd -al
shows others than root have r/w rights.

---

### Post by BeardedLinuxGeek on 2009-07-22
I went ahead and ran **chmod -R a+rwX /dev/snd**
It doesn't matter if all users have access to the soundcard.

I can now run alsamixer and aplay -l from my normal account.

I can't be sure if sound is coming from the speakers. I get off at work at 6 and I'll post the results when I get home.

By the way, I do appreciate how helpful and patient you guys have been with me. Thank you.

---

### Post by BeardedLinuxGeek on 2009-07-22
I had to do some minor tweaking, something with having both the analog and digital outputs enabled at the same time.

Anyways, it works now!

So thank you all very much.

---

### Post by Hellkid on 2009-09-11
I stumbled across this thread because I wanted to post about the same issue. A couple weeks back I was trying to get sound working and nothing was working until I found on some other forum a posting about the permissions on the files in the /dev/snd/ directory. Modifying the permissions then made everything work as you found too.

HOWEVER - whenever the server is rebooted, all the permissions are reset and I have to chmod them again to get the sound working. Do you guys have the same issue? Is there anyway to have the changed permissions persist if the server is rebooted?

---

