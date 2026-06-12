---
title: "Fresh install, No Mic Input. What am I doing wrong?"
date: 2010-01-21
forum: Multimedia Software
---

### Post by Stev0 on 2010-01-21
Just finished an install of 9.10. Ran the update manager, installed all updates, nvidia drivers, gstreamer libs, and restricted-extras  For sound I'm using a creative x-fi fatal1ty series card. Under 9.04 it was a royal pain to get that thing working, and I was absolutley amazed to see it recognised immediatley out of the box by 9.1. Using the GUI sound preferences I selected the X-fi card as output device, quick check through music box, Wow, my creative card is playing mp3s perfect with amazing quality without requiring me to fiddle with drivers or alsa, or pulse.  Awesome.
 
Lets try the microphone...I open up sound recorder, switch to the input tab in sound preferences, it lists both my onboard Intel HDA controller from my mobo, and the X-fi. Excellent. Intel HDA shows me a drop down menu where I can specify which mic connector I want. When switching to the X-fi, there is no option to select  a connector, just the input volume slider. Attempting to record sound resulted in a 'what u hear' experience. Quick search through the forums indicated that I should use the alsamixer command from terminal to ensure that the correct mic settings are being applied.
 
Upon running alsamixer I see that it is displaying the Intel HDA controller as the sound device. Makes sense, I recall in 9.04 having to use the asoundconf command to tell alsa which card I wanted to use. Attempting to run that command...asoundconf is not installed. If this were 9.04 I'd have no problem just jumping in there and building alsa from scratch, but I'm brand new to 9.10, and I'm not sure exactly how the X-Fi support came integrated with it, so I'm reluctant to start messing with alsa. Do I need to install the asoundconf and go from there as one would with a fresh install of 9.04 or am I missing some configuration step in order to get my mic working?

---

