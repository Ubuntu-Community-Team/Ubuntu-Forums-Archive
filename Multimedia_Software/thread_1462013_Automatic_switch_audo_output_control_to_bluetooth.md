---
title: "Automatic switch audo output control to bluetooth"
date: 2010-04-25
forum: Multimedia Software
---

### Post by iamroddo on 2010-04-25
I'm using a Hama Voiis bluetooth audio device connected to my stereo. Both my girlfriend (running 9.10) and me (10.4) can pair with, connect to and stream audio from whatever application we use to the device. However to do so requires a couple of manual steps which I'd like to optimise.

First it's necessary to manually connect to device, since we both want to stream to this, connecting manually seems the best since I suppose only one can connect at any one time.

Once connected it's necessary to select "Output" in "Sound Preferences" in order to use the keyboard or multimedia keys to change the volume. This latter step is a little annoying since it has to be done every time we connect. Does anyone have a solution that automatically makes this change when connecting?

---

### Post by kostkon on 2010-04-25
You could try setting it as the default device in Sound prefs (although I highly recommend you to install the *PulseAudio Device Chooser* utility and use the pulseaudio volume control, for a more fine-tuned control over your audio devices and streams) and when you are not connected to it your system should fallback anyway to your second available audio device, thus you'll not have to do all these steps that you mentioned.

---

