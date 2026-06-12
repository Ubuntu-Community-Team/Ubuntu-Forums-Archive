---
title: "Pixeled playback with fglrx"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by Caligula on 2008-04-19
Hey people,

I have a serious problem with fglrx.
Whenever i try to play a video the picture is very pixeled.

It happens both with xine and gstreamer, in kaffeine, totem, mplayer and vlc.

I've tried to use vlc with the opengl video output, but that just crashes the player. If I try to configure xine to use opengl it gives me an error.

I'm using the 8.3 fglrx driver, 7.3 Xorg I believe (the one that comes with hardy by default), and running compiz via AIGLX.

Turning off compiz doesn't help, neither does using xgl.

If anyone can help with that issue I'll be his slave for eternity :]

Thanks!

Josh

---

### Post by mc4man on 2008-04-19
i'm using nvidia so pretty useless for direct help but if you open a player from the terminal the error messages can be informative. Vlc is usually short and to the point. Set output module back to default 1st.

---

### Post by dashnak on 2008-04-19
That happened once to me, it turned out that the video module I was using to output the video (you can select this from within the program) was on X11. I changed it to GL and it worked like a charm.
Then it stopped working with GL and I switched to something else.
Experiment a bit with this.
BTW: Love your sig. :D

---

### Post by Caligula on 2008-04-19
> **dashnak said:**
> That happened once to me, it turned out that the video module I was using to output the video (you can select this from within the program) was on X11. I changed it to GL and it worked like a charm.
Then it stopped working with GL and I switched to something else.
Experiment a bit with this.
BTW: Love your sig. :D

Yeah, that's what I meant about changing the video output to opengl. It just crashes vlc for me. bugger.

what part about it did you like? :P

---

### Post by mc4man on 2008-04-19
shot in the dark
sudo aticonfig --overlay-type=Xv

---

### Post by dashnak on 2008-04-20
> **Caligula said:**
> Yeah, that's what I meant about changing the video output to opengl. It just crashes vlc for me. bugger.

what part about it did you like? :P


Don't only try GL output. Try some others, some will crash, some may actually work.
Also, if you are using compiz, try to enable the video playback plugin in the settings.
I like " 				No Gods No Masters Anarchism!"

---

### Post by alexei.colin on 2008-05-10
Hi, I have the *exact* same problem -- pixelated DVD playback. Everything in the original post applies except my fglrx is 8.1. 
- Same problem under both Metacity and Compiz. 
- OpenGL output crashes VLC
- Xv and X11 have same problem 
- aticonfig --overlay-type=Xv did not fix it
- CPU is not overloaded (~15% load) during playback

Did anyone find a fix for this? Thank you in advance!

UPDATE: OpenGL output worked in MPlayer! No more pixelated DVDs, yay! Now, the problem with less priority is that OpenGL output flickers in Compiz (just like Xv, and unlike X11). If anyone knows how to get rid of flickering in Compiz *for OpenGL output*, please post! Thank you!

UPDATE2: OpenGL flickering removed in full screen by checking Unredirect Fullscreen Windows in Compiz preferences. See [http://ubuntuforums.org/showthread.php?t=762636]("http://ubuntuforums.org/showthread.php?t=762636")

---

### Post by darkshado on 2008-05-10
I try every think say here and nothing change. Same pixeled problem for films! :/ My ATI card its a X1650 pro AGP, i use fglrx to.

---

### Post by alexei.colin on 2008-05-10
I'm no expert, but maybe something useful will popup from the discussion. Which players did you try and with what output setting (e.g. Xv, X11, OpenGL)? 
Do you have Compiz enabled (Preferences->Appearance->Effects: not none)? If yes, did you try everything in Metacity?

---

### Post by darkshado on 2008-05-10
ok i tested with "mplayer" with OpenGL vidéo out its working fine no pixeled image only the flickering when the screen is at 1:1 but in fullscreen no problem! Thanks for the issue at the moment! ;)

---

