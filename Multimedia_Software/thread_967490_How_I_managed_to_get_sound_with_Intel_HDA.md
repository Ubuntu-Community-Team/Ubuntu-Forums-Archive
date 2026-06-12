---
title: "How I managed to get sound with Intel HDA"
date: 2008-11-02
forum: Multimedia Software
---

### Post by siDDis on 2008-11-02
All I did was typing this in the terminal
```
sudo killall pulseaudio
```
So it's no doubt that it's pulseaudio causing all the issues with Intel HDA sound systems.

EDIT:
Some applications also requires this:
```
sudo alsa force-reload
```

But how do I remove pulseaudio completely? If I try to uninstall it from synaptic it asks if I want to completely remove Ubuntu Desktop.

---

### Post by xdotx on 2008-11-02
This has fixed my problems with sound capture (line in) AND flash playback. Thanks for the temp workaround!

---

### Post by beauman on 2008-11-02
It didn't work out for me. 

After killing the pulsaudio server, recording behaves different.
In the gnome audio recorder the time of recording is now progressing
with the right speed. But it's not recording anything.

In the audio setup dialog, I get the message:

gconfaudiosrc ! audioconvert ! audioresample !
gconfaudiosink profile=chat: Failed to Connect:
Connection refused.

I can't test flash with the USB-device I mentioned at the moment.

---

### Post by Spabuntu on 2008-11-02
sort of helped me, i can use skype now althugh its still not perfect. 
thanks anyway!

how can i manage it that this commands are executed everytime i boot ubuntu? and is there a way to avoid that the audiocontrol disappears from the panel?

best wishes and many thanks

spabuntu

---

### Post by sevesteen on 2008-11-02
This is a decent workaround for my problem where only the left channel works after upgrading--now sound seems to work as before.

---

### Post by Bott on 2008-11-02
> **siDDis said:**
> All I did was typing this in the terminal
```
sudo killall pulseaudio
```
So it's no doubt that it's pulseaudio causing all the issues with Intel HDA sound systems.

EDIT:
Some applications also requires this:
```
sudo alsa force-reload
```

But how do I remove pulseaudio completely? If I try to uninstall it from synaptic it asks if I want to completely remove Ubuntu Desktop.


[http://ubuntuforums.org/showthread.p...ove+Pulseaudio](http://ubuntuforums.org/showthread.p...ove+Pulseaudio) is a thread that tells how to remove pulseaudio. I can't take credit for it.  To summarize:


killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo Nautilus

and then browse and remove "/etc/X11/Xsession.d/70pulseaudio"

Other than just getting rid of pulseaudio, I'm searching for posts on how to fix it.  I haven't found any that work for me yet.

---

### Post by rmblack on 2008-11-10
This restored my sound output in right channel only.

I have had sound issues after every kernel update and have found patches or work-arounds, but have never been able to address the source of the problem.
These issues predate my installation of PulseAudio. After my Intrepid upgrade all sound card problems were temporarily resolved, except I had no output to my headphone jack...then, after the first post-Intrepid Rhythmbox update...back to nothing.

Thank you for the partial restoration of my sanity. The search continues...

---

