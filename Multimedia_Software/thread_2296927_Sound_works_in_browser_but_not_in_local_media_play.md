---
title: "Sound works in browser but not in local media player, parole, rythmbox"
date: 2015-09-29
forum: Multimedia Software
---

### Post by enixon on 2015-09-29
My sound works fine watching youtube videos or drag-dropping music or video files onto the browser, but doesn't work at all when playing on a local media application. I've tested this on Parole and Rythmbox. I should note that everything worked fine when I installed xubuntu 15 a few days ago. There's no sound drivers to be found in additional drivers. I'm a bit stumped at this point because no one else seems to have the same scenario.

Any help would be greatly appreciated.
-Enixon

---

### Post by Rob Sayer on 2015-09-30
The first thing I'd suggest is to copy/paste these lines into terminal, one at a time:

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

since ubuntu doesn't ship with closed source codecs.

I really don't think it's a sound driver issue since the sound works with your browser.

---

### Post by Yellow Pasque on 2015-09-30
Make sure you have the correct sound device selected in the sound control.

Is it just Rbox and parole, or is it any local application? Does this command produce any output?
```
paplay /usr/share/sounds/alsa/Front_Left.wav
```

---

### Post by enixon on 2015-10-01
Thanks for the advice, both of you. I already had ubuntu-restricted-extras installed. The 'Front_Left' wave file does play when I put that in the terminal. I also installed VLC to test, VLC plays fine. So it's only parole and Rythmbox. I like Rythmbox and would prefer use it. Doesn't make much sense to me that it some programs work but other don't. I've used ubuntu for 10+ years but on this one I'm stumped.

---

### Post by Yellow Pasque on 2015-10-01
> Doesn't make much sense to me that some programs work but others don't
The common link is that Rhythmbox and parole both use gstreamer.

You should already have the packages installed, but run this to verify:
```
sudo apt-get install gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-libav
```

Next, do a simple gstreamer test (make sure your volume is at a reasonable level) and post the output of the gst-launch command:
```
sudo apt-get install gstreamer1.0-tools
gst-launch-1.0 -v audiotestsrc ! audioconvert ! audioresample ! pulsesink
```

---

### Post by enixon on 2015-10-01
The gstreamer plugins were not installed on my computer. Not sure how that happend but both applications are working now. Thank you for your help Temüjin.

---

