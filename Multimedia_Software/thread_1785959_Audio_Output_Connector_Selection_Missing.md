---
title: "Audio Output Connector Selection Missing"
date: 2011-06-19
forum: Multimedia Software
---

### Post by fredyboy10 on 2011-06-19
After a recent installation of Ubuntu 11.04 I noticed the connector selection box was missing from the output tab of gnome-volume-control. I found this very useful in the past being able to change to output from one sink to another. What happened to this option?

---

### Post by fredyboy10 on 2011-06-21
Any suggestions?

---

### Post by BicyclerBoy on 2011-06-21
The gnome sound prefs looks the same on my 10.04 & 11.04 boxes...

Can you elaborate what the connector selection was used for ?

I have to change/config the device using the hardware tab..
Maybe the existing output device profile has only one connector option ?

---

### Post by fredyboy10 on 2011-06-22
I have gone through all of the hardware configurations and none of them provide this selection. The selection allowed one to force the audio through only the headphones or the speakers or provide the usual configuration of speakers first then headphones. The image below shows the options I used to have available.

[IMG]http://i51.tinypic.com/2jyweh.png[/IMG]

---

### Post by BicyclerBoy on 2011-06-22
Could be the new install alsa does not correctly determined your audio h/w ouptut connector stack.
I guess that the new install could have over-written/replaced/ignored some snd-hda-intel module options.
These options would have been in /etc/modprobe.d/  & the files could be sound.conf or similar.

There are alsa info scripts on the alsa project webpage but I would not be able to be any help.

Figure out your mobo & audio hardware & then search alsa website for any special/specific module options.

---

