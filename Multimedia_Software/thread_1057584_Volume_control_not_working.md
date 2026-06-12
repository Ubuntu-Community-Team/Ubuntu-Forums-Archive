---
title: "Volume control not working"
date: 2009-02-01
forum: Multimedia Software
---

### Post by AdamW0 on 2009-02-01
I just installed Ubuntu on an Dell Inspiron 9300.
Everything worked out of the box, except volume control. Using the multi media volume buttons shows a nice pretty image showing us that the volume is say, muted, or 25% up.
So the operating system thinks it controls the volume, and it seems the buttons are hooked up.
Interestingly, a youtube video's volume thingy works fine.
Any suggestions, help?

Ohh just checked got some helpful info:
Get this, the volume control works, but it seems to be independantly controling a set of normal speakers, while a deeper "Subwoofer" keeps droning on. So we need to control the subwoofer.

At full "Volume" everything sounds pretty good, but muted, it sounds like you got a little to excited with the eq.


Okay, this might help you more:
When the mute butten is pressed, ONLY the Master volume it muted.

PCM is now muted, but when muted (Rclick on volume, Open Volume Control) everything is muted.
Any help?

Another update:
If I can control pcm, then everything works. The prob:
In sys-prefs-sound I cant select PCM as the default.
Help!!

It should work to right click on volume, preferances, and then select PCM
But it dont

---

### Post by Metaljaz on 2009-02-03
Try this:

System>Preference>Sound
under Device select PCM and you should now be able to control
the sound with the volume button on the laptop. Make sure
the Device selected, such as Intel (ICH5) Alsa Mixer is the 
device that is selected under volume control preferences.
Try to make sure those devices match.

---

### Post by AdamW0 on 2009-02-04
Yay! it worked!
Still, funny that volume preferences did not work.

---

### Post by Puzzled Guy on 2009-11-21
Thanks! That worked for me. My problem was probably caused as an after-effect of my fiddling to get Skype to work (which failed miserably)

---

