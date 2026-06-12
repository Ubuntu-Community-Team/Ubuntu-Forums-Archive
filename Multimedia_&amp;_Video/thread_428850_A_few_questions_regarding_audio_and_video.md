---
title: "A few questions regarding audio and video"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by Fidelity on 2007-04-30
My first question is regarding audio.

Im currently using a realtek ac97 soundcard because my x-fi doesnt work under linux. I can get 2 channels working proprely but no rears, center, or subwoofer. Is there a certain way to enable surround sound in linux?

Second question.

Is there a way to enable vsync when watching DVD's on linux? I'm really tired of the screen tearing in the player "Kaffiene", using the Xine engine. Is there another player I could use that would solve this problem? I have "Sync to VBlank" enabled in my driver control panel but that doesnt seem to have any effect.

3rd question.

How do I install kiba-dock? I have beryl up and running, but kiba-dock refuses to install for me!

That is all for now :) Thanks.

---

### Post by Fidelity on 2007-04-30
Anyone? Thoughts?

---

### Post by Fidelity on 2007-05-01
no one? :confused:

---

### Post by stchman on 2007-05-01
> **Fidelity said:**
> My first question is regarding audio.

Im currently using a realtek ac97 soundcard because my x-fi doesnt work under linux. I can get 2 channels working proprely but no rears, center, or subwoofer. Is there a certain way to enable surround sound in linux?

Second question.

Is there a way to enable vsync when watching DVD's on linux? I'm really tired of the screen tearing in the player "Kaffiene", using the Xine engine. Is there another player I could use that would solve this problem? I have "Sync to VBlank" enabled in my driver control panel but that doesnt seem to have any effect.

3rd question.

How do I install kiba-dock? I have beryl up and running, but kiba-dock refuses to install for me!

That is all for now :) Thanks.

I did not know that Ubuntu does not support the X-Fi.  Ubuntu supports my Audigy 2 very well.

You will have to double click the speaker in your system tray and add the center and rear speakers.  I had to do this for my Audigy 2 to get surround sound.

As far as your X-Fi, maybe Gutsy will support it in six months.

---

### Post by ronocdh on 2007-05-01
> **stchman said:**
> I did not know that Ubuntu does not support the X-Fi.  Ubuntu supports my Audigy 2 very well.

You will have to double click the speaker in your system tray and add the center and rear speakers.  I had to do this for my Audigy 2 to get surround sound.

As far as your X-Fi, maybe Gutsy will support it in six months.
Unfortunately unlikely. =( I had a friend who was switching to Linux and found out the hard way that the X-Fi isn't supported; good thing is that he is mad about that, and his anger is directed at Creative!

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

---

### Post by emil10001 on 2007-05-03
Are you using the opengl output on kaffiene? If not, try that. 

Also, try some other players, like mplayer (from the command line) and learn it well, "man mplayer," it is one of the most powerful mutimedia players that you will use on a daily basis. There's a lot of stuff that you can do with mplayer that can help you diagnose the problem, serach for the "-vo" option, like "mplayer -vo gl2 -vf pp=lb/l5 file.mpg" (this tells mplayer to use the opengl2 video output, and a couple of deinterlacing video filters). Another couple of things to look at is the config file for kaffiene, which should be hidden in your home directory "ls -a ~", "ls -a ~/.kaffiene/" the file should be called "config". I'd also check out the xine player itself, I like it better than kaffiene, as the gui settings are more in-depth.

Good luck.

-John

---

