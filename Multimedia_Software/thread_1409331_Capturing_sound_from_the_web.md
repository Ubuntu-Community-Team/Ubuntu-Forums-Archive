---
title: "Capturing sound from the web?"
date: 2010-02-17
forum: Multimedia Software
---

### Post by savaan on 2010-02-17
I've tried to look up different programs for this but can't find anything :( Any suggestions? I'd like to be able to open my recorder on Myspace for instance and capture any sound playing through my speakers. I used to have a little program for this, but its windows based and won't seem to install correctly in WINE

---

### Post by arvevans on 2010-02-17
I use "sound recorder" for this function.
With Gnome it is in Applications->Sound and Video->Sound Recorder.

---

### Post by savaan on 2010-02-17
I have no idea how you're getting that to work. I don't really see any settings in there, and simply hitting my record button while listening to the stream didn't work :( Was there anything else you did?

---

### Post by hxcobd on 2010-02-17
This is much easier than people make it out to be, you don't need WINE or any other external application.

Install all of your distro's Pulseaudio applications, namely PulseAudio Volume Control.

Open PulseAudio volume control.

Under "Input Devices," click the dropdown and show only "Monitors."

Check "Set as Fallback" for whichever device you listen to audio with.

Under "Output Devices," just make sure your correct output device is selected.

Now open Audacity or another audio recorder, go to Audio Setup, and make sure "pulseaudio" is selected for both recording and playback. Deselect any options that say "monitor while recording" or "loopback."

Voila. You may have to tweak these settings a bit, this is a general guide.

---

### Post by ell02 on 2010-02-17
Here is a nice guide for setting up pulse. Getting sound recorder to record your speakers is toward the end.It worked well for me.
[http://ubuntuforums.org/showthread.php?p=8043003](http://ubuntuforums.org/showthread.php?p=8043003)

---

### Post by savaan on 2010-02-17
That worked perfectly :) Thanks guys!

---

