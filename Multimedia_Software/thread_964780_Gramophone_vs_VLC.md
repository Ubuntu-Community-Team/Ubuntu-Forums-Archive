---
title: "Gramophone vs VLC"
date: 2008-10-31
forum: Multimedia Software
---

### Post by Qrjusz on 2008-10-31
Hi there

the situation looks like this: I have a gramophone connected to my PC by the line-in input. I can hear perfectly the sound in my speakers. I wonder if there is a possibility to record the sound from gramophone and/or to equalize it in for eg VLC.

---

### Post by ajgreeny on 2008-10-31
You can record it easily using audacity and other applications available from the repos; equalisation I'm not too sure about.   I have used audacity a lot but none of the others.  Just make sure you have line in enabled in alsa-mixer and that "capture" is set appropriately for the recording.  I think it will all become clear when you do it, but if not, come back again.

---

### Post by Qrjusz on 2008-10-31
heh so I'm back. I guess the problem is not that simple as i thought. Firstly in my alsa mixer I don't have those switches to capture (dunno why, I've had them some time ago). Secondly Audacity doesn't record even my mic (even if it's configured correctly eg I'm able to hear myself and talk on Skype). I guess it's a problem of Audacity but i don't know what should I set 'cause no matter what I chose (OSS or ALSA) it doesn't work:/

---

### Post by ajgreeny on 2008-10-31
OK, so double click in the volume control icon in your panel and then go to edit->preferences.  There you should be able to add various items to show in the alsa-mixer which shows when you double click on volume.  You may need to set which evice is showing first by right clicking in the volume icon and choosing whichever one shows alsamixer, maybe in brackets after the card name for example mine shows **NVidia nForce2 (alsamixer)**.

Just to help further, in my sound preferences I have everything set to pulse audio except the Default Mixer Tracks which are set to **NVidia nForce2 (alsamixer)** again. Perhaps different sound cards work differently, but this all works brilliantly for my system.

---

### Post by Qrjusz on 2008-10-31
Ok so i got my mic and input recording working. I've tried a few combinations (the one with Pulse didn't work, I had to set this all to ALSA) and the one i have now works great. But still I would like to ask if VLC can capture this input signal from my gramophone and equalize it? VLC or any other player with equalizer.

---

### Post by aeiah on 2008-10-31
vlc isnt really meant for recording. now you have your soundcard working, have you tried audacity? or are you actually just wanting to play your vinyls and use vlc to equalise the sound, and not record at all?

---

### Post by Qrjusz on 2008-11-01
Yeah exactly. I know I can record them using Audacity and the basic gnome-sound-recorder but I would like to pass the signal from my line-in by the equalizer to the speakers. To use my PC as an equalizer in other words. Is it possible? I know i can receive the line-in video signal (using video4linux) but is it possible to actually listen the vinyl in VLC?

---

