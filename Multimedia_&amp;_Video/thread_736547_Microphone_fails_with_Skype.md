---
title: "Microphone fails with Skype"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by tonyn999 on 2008-03-26
I have seen other older posts regarding mic problems with Skype.
My problem is showing up on a Thinkpad X61S running the lastest Hardy Heron beta.

The microphone is turned all the way up in the alsa mixer.

My sound card is an Intel 82801H.

I suspect that the ALSA driver may need to be recompiled to fold in changes made to other related code.  But this is little more than a guess.

My system is dual boot, and when I bring it up with XP the mic works fine with skype.

---

### Post by spych102 on 2008-03-27
I know it's an obvious question, and I'm sure that you have checked this but is the microphone icon on mute?:)

---

### Post by tonyn999 on 2008-03-27
Unfortunately, the mic is definitely not on mute.

---

### Post by xc3RnbFO8P on 2008-03-27
You could try this:
> > Ok, found something else that works... If I open gnome-volume-control
> and go to the third tab (options) and change the Input source to Line
> (it was Mic), close it and then open again and change back to Mic, and
> finally close, I try Skype and works. After a boot and before doing
> this, I have a dead mic. This time I didn't even touch Ekiga.
>
> Any ideas? Works for someone else?

That is exactly what I do to get the microphone working here. I seems odd to
de-select and then re-select mic on as input source but, then again, it does
the trick :-)



---

### Post by yahoo on 2008-03-28
I have just been playing around to get my microphone working also.
I opened the Volume Control (System>Preferences>Volume Control), selected Edit>Preferences, and scrolled down to tick Mix (as well as trying a few others).
Back on the Volume Control, chose the Switches tab, and ticked Mix.
I am sure it was Mix that made the microphone work.

I have only tried the Skype test call, and it wasn't 100% clear - a bit choppy, but it made my inbuilt microphone and a line in mic both workable.

Cheers
Yahoo

---

### Post by grand_master on 2008-04-05
I had the exact same problem with the internal mic and Skype on my X61s running Gutsy. Believe or not, now it's working! I found the solution on notebookreview.com:

"I got it fixed.

Go to the Volume Control (gnome-volume-control) > Edit > Preferences > check the Capture box > Close. Next go to the Recording tab and set Capture to max (and unmute it if it's muted)
Then went to the mixer's Options tab and where it said input source and set them both to internal mic.
now skype works just fine."

Original post: [http://forum.notebookreview.com/showpost.php?p=2936055&postcount=4](http://forum.notebookreview.com/showpost.php?p=2936055&postcount=4)

I've taken screenshots on all four tabs in the gnome-volume-control, so you can see for yourselfs what my exact settings are.

---

