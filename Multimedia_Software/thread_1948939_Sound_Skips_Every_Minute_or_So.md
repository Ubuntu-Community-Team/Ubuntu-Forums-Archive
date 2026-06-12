---
title: "Sound Skips Every Minute or So"
date: 2012-03-29
forum: Multimedia Software
---

### Post by Rodney9 on 2012-03-29
```
$ cat /proc/asound/car*/co* |  grep Codec
Codec: Realtek ALC272
Codec: LSI ID 1040
Codec: Intel Cantiga HDMI
```

Toshiba L500-08P Pentium Dual Core 2.2Ghz , 1Gb Ram

I am using Xubuntu 11.10 64 bit and sound stops and restarts in a split second every minute roughly, it is very annoying.

It happens when playing music with mplayer, Banshee or Audacious and when playing YouTube in Firefox.

It happens all the time even at a clean boot with nothing else running, memory at 20 % and cpu at 2 %.

I have tried adding ```
load-module module-udev-detect tsched=0
``` to ```
etc/pulse/default.pa
``` made no difference.

I have googled and seen many others having similar problems but can't find a fix, Please Help

Rodney

---

### Post by Rodney9 on 2012-03-29
Some of the many other posts describe it as Stuttering.

Any Clues ? This is driving me mad.

Rodney

---

### Post by LewisTM on 2012-03-29
Have you tried removing Pulseaudio?
My machine has a Realtek ALC269 sound card and it runs perfectly with ALSA-only in Xubuntu.

Cheers!

---

### Post by Rodney9 on 2012-03-29
> **LewisTM said:**
> Have you tried removing Pulseaudio?
My machine has a Realtek ALC269 sound card and it runs perfectly with ALSA-only in Xubuntu.

Cheers!

No, I will try though.

Rodney

---

### Post by Rodney9 on 2012-03-29
I used - ```
$ sudo apt-get autoremove pulseaudio
``` 
and
```
$ sudo apt-get purge pulseaudio
```

to remove Pulse. 

As far as I know, I now only have Alsa. 
[I]
[SIZE="3"]The skipping still happens[/SIZE].[/I]

Any other ideas please, I would love to play music while I work.

Rodney

---

### Post by Rodney9 on 2012-03-29
I seem to be narrowing it down.

The laptop speakers, I think, were conflicting with the external USB speakers. If I mute the laptop speakers the glitches are not as bad, still very annoying.

Now I just have to work out how to set all sounds to the external speakers.

I can tell Audacious to play thru them, but how do I get mplayer, firefox, system sounds etc all working ? Then still use Skype thru the headphones/mike ? 

Who would of thought, plugging in a couple of speakers, would be so hard to make work.

Rodney

---

### Post by Rodney9 on 2012-03-30
No, I take it back, the skips are just are bad using Alsa and muting the laptop speakers.

I have read that disabling the laptop speakers in bios helps, but there is no option in my bios, this is getting crazy just to get speakers working.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AUDIO [USB  AUDIO], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


Rodney

---

### Post by Rodney9 on 2012-03-30
Is there anyway of playing music in Xubuntu  without skips ?

I tried 12.04 Beta 2 and it skips in it as well.


I am afraid this is beginning to make me conclude it's my laptop, but you would think the USB speakers would negate the the sound chip in the laptop, I don't know.

Rodney

---

### Post by Rodney9 on 2012-03-30
I tried the same music files, thought maybe it was them, the same speakers , in my desktop running Lubuntu 11.10 and it all played perfectly.

So I'll try Lubuntu on this laptop and see, if it still skips, at least I know it is the laptop or Xubuntu.


Rodney

---

### Post by Rodney9 on 2012-03-31
Just when I was about to give up and believe it was my laptop.

I tried Pinguy 11.04 64bit and sound plays perfectly and the easiest to set up for the USB speakers.

I do not know what the difference is, Pinguy is built on Ubuntu and uses pulse.

Rodney

I can not mark this as solved as I could not stop music skipping / stuttering in Xubuntu 11.10 or 12.04 beta 2, sadly.

Rodney

---

