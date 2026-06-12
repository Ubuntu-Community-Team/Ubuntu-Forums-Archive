---
title: "Stuck with Terratec PhonoPreAmp iVinyl"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by biblonchk on 2008-02-02
Dear all,

I've shortly acquired a Terratec iVinyl PhonoPreAmp. It's USB and works  under os-x or window$ without requiring any particular device driver for recording. A proprietary software included in package is required for 32 bits recording (which is not in my plans)

'gusty gibbon' detects an usb1 audio device and set alsa with snd-hwdep, snd-usb-audio and snd-usb-lib for hw:1,0 dynamicaly.

Alsamixer shows for the iVinyl device a simple 'mic' switch as a unique controler (no volume or other tuning at all). But this is also the case on the other plateforms.

Here the output of `cat /proc/asound/cards´

[INDENT]```
 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xdc00, irq 11
 1 [iVinyl         ]: USB-Audio - PhonoPreAmp iVinyl
                      Terratec PhonoPreAmp iVinyl at usb-0000:00:11.0-1, full speed

```
[/INDENT]


Having found working parameters for iVinyl by running `arecord´ with all
available formats, i can now run the following command and get a vinyl recorded:

[INDENT]```

$ #
$ # Notice: 
$ #   Format must be given. Only `S24_3LE´ seams to work.
$ #   Channels must be given.
$ #   Rate default to 32000. 44100, 48000, 96000 may be given.
$ #
$ arecord -v -D iVinyl -f S24_3LE -r 44100 -c2 test.wav
Enregistrement en cours WAVE 'test.wav' : Signed 24 bit Little Endian in 3bytes, Taux 44100 Hz, Stéréo
Hardware PCM card 1 'PhonoPreAmp iVinyl' device 0 subdevice 0
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
  format       : S24_3LE
  subformat    : STD
  channels     : 2
  rate         : 44100
  exact rate   : 44100 (44100/1)
  msbits       : 24
  buffer_size  : 22050
  period_size  : 5513
  period_time  : 125011
  tick_time    : 1000
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 5513
  xfer_align   : 5513
  start_threshold  : 1
  stop_threshold   : 22050
  silence_threshold: 0
  silence_size : 0
  boundary     : 1445068800
Terminé par le signal Interruption...
$

```
[/INDENT]

But Audacity crash miserabily as soon as AudioI/O preferences are saved with recording device set to iVinyl (hw:1,0). Have play hours around type,pcm,hw,slave,plug... in .asoundrc without result. Nor did I got a sound from jack or pulse audios, but this is due to my poor knowledges in sound handling in general and alsa stack in particulary :(
Furthermore, this device doesn't exist by Alsa, isn't given as compatible with linux by it's manufacturer, nor it is found in a tip in linux forums or in google...
In other words i'm stuck.

[LIST]
[*]Q1: How do i translate -f -r and -c options of the `arecord´ above into a named setup for capture device located in `asoundrc´, in a way that may be used next as '-D' option param for the arecord command ?
[*]Q2: How do i bind this for Jack or Pulse audios ?
[/LIST]
Could someone help me in setup ?

Many thanks in advance for your tips.
Kindest regards
blonchk

---

### Post by biblonchk on 2008-02-04
Solved by purging pulseaudio stuff accordingly this tread [http://ubuntuforums.org/showthread.php?t=601522](http://ubuntuforums.org/showthread.php?t=601522).
Can't still not connect audacity to native alsa pcm for iVinyl device, but it works if connected to jackd.

---

### Post by biblonchk on 2008-02-04
Solved by purging pulseaudio stuff accordingly this tread [http://ubuntuforums.org/showthread.php?t=601522](http://ubuntuforums.org/showthread.php?t=601522).

Can't still not connect audacity to native alsa pcm for iVinyl device, but it
works if connected to jackd.

---

