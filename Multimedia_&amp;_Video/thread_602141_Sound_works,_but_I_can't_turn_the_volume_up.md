---
title: "Sound works, but I can't turn the volume up"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by Glowing Fish on 2007-11-03
So, after some time, I got several of my sound problems fixed. 
(It turns out that I had pulseaudio installed, but I needed to actually start it from the command line)
And now I can run alsamixer.
The problem is now, everything is very quiet. I have all the volumes turned up to maximum, including the controls on my subwoofer, but most applications play only quietly. 
When I go to run alsamixer, I notice something unusual: there is only the master volume control. Usually, alsamixer has at least six controls.
Is there additional alsamixer tools I need to apt-get ?
Incidentally, my soundcard is a SoundBlaster Live card, which as I understand it should be one of the most standard cards.

---

### Post by kyphi on 2007-11-04
You might have placed a tick where there should not be one.

Right click the speaker icon in the top right corner and left click on 'Open Volume Control'.  Go to Switches and see that Analog/Digital Output Jack is not ticked.  

Check the sliders in Playback and Capture.

You are right about the Soundblaster Live - works like a charm.

---

### Post by Glowing Fish on 2007-11-04
You know, the thing about Linux is it keeps me modest...and I have been using Linux on the desktop since 2000!

I had deleted my volume control from my panel.

I added it and it was halfway up. 
Turned it up.
Problem solved.

---

