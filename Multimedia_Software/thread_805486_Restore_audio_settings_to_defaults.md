---
title: "Restore audio settings to defaults?"
date: 2008-05-24
forum: Multimedia Software
---

### Post by pirotrav on 2008-05-24
Hi,

So i did a lot of futsing with my audio settings trying to get 5.1 dolby digital to work and turns out i just made a mess.  I installed pulse audio, tried to use that, messed with my default sound card and a few other things and now i have no audio output at all!

So my question is this: is there a way to restore all audio related configurations to the defaults without reinstalling ubuntu?

Thanks,
Travis

---

### Post by Fevrin on 2008-06-08
Did you happen to find any solution?  I'm in a similar, albeit less extreme, situation—I've been wondering how to reset my GNOME audio profiles to their defaults, but I haven't found an answer as to how to do that.  I've tried searching for the file(s) that holds the actual data that you can edit with gnome-audio-profile-properties with no luck.

---

### Post by markbuntu on 2008-06-08
If you have these:

alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)

libasound2-plugins (jack, OSS, pulseaudio)

libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

You can get everything back into working order fairly quickly and without a lot of fuss. 

First use asoundconf-gtk to set alsa default to your sound card then go to System/Preferences/Sound and set all the entries to alsa instead of automatic. Then open the gnome-alsamixer and turn everything on and put the volumes up and be sure to select mix. You might want to mute the microphone to prevent feedback.

Then reboot and everything should work.

That way everything is reset to go through alsa to your sound card. If you are using jack set the driver to alsa with jack control and the input and output to default for now though you may want to change that later. You can also check with the pulseaudio manager to make sure the default input and output sinks are set to alsa. They should be.

---

### Post by A-sop on 2008-09-25
Hi markbuntu, 

when I tried to set alsa with asoundconfig, I got this:

logan@logan:~$ asoundconf-gtk
Traceback (most recent call last):
  File "/usr/bin/asoundconf", line 430, in <module>
    exit_code(set_default_card(sys.argv[2]))
  File "/usr/bin/asoundconf", line 348, in set_default_card
    (j, k) = sep.split(i)
ValueError: need more than 1 value to unpack
Traceback (most recent call last):
  File "/usr/bin/asoundconf", line 430, in <module>
    exit_code(set_default_card(sys.argv[2]))
  File "/usr/bin/asoundconf", line 348, in set_default_card
    (j, k) = sep.split(i)
ValueError: need more than 1 value to unpack

can you help?

Logan

---

### Post by A-sop on 2008-09-25
> **markbuntu said:**
> 


First use asoundconf-gtk to set alsa default to your sound card ...

When I ran this in terminal , it only came up with PulseAudio and NVidia - although I checked Synaptic for the packages you mentioned. 

Any ideas?

---

### Post by markbuntu on 2008-09-25
Wow, this is an old thread. Since then I have written a guide to getting your sound working. It is here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by narcisgarcia on 2010-04-30
This can help you:

[http://ubuntuforums.org/showthread.php?t=237096](http://ubuntuforums.org/showthread.php?t=237096)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

And/or deleting soundcard settings for alsa:
```

sudo mv /var/lib/alsa/asound.state /var/lib/alsa/asound.state.bak
sudo invoke-rc.d alsa-utils restart

```

markbuntu has been maintaining a detailed guide for sound troubleshooting:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

