---
title: "Sound Recorder - WTF!  Intel HDA/Realtek ALC880"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by cosmolee on 2006-10-10
Intel D915GEV board w/ Intel HDA/Realtek ALC880, Ubuntu 6.06.

I can talk w/ my microphone no problem with Skype.  So I know that I've got a working microphone setup.

However, I can't record with Sound Recorder (2.14.2).  Sound Recorder does something really ODD.  

I've got the Volume Control opened up, I'm looking at the "Capture" tab under the settings for the "HDA Intel" device.  The capture tab doesn't show any seperate devices for Mic, Line, etc.  It just has one slider labeled "Capture".  Fine.  

What's really odd is that when I start to record with Sound Recorder, the Mute goes ON in the Capture tab, and no sound gets recorded!  I have to manually Un-mute while Sound Recorder is recording in order to get any sound recorded.

In addition, the sound level is drastically reduced - Unusable, really.  

What's with that??

Cosmo Lee ](*,) 


ps: Even more oddness:  In Sound Recorder, there is a "Record From Input" drop-down.  At first, your choices are "Capture", "Capture 1" & "Capture 2".  Each time you record, it adds another set of those choices to the drop-down.  I.E.: if you try to record ten times, you will then see ten duplicate sets of those three choices.  Further, on each successive recording, it will only let you record from "Capture 2".  No matter which one you chose, SR changes your choice to "Capture 2" as soon as you click Record.

---

### Post by Syock on 2006-11-06
I had this problem because I was using the front mic while the input source was set to mic as default. I had only 3 capture channels though.

Here`s what I did:

First I muted capture 2 which was originally used by my Sound Recorder, though I think you can skip this. Just make sure that your input is set to your microphone. To do this, enable the the drop-down menu for Input Source by checking its box in Settings.
Then go to Options tab and select your device from the drop-down menu. Next, raise Capture`s volume. Make sure it`s not muted (both speaker and microphone icon shouldn`t have red X on it). On Sound Recorder, select Capture as the input type. It should be usable by now.

---

