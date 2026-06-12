---
title: "pulseaudio and mythbackend"
date: 2010-02-15
forum: Mythbuntu
---

### Post by tim.otten on 2010-02-15
I recently upgraded my Ubuntu desktop from 8.10 to 9.10. The desktop had a working MythTV frontend+backend installation configured with a WinTV Go capture card. After upgrading, the sound stopped working *in two ways*. I wanted to post a quick note on my experience.

Firstly, the frontend wouldn't play sound for previously recorded TV. Some Google searching led me to this forum (and some similar ones) which pointed out that one can fix this by passing an environment variable to mythfrontend, e.g.

*export* EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1

Great. One problem solved.

Secondly, even once the frontend played sound for previous recordings, it would not play sound for live TV. This was a familiar problem -- the volume settings for the audio capture device were wrong, so mythbackend was unable to record audio. In the past, one could use alsamixer to twiddle the audio capture volume. However, under 9.10, alsamixer appears heavily neutered, and it seems that pulseaudio's mixer is "preferred."

I've searched Google, pulseaudio.org, mythtv.org, ubuntu.com, et al for guidance on how to get the audio-capture working correctly with mythbackend and pulseaudio. The only useful suggestion I found was to uninstall pulseaudio, e.g.

[http://ubuntuforums.org/showthread.php?t=1404161](http://ubuntuforums.org/showthread.php?t=1404161)

Of course, this is a bit ugly -- it breaks the volume widget in the main Gnome panel, it breaks the volume hotkeys, etc. Instead, one can trying removing the stock /etc/asound.conf:

mv /etc/asound.conf /etc/asound.conf-pulseaudio-bak

This file has several references to pulseaudio. If you remove it, then the alsamixer will work again, and you can twiddle the audio capture volume.

---

### Post by mulad on 2010-03-10
I have gotten stuck in exactly the same spot, though I am unable to remove PulseAudio because I need the desktop integration.

I thought I had it going correctly for an instant, but that victory was shortlived.

I am confused how this whole MythTV -> ALSA (library) -> PulseAudio -> ALSA (kernel driver) path is supposed to work when mythbackend starts up as the system boots, while the pulseaudio daemon doesn't start until you at least get a login prompt via gdm.

Currently, my /etc/asound.conf file looks like this:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

I have mythfrontend using "ALSA:default" as the output device, but that only works with the "EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1" environment variable.

Earlier, I had tried going through the instructions at [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup) but there isn't much there regarding MythTV other than it didn't work for a while and now it's supposed to work in versions 0.21 and later.  There was also mention of adding these lines to ~/.pulse/default.pa: 

```
load-module module-alsa-sink device=hw:0
load-module module-alsa-source device=hw:0
```

...but that didn't seem to help at all (I think it made it so PulseAudio didn't work at all, and I couldn't get the volume control or System -> Preferences -> Sound to start).  After that didn't work, I simply decided to remove the ~/.pulse directory and ~/.pulse-cookie file and logout and log back in.

I'm currently trying to figure out if I can configure /etc/asound.conf in a way that would only have audio *output* feed through to PulseAudio, and have the ALSA libraries access the *input* directly.  I'm not sure if that's going to work (from the symlinks created in /proc/$(pidof pulseaudio)/fd it looks like pulseaudio always opens the device in read/write mode, which could screw up my idea).



I had fought PulseAudio to a reasonable standoff in Ubuntu 9.04, but when I upgraded to 9.10 (which finally fixed my ATI video so that it wouldn't have tearing during playback), my sound got all screwed up.  In Ubuntu 9.10, I could either have PulseAudio talking to the sound devices, or I could have MythTV talking to them, but not both.  Totem and other video players would start up but wouldn't play when I pressed the play button.

---

### Post by mulad on 2010-03-10
Well, after all my whining, it looks like I just had to get the input volume set up correctly and it now seems to be working.  I had to run

```
alsamixer -D hw:0
```

to get it going (this bypasses PulseAudio and accesses the hardware mixer directly -- you may need to use "hw:1", "hw:2", or some other parameter to specify a different device).  You have to press the Tab key to go to the Capture section, then move left and right to enable capture on the right input and use the up/down arrow keys to set the input volume.  On my system, I also have to flip a toggle a few times to get it to record on the "Line" input rather than "Mic" or "Front Mic".

I did modify /etc/init/mythtv-backend.conf to change the line

```
    exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
```

...to instead read

```
    exec /bin/su -c "env EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1 /usr/bin/mythbackend $ARGS" $USER
```

...though I'm not sure if that was necessary.

I just have mythbackend using "/dev/dsp" as the input audio device.

I suspect the volume/input settings won't survive a reboot, but maybe I'll get motivated to figure out how to fix that tomorrow.

---

### Post by markackerman8@gmail.com on 2010-10-20
Did you ever get it working?, it has been a problem for me for months.

Mark

---

