---
title: "Audacity Help"
date: 2024-01-04
forum: Multimedia Software
---

### Post by RangerK on 2024-01-04
Hi Guys,

I have what seems like an extremely simple problem, and I'm frustrated at not being about to get around it.

I can't make audacity play any sound.

[IMG]http://grouper.games/images/audacity1.png[/IMG]

Audacity *thinks* it's playing sound -- as you can tell by the green bars.  Sound definitely works on my computer.

Next to the speaker icon, there are presumably several choices for output.  Here, I photographed them:

[IMG]http://grouper.games/images/audacity2.png[/IMG]

No matter which I chose, no sound.

The strangest thing is that it worked momentarily.  Then I re-opened Audacity to do more editing, and now it doesn't work at all.  I tried re-installing too.

Any help would be greatly appreciated.

---

### Post by TheFu on 2024-01-05
Check that the pulseaudio device you want output going to is working system wide and ensure that audacity is setup to use that device.
The **pavucontrol** tool allows changing the inputs and outputs to PulseAudio. It may need to be installed, but it is the full, official, PulseAudio tool.

BTW, sometimes unplugging the audio device, waiting 10 seconds and replugging in the audio device you want used can work. I think pulseaudio is setup to automatically switch to the most recently connected device.

---

### Post by ajgreeny on 2024-01-05
Just in case it helps here are my audio settings in this screenshot from which I get no problem at all playing the recorded sound before exporting it to a file.

---

### Post by RangerK on 2024-01-05
Thank you guys.  I looked at both of those things.  I already had pavucontrol installed, incidentally.  The **pavucontrol **utility only gave two options under "port" - speakers, and headset (unplugged).  That didn't seem helpful.

Strangely, Audacity started working again when I had my bluetooth headset connected.  It didn't push sound through the bluetooth, mind you, but suddenly "default", "sysdefault", and "front" started pushing sound through my normal speakers, and HDMI 1 started pushing the sound through my computer monitor.

I don't like having to hack my system by toggling a blue tooth device, but I guess that's good enough for now.  If anyone has a suggestion on how to get good at linux audio, I'd invest some time into it.

With my blue tooth on, I had man choices in Audacity:

Six "HDA Intel PCH" choices, including HDMI 0 to 4, and and analog choice.
sysdefault
front
three different Surrounds
hdmi
default
dmix


 Several of them work.  Earlier (see photo) none of them played any sound.

---

### Post by ajgreeny on 2024-01-05
The toolbars of your audacity window look a bit different from mine so I wonder what version of audacity you're using; mine is the Appimage v:3.3.3.
It may also be useful to see the middle tab, **Output Devices** and right hand **Configuration** tab settings of your pavucontrol window.
My Configuration tab is shown in the screenshot; make sure both of your Profiles shown are available and one is not **Off**

---

### Post by RangerK on 2024-01-31
Same problem again.  This is maddening.  I'm going to try the Audacity forums.

---

### Post by &amp;KyT$0P# on 2024-02-24
Bit late to this thread but last I checked Audacity does not use PulseAudio.  Try running Audacity under [FONT=Courier New]pasuspender[/FONT] ?

---

### Post by TheFu on 2024-02-24
> **halogen2 said:**
> Bit late to this thread but last I checked Audacity does not use PulseAudio.  Try running Audacity under [FONT=Courier New]pasuspender[/FONT] ?

I use audacity all the time and never have to touch anything related to pulseaudio.  To record my voice, I just connect a USB mic and it is used by default.  The "monitor" clearly shows this. Yep. Just recorded a clip. I think it will use the device that pulseaudio makes the default on systems with defaults.  

As for the output of audio, again, it just uses the system default as setup in pulseaudio.  The volume controls inside Audacity also work, BTW.

I'm on 
```
audacity       2.3.3-1build1 amd64
```

I don't have any HDMI audio connected on this system.  Generally, HDMI audio is controlled by the GPU, not any audio chips on the motherboard, so be certain you are clear about that.

Output devices:
```
$ pactl list short sinks
0       **alsa_output.pci-0000_09_00.6.analog-stereo**      module-alsa-card.c     s16le 2ch 44100Hz        SUSPENDED
1       dcv     module-null-sink.c      s16be 6ch 48000Hz       SUSPENDED

```

And for the microphones/inputs:
```
$ pactl list short sources
0       alsa_output.pci-0000_09_00.6.analog-stereo.monitor      module-alsa-card.c      s16le 2ch 44100Hz       SUSPENDED
1       dcv.monitor     module-null-sink.c      s16be 6ch 48000Hz       SUSPENDED
2       **alsa_input.usb-Samson_Technologies_Samson_GoMic-00.analog-stereo**       module-alsa-card.c       s16le 2ch 44100Hz       SUSPENDED
```

The DVC devices are from my KVM switch. I don't use it.

The bold devices are what I've set as my default output and input audio devices.  I've disabled all the others, which are shown on the "Configuration tab" of pavucontrol.  I'm specifically using the motherboard audio with the front-panel headphone jack that is connected to 2 speakers.  

On another computer, I have a 5.1 setup that uses 5-6 analog jacks on the back of the motherboard.  Both systems use identical motherboards, but I only have 1 5.1 surround speaker system. ;(

I didn't re-re-read this thread.  Probably best if I just unsubscribe now.

---

