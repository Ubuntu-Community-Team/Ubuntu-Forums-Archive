---
title: "Problems with USB External Sound Card"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by alphanimal on 2007-08-13
Hi people!

I run Ubuntu 7.04 (feisty) on my Sony Vaio VGN-A115S

I have some issues with Sound:
I have 2 sound cards attached:
[LIST]
[*] internal sound chip (laptop speakers and headphone output)
[*] an external USB 5.1 surround sound card from Trust (Item.No. 14134)
[/LIST]
Both devices are recognized - looking into /proc/asound/cards gives the following:

```
 0 [Audio          ]: USB-Audio - USB Audio
                      USB Audio at usb-0000:00:1d.0-1, full speed
 1 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with ALC203 at 0xff7ff800, irq 9
```

When I go to "System -> Preferences -> Audio" I can select a device for each application (events, music/video, audio conference ...). I can choose from the following devices:
[LIST]
[*] Detect automatically
[*] Intel 82801DB-ICH4 - IEC958
[*] Intel 82801DB-ICH4
[*] USB Audio
[*] ALSA - Advances Linux Sound Architecture
[*] ESD - Enlightened Sound Daemon
[*] OSS - Open Sound System
[/LIST]
Next to each Select box is a "Test" button. Pressing the button plays a beep sound on the selected device.
I always hear the sound coming from my internal speakers except:
- on OSS it's coming from my USB Sound Card with 5.1 Speakers attached (sound from all 5 speakers)
- on "82801DB-ICH4 - IEC958" i don't hear anything
even when i have "USB Audio" selected, The test sound is played on my internal speakers!

So something is not as it is supposed to be right?

Okay, so OSS is the only choice I have if I want my 5.1 Speakers to work.
But firstly there's only Mono sound (which is a bit boring in comparison to 5.1; sound comes only from the front left speaker)
I tried this in VLC and XMMS with the same result. Both, VLC and XMMS, have Output modules for ALSA and OSS. Here it's the same as with the "Test" button in Audio Prefs: ALSA uses internal speakers, OSS my USB device (mono, though the Test button played all 5 channels)
Secondly I cannot play sound with more than one App at a time. When music is playing in XMMS the Test button in Audio Prefs tells my that the device is busy, and VLC simply switches to the internal speakers. It is the same otherwise: When i watch Video in VLC (over 5.1) and want to play music in XMMS, it tells me to check if my sound device is properly configured and not used by an other application.

It is exactly the same thing with my internal speakers! When i select the ALSA device in XMMS and try to do a Test sound in Audio Prefs it tells me that device is busy!

I do not hear system events (like from Gaim) or any other sound except from that app that currently owns the device.

So I wrote a lot about my problem and hope somebody can help me.
I have already tried the solution in this Thread:
[External USB sound card and ALSA]("http://ubuntuforums.org/showthread.php?t=402293")
But that did just disable my internal Sound Card, and the USB Device was still busy and couldn't be used by multiple Apps.

I searched the Forum twice, played around with different settings a lot (and I mean a lot!), asked in the IRC #ubuntu und #ubuntu-de. No solution in sight!

Ubuntu is really great and I have switched from Windows to Linux and I don't want to fall back to MS because if this :)

ps: maybe some words are a bit different because i translated from my German system.

---

### Post by alphanimal on 2007-08-13
Alright then... I played around again and disabled my internal device by adding an entry to /etc/modprobe.d/blacklist:
blacklist snd_intel8x0

So my internal sound card is no longer recognized.
Now, in my Audio prefs i can choose out of the following devices:
[LIST]
[*]Detect automatically
[*] USB Audio
[*] ALSA - Advances Linux Audio Architecture
[*] ESD - Enlightened Sound Daemon
[*] OSS - Open Sound System
[/LIST]

A test on each of them except OSS fails because the device is busy.
So my guess: OSS is blocking my USB Sound Card!

When I set up XMSS to use OSS it plays music over my USB Sound Card.
If I try a Test sound with OSS it tells me again that the device is busy!

Is there a way to disable OSS from stealing my device so I can try it with ALSA?

---

### Post by alphanimal on 2007-08-13
Okay I got updates again. Played around a bit and now the Test sound works for ALSA but not for OSS.

I started VLC by bash and got the following output:

```
VLC media player 0.8.6 Janus

** (.:6287): CRITICAL **: glide_draw_box: assertion `height >= -1' failed
[00000336] oss audio output error: cannot open audio device (/dev/dsp)
[00000336] main audio output error: couldn't find a filter for the conversion
[00000336] main audio output error: couldn't create audio output pipeline
signal 2 received, terminating vlc - do it again in case it gets stuck
user insisted too much, dying badly
```

it seems that "couldn't find a filter for the conversion" is the reason for "couldn't create audio output pipeline"

launching XMMS with bash gives more details:
```
Message: device: default

** WARNING **: alsa_get_mixer(): Attaching to mixer hw:0 failed: No such device

** WARNING **: Input has 2 channels, soundcard uses 8 channels
No conversion is available
```

So is the device available but it just cant convert output to 8 channels?

---

### Post by alphanimal on 2007-08-13
Just tried opening a DVD with VLC: error message is different

```
[00000334] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.iec958
[00000335] oss audio output error: cannot open audio device (/dev/dsp)
[00000359] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.iec958
[00000335] oss audio output error: cannot open audio device (/dev/dsp)
```

I'm really stuck :(

---

### Post by alphanimal on 2007-08-14
can anybody help? :(

---

### Post by alphanimal on 2007-08-15
ok just installed a fresh ubuntu. my internal card now works again but the external has still that problems.

do i have to be the only one here??? not a single comment from anybody??? you could just say "hi" if you dont know anything about my sound problems :)

---

### Post by th0r0n on 2007-08-20
Hi :) I have a problem with my USB sound too on Audigy NX

---

### Post by alphanimal on 2007-08-20
:-s ALSA is just not made for this chip I guess.

I'm back to Windows. Can't live without sound.

---

### Post by Tomone on 2007-08-24
I'm having the same problem right now where only one app can use my external usb card at a time. It doesn't seem too bad right now, but I know it's going to start to drive me nuts soon.

---

### Post by janfsd on 2007-08-25
Have you tried the official oss drivers? Because the ones provided are really really old.
get them at [http://www.opensound.com/](http://www.opensound.com/)
They used to be binary only, but they just got gpl'ed :)

Personally I haven't tried them, but I have read reports that installing them have fixed sound problems, and even that the sound is better than alsa. BTW there won't be any sound locking problems because they had sw mixing implemented long time ago. I dunno why they don't offered before the binary drivers like they offer binary nvidia drivers and other stuff, if they are better. Maybe this will change in the future. Hope this helps.

---

