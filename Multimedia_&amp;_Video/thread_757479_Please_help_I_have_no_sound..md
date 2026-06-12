---
title: "Please help: I have no sound."
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by Th3Professor on 2008-04-17
My laptop's sound was working fine until just a couple days ago. I don't recall doing anything that would give the computer's sound reason to just stop.

It seems like this is the best place to ask this (a while back I asked in another forum but unfortunately I didn't receive any effective help there).

I checked the sound control, currently using ALSA Mixer, Intel 82801DB-ICH4.
No luck so far.

I tested things in Sound Preferences (System>Preferences>Sound).
No luck so far.

I clicked on the nice little "?" button for the general help, tried searching for topics to help me troubleshoot the no audio.
No luck so far.

Here's the output of aplay -l and aplay -L:
```

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```

default:CARD=I82801DBICH4
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Default Audio Device
front:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Front speakers
surround40:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    4.0 Surround output to Front and Rear speakers
surround41:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

```

I'm using Ubuntu Studio on a Dell Inspiron 8500 laptop/notebook.
For everyday use, I actually do not use the realtime kernel, only when I use the more hefty audio applications. For general use, I use the generic kernel.

Here's my uname -a:
```

Linux computer 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

```

I am definitely not a professional computer user, though I am a professional musician, and my computing seems void of purpose without sound.

Please help.


EDIT:
I am going through the thread entitled "Comprehensive Sound Problem Solutions Guide", though I still welcome any help. Thank you.

EDIT 2:
I'm following the given steps on the thread (mentioned above), though am stuck at one point:
ALSA soundcard driver. I'm not sure if I have snd-intel8x0 or snd-intel8x0m (or neither).
My /etc/modules reads:
fuse
lp
spb2

In alsamixer, PCM Out is set to pre-3D (not post-3D).
There is also something in alsamixer called "IEC958" (and playback).
alsamixer says that I have this:
Card: Intel 82801DB-ICH4
Chip: SigmaTel STAC9750,51 (does SigmaTel mean I should use a different driver in the "/etc/modules" file? I cannot find the driver on ALSA's site if that's the case.)

EDIT 3:
The "Volume Control" lists (in "file>change device...") the following:
Intel 82801DB-ICH4 (Alsa mixer)
SigmaTel STAC9750,51 (OSS Mixer)

I try both of them out, adjusting volume settings, and still hear nothing.

(I'm testing with a couple different audio files via "ffplay", same files and a couple different video files in "totem".)

EDIT 4:
My speakers are physically working. I boot into another operating system and sound works perfect. (I do not "mute" the speakers before switching back from the other OS to Ubuntu Studio.)

EDIT 5:
Another "edit", lol. I thought I'd go ahead and share my lspci -v, anything with the intel "82801", "audio", or sigmatel - some of includes USB stuff but I'll put it in just in case:
```

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)
USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Latitude D400
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf80 [size=32]
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)
USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Latitude D400
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf40 [size=32]
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)
USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Latitude D400
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf20 [size=32]
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M)
USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 013e
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
(prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: f6000000-fbffffff
        Prefetchable memory behind bridge: 30000000-33ffffff
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
(prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corporation Latitude D400
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at bfa0 [size=16]
        Memory at 34000000 (32-bit, non-prefetchable) [size=1K]
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)
AC'97 Audio Controller (rev 03)
        Subsystem: Dell Unknown device 013e
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at b800 [size=256]
        I/O ports at bc40 [size=64]
        Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```

EDIT (again)...

Okay, I did a sudo lspci -v and here's the audio controller info without the "<access denied>" bit:
```

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Unknown device 013e
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at b800 [size=256]
        I/O ports at bc40 [size=64]
        Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

```
(I found nothing related to SigmaTel.)

The computer has locked up on me a few times and I've had to forcibly shut it down. I have not done "fsck" afterwards, and it doesn't appear to automatically do that after a cold shutdown (without unmounting anything). I'm a bit scared to do a fsck, the last time I did that my entire computer's hard drive somehow ended up completely messed up. (I had to go into it with help from a friend, to retrieve my email (from a "raw data" search through the drive and back it up onto a flashdrive before reinstalling Ubuntu.) So, I'm certainly scared to do a fsck now, unless there's a certain way to do it safely without all of the data somehow getting offset or whatever happened last time. Though, I don't know if that has anything to do with my audio but wanted to mention it.

Also, lately I seem to have been having problems with the icons on my desktop and general file browser usage. Either not working (not letting me click on them) or having great delays before finally doing something, or in some cases icons on the desktop not even loading. That's another non-audio concern but I wanted to mention it just in case it might have something to do with the audio - on a grand scheme of things type of level.

---

### Post by xc3RnbFO8P on 2008-04-17
I found this:
[http://www.rubin-de-celis.com/blog/category/linux/fc5-on-toshiba-m30/]("http://www.rubin-de-celis.com/blog/category/linux/fc5-on-toshiba-m30/")

```
Problems with Alsa
September 20th, 2006 by September 20th, 2006 by JCR

Since the last update (via yum), the sound faded for some applications (Xine, Amarok, rhythmbox), but not for others that allow configuration of the device (such as XMMS). 

Of course all were with ALSA (1.0.11) by default.

 For now, switching to OSS solve the problem, but it is still unknown why these programs do not seem to want to work with ALSA.

 Update: After reviewing the configuration, the problem is that the form of alsa was configured incorrectly.  Even I do not know what changed this application.

The solution:

# vim /etc/asound.conf
pcm.!default { type hw card 0 device 0 }
ctl.!default { type hw card 0 }

Update 2: The previous solution worked only until I got switched off and turn on the computer. For this reason I looked a more permanent solution:

 $ cat /proc/asound/cards
0 [I82801DBICH4 ]: ICH4 - Intel 82801DB-ICH4 Intel
82801DB-ICH4 with STAC9750,51 at 0xc0000c00, irq 4
1 [Modem ]: ICH-MODEM - Intel 82801DB-ICH4 Modem
Intel 82801DB-ICH4 Modem at 0x2400, irq 4

$ vim .asoundrc
!defaults.pcm.card I82801DBICH4
defaults.ctl.card I82801DBICH4

The. Asoundrc takes precedence over asound.conf.

I am grateful for the help of people in the IRC channel # alsa.
```

---

### Post by Th3Professor on 2008-04-17
Thank you for that. Hopefully it's a lead in the right direction, it hasn't worked yet though I haven't found any asound.conf on the system.
There's asound in /proc
There's /var/lib/alsa/asound.state
...ah wait... there's /usr/bin/asoundconf

On the command "asoundconf list" I get:
```
Names of available sound cards:
I82801DBICH4
```

I tried "asoundconf is-active" but on testing audio/video files, still no sound.

Same thing happened with "asoundconf reset-default-card".

The manpage on "asoundconf" shows that the config files are in my ~ directory.

However, there is no ~/.asoundrc nor is there ~/.asoundrc.asoundconf

---

### Post by nstamoul on 2008-04-17
Gutsy or Hardy?

If you are on hardy you might want to check your pulseaudio settings.

If you are on gutsy me sure that you havent muted anything by mistake.Anyway give alsamixer a go and unmute everything.
Last thing you might want to check is that you havent ticked on any switches you shouldnt have (digital output etc.).

Good luck and feel free to report back :)

---

### Post by Th3Professor on 2008-04-17
> **nstamoul said:**
> Gutsy or Hardy?

If you are on hardy you might want to check your pulseaudio settings.

If you are on gutsy me sure that you havent muted anything by mistake.Anyway give alsamixer a go and unmute everything.
Last thing you might want to check is that you havent ticked on any switches you shouldnt have (digital output etc.).

Good luck and feel free to report back :)


OMG! I have sound!

I umuted everything.

This is odd still:

I *had* unmuted everything before, and still had no sound.

Weird. Oh well, I'm just glad to have sound now.

And simple as unmuting it. jeesh. ;)

---

