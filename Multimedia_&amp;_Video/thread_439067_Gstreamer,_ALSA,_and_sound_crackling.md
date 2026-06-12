---
title: "Gstreamer, ALSA, and sound crackling?"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by hyperair on 2007-05-10
I've been using amaroK for the past few years, and then I decided I'd save some CPU cycles by switching over to some Gtk audio player. I've tried quite a few ranging from Rhythmbox to Banshee to Quod Libet to Listen and finally Exaile, settling with Exaile. One thing I noticed with these audio players is that for some mp3s the sound output will have crackling and popping sounds, as though the range is too great. So what I did was open the Gnome volume control and reduce the PCM sliders slightly. Now I'm done with the crackling sound problem. I never experienced this with AmaroK though (using Xine engine). Now, out of curiosity more than anything, what is the cause of this problem and is there a way to correct this (I mean a fix, not a workaround as I have mentioned above)

---

### Post by ScislaC on 2007-07-20
Same here... been using Amarok, wanted to make things lighter with Rhythmbox... I get lots of crackling in RB. :(

---

### Post by hyperair on 2007-07-20
Sorry, I'd found a fix but forgot to post it here. You need to open your Sound Control.. double click on the sound icon in your panel.

Then reduce the PCM slider to around 85. The crackling should go off. Then you increase everything else to compensate for it.

---

### Post by JPorter on 2007-07-21
The best way to fix the distortion issue is actually to run [FONT="Courier New"]alsamixer[/FONT] and adjust the PCM volume to 0.00 gain.  Run [FONT="Courier New"]sudo alsactl store 0[/FONT] to save it so it persists through reboot.

---

### Post by hyperair on 2007-07-21
How exactly do you do that? >< 

EDIT: Nevermind found it.

---

### Post by JPorter on 2007-07-21
Any improvement?

---

