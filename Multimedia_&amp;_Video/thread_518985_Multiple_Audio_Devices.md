---
title: "Multiple Audio Devices"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by jaldus on 2007-08-06
I have a question concerning multiple audio devices on the same machine.

My girlfriend uses Ubuntu (with the Kubuntu-Desktop, not Gnome), and has a regular set of speakers plugged into her built-in sound card on her machine.

Once in a while though, she would like to use a USB headset.  Ubuntu detects the headset fine, the driver works and all, but the audio is still coming out of the speakers.

I was wondering
A) with ALSA how do you change the audio device? and
B) is there a way I can set it up so when ALSA detects the USB headset, it automatically switches to the headset?

---

### Post by fredj on 2007-08-06
Try opening the Alsa mixer (double click on the speaker icon) and go to the 
File->Change Device menu. However since the USB device is output only this may not
give you a working configuration.  Getting the soundcard to work for input and the USB to
work for output can be done but its not that easy.

---

### Post by jaldus on 2007-08-07
In the ALSA Mixer (Kmix?) the File menu only has the option to Quit.

The headset itself also has a MIC and KMix gives me the option to set both the PCM and Mic volume.

But again, I don't see an option to change device.
i've also tried turning on 'Auto Gain Control' under the USB device configuration, but that doesn't seem to work either.

---

### Post by fredj on 2007-08-08
I was assuming that the Kabuntu mixer was the same as the Gnome one. Obviously its not.

---

### Post by jaldus on 2007-08-09
I installed gnome-alsamixer.
It also only has "Exit" under the File menu.
I suspect I am missing some alsa package that gives additional configuration options. 

Could anyone give me some suggestions as to why it seems other people get the option to switch audio devices in their mixers and I don't?

---

### Post by Lucky_ on 2007-08-11
You can install asoundconf-gtk, it comes in settings in the menuK.
Then you can choose the default sound card.
It's the only easy way I could find to switch between the sound card and the headset.
Don't forget to update kmix and the master channel

---

### Post by jaldus on 2007-08-14
That was the perfect solution Lucky_.
Now to start bugging some KDE people to make a similar program...

---

