---
title: "Any good video converter?"
date: 2009-09-26
forum: Multimedia Software
---

### Post by jahgamer189x on 2009-09-26
Is there any good video converter that can convert a variety of file types to other file types in Ubuntu?
Or any one that works well in wine?
I was using xilisoft hd converter (worked great) in wine a while ago but I'm using a more updated wine and that doesn't seem to work with xilisoft.

---

### Post by Jose Catre-Vandis on 2009-09-26
Mencoder (Mplayer)
FFmpeg

---

### Post by HappyFeet on 2009-09-26
Winff is the gui frontend for ffmpeg. Try that.

---

### Post by dr_dred5 on 2009-09-26
I've been using Handbrake from [http://handbrake.fr/](http://handbrake.fr/)

It has an easy to use Gui, lets you choose what video and audio codec to use, supports subtitle, ripping and what I like is that it will let you choose the size of your final video and set the quality automatically.

Oh yeah, it's also quite fast without loss of quality.

I believe it was originally designed for Mac, but has been re-tooled for Linux.

Cheers!

---

### Post by arnab_das on 2009-09-29
i have tried many. handbrake doesnt allow resolution changing, so thats a huge negative.
avidemux is good but the interface can get a bit confusing.
devede is almost like covertx for windows. and its worked fine for me.

winff is also good (i prefer this as devede uses divx and not xvid).

however i am getting this strange error ever since i installed the latest version of ffmpeg. the pic below is of winff.

[IMG]http://i692.photobucket.com/albums/vv287/frnd08/Screenshot-3.png[/IMG]

---

### Post by paul.gevers on 2009-09-29
> **arnab_das said:**
> however i am getting this strange error ever since i installed the latest version of ffmpeg. the pic below is of winff.

If you go to the options -> Settings menu and look at the linux tab, what is the path given to ffplay? And do you find that path on your computer?

Where did you get that latest version? Please also consider reporting such issues at the  [bugtracker of winff]("http://code.google.com/p/winff/issues/list").

---

### Post by arnab_das on 2009-09-29
> **paul.gevers said:**
> If you go to the options -> Settings menu and look at the linux tab, what is the path given to ffplay? And do you find that path on your computer?

Where did you get that latest version? Please also consider reporting such issues at the  [bugtracker of winff]("http://code.google.com/p/winff/issues/list").


no i cant find it in the folder mentioned! so what do i do now?

---

### Post by paul.gevers on 2009-09-30
> **arnab_das said:**
> no i cant find it in the folder mentioned! so what do i do now?

Sorry, my mistake. Menu should be Edit -> Preferences -> Linux -> Path to FFPlay Executable

---

