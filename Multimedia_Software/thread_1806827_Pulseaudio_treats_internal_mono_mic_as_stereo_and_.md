---
title: "Pulseaudio treats internal mono mic as stereo and google hangout resets changes"
date: 2011-07-18
forum: Multimedia Software
---

### Post by danielsbrewer on 2011-07-18
I have an Acer Aspire One A150.  PulseAudio treats the internal microphone as stereo rather than mono and so be default does not work.  This can be fixed by using pavucontrol to unlock the controls and set one channel to mute.  This works with Skype as long as the "automatically adjust levels" option is unset.

The problem I am having is with Google hangouts (probably applies to Google talk too), which appears to adjust the volume levels as well and there is no option to stop it.  This has the effect of making the mic stop working every 30 seconds until I adjust it again ... which gets very frustrating.

Is there a way to fix the pulseaudio configuration so that my microphone is treated as mono?  Or is there any other way around this?

Thanks in advance

Dan

---

### Post by danielsbrewer on 2011-07-18
This might be a possible solution:

> To turn off autoadjust by google talIk plugin:
cd ~/.config/google-googletalkplugin # get to google chat's directory
cp -p options options.bak # make a backup before changing stuff..
gedit options # edit the config file
If you don't have file named options in this folder create one..
Add following line to this file..
audio-flags=1

I'll try it tonight and see

---

### Post by danielsbrewer on 2011-07-18
Another possibility might be to include Jack between alsa and pulseaudio:
[http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/](http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/)

---

### Post by yaidiot! on 2011-07-19
I ran into this trouble. I was able to fix the issue by changing the input in gstreamer-properties. Mine was set on custom rather than pulseaudio...

Testing with arecord works, now i need a reliable test number...

---

### Post by Benedolt on 2012-07-02
Hello everyone!
I am having *exactly* the same issue as Dan on a different Acer laptop. Did you guys by any chance figure out to fix it?

EDIT

Never mind, after another firefox restart, the "audio-flags=1" thing seems to work.

---

### Post by danielsbrewer on 2012-07-03
The changes to the gtalk config file worked for me in google hangouts.

---

### Post by Yellow Pasque on 2012-07-03
If you have to mute one channel to hear audio, you could have an inverted mic: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1002978](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1002978)

---

