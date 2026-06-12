---
title: "Pulseaudio - Digital out has just stopped working"
date: 2010-10-10
forum: Multimedia Software
---

### Post by thecapsaicinkid on 2010-10-10
For no conceivable reason, pulseaudio will no longer output via the spdif connection on my onboard sound card.

Up until now, various applications could output digitally (mostly using via the alsa plugin) fine. DVD playback would passthrough DD/dts bitstreams if the application was set to communicate with alsa directly. The sound profile in Ubuntu's audio applet would have to be set to *Analog Stereo Output *for this to work, no idea why.

Now, all the works is digital passthrough via alsa (i.e DVDs). So definitely not a hardware issue. Regular audio either via the alsa plugin or using pulse directly does not work so no music/system sounds/flash etc. 

All sliders are unmuted (see pics linked below) and the volume meters all show movement with sound activity. Changing the *Profile* setting does nothing, I thought maybe it had been fixed so digital actually meant digital.

This has happened before (sometimes triggered by DVD playback and DD passthrough) but usually fiddling with the mute toggles fixed it.Possibly this has been caused by a recent update.

Any suggestions welcome. Thanks.

[http://i54.tinypic.com/9fs75w.png](http://i54.tinypic.com/9fs75w.png)
[http://i52.tinypic.com/2q1scnm.png](http://i52.tinypic.com/2q1scnm.png)
[http://i55.tinypic.com/14l6902.png](http://i55.tinypic.com/14l6902.png)

---

### Post by thecapsaicinkid on 2010-10-10
It seems having to set my output to *Analog* *Output* has been fixed in a recent update so I now need to select *Digital Output *(as expected) but what I didn't realise before was the device in the *Output Devices *tab was muted.

One thing to note, digital passthrough stopped working as soon as I selected digital output, I assume because pulseaudio was blocking the soundcard. To use passthrough I must set the output back to Analog (Gnome Mplayer audio options are set to 'Alsa' and 'Enable AC3/DTS pass-through to S/PDIFpassthrough')

This is all in the Pulse Audio Volume Control app which I believe is a less cutdown version of the main audio applet in the taskbar.

---

