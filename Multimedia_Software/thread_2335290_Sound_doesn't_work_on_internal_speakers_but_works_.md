---
title: "Sound doesn't work on internal speakers but works on headphones"
date: 2016-08-27
forum: Multimedia Software
---

### Post by Firubat on 2016-08-27
I recently switched from windows7 to Xubuntu on Dell Inspiron N4030, and  I have a problem that sound only worked through the headphones jack,  and not with the internal speakers. I tried to troubleshoot it myself  using all kinds of threads and guides I found with similar problems, to no avail. After I messed  something up and it didn't work at all (thankfully rebooting restored to  the previous state) I decided to give up trying myself and hope for  more informed support. 
[FONT=courier new][FONT=arial][FONT=verdana][FONT=courier new][FONT=verdana]
I run Xubuntu 16.04.1 on Dell Inspiron N4030.
Some info:
[/FONT][/FONT]```
uname -a
Linux Ur-Inspiron 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k4.4.0-34-generic
[FONT=courier new][FONT=arial][FONT=verdana]
[FONT=courier new][FONT=arial][FONT=verdana]head -n 1 /proc/asound/card*/codec#*
Codec: IDT 92HD81B1X5[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]

lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Dell 5 Series/3400 Series Chipset High Definition Audio
    Flags: fast devsel, IRQ 22
    Memory at fbf00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 25

```

[/FONT][/FONT][/FONT]I tried adding to [FONT=courier new]/etc/modprobe.d/alsa-base.conf[FONT=verdana] the line [/FONT][/FONT]
```
options snd-hda-intel model=X
```
Where X is replaced with all kind of things that didn't work. Note that in the [HD-Audio-Models list]("http://lxr.linux.no/#linux+v4.4/Documentation/sound/alsa/HD-Audio-Models.txt") there is no category for [FONT=courier new][FONT=arial][FONT=verdana][FONT=courier new][FONT=arial][FONT=verdana]92HD81* codec, so I'm not sure which one *should* work.


I thought this might also be a hardware problem, but I don't know how to test it.

Thanks in advance.
[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]

---

### Post by Firubat on 2016-08-29
Well, I ran some test through the BIOS that might indicate it is indeed a hardware test (it was not an audio-test per-se, which there isn't one, but some trick mentioned [here]("http://en.community.dell.com/support-forums/laptop/f/3517/t/19351382"). If anyone knows of a sure way to check I'd be happy.

---

### Post by grege2 on 2016-09-12
In the mixer app check to see what output is used as the default. Also try installing gnome-alsamixer and playing with the toggles. I have had good results in the past from settings that seem unrelated. Try all settings not just the ones that make sense.

---

### Post by Bucky Ball on 2016-09-12
Install Pulse Audio Volume Control if you haven't already. Get an audio stream going (play some music). In PAVControl, check the output tab and see which port the stream is going to; headphones, external speakers, somewhere else ...

Check the details of the stream in the Playback tab. Experiment and see if you get anywhere.

---

### Post by Yellow Pasque on 2016-09-14
^If that doesn't work, give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Firubat on 2016-09-14
Thanks for the replies.
I attached a screenshot of alsamixer and PAVcontrol while sound is supposed to be streaming. 
The port is "Speaker". 
Tried all kinds of things with no success.

ALSA information: [http://www.alsa-project.org/db/?f=396dd75be9955d9c236d820bf1180581a77c6176](http://www.alsa-project.org/db/?f=396dd75be9955d9c236d820bf1180581a77c6176)

I truly suspect a hardware problem, but not sure how to confirm that.

[ATTACH=CONFIG]271178[/ATTACH]

---

### Post by Bucky Ball on 2016-09-14
Ok, go to the 'Playback' tab with the stream going. It should give you the stream of the *app* you are using and after '*on*' and a selection box.  Right device?

Attached a pic of my 'Playback' tab and audio stream setting.

---

### Post by Firubat on 2016-09-14
it looks different:

---

### Post by Bucky Ball on 2016-09-14
Nice song choice! Er, yea, you probably have the one device configured so no device selection is showing up in 'Playback'. Try 'Configuration' and make sure the device you are trying to use is actually selected there.

---

### Post by Firubat on 2016-09-15
:) thanks!
well I'm not sure what I'm supposed to see - it just says "built in audio", and that's indeed what it is. But it doesn't specify more.
The options in the menu are:
- Analog Stereo Duplex
- Analog Stereo Output
- Analog Stereo Input
-Off
And none of them works.

---

### Post by Bucky Ball on 2016-09-15
Analogue stereo duplex is what it was on when you checked or you changed it to that? That is what you want.

---

### Post by Firubat on 2016-09-15
That's what it was when I checked.

---

### Post by Firubat on 2016-09-22
Any ideas?

---

