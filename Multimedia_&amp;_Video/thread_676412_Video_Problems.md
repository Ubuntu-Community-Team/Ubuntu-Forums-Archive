---
title: "Video Problems"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by gtkourounis on 2008-01-23
Hey there, installed 7.10 on my desktop again and have all the codecs necessary for videos to run. I have some avi files that i want to see using VLC media player, and when i open the file, the VLC goes black. I hear the audio and I see a bit of the video in the very beginning (maybe only one frame), then it turns black. However if i go to fullscreen the video and the audio show up normaly. 

Do any of you have a clue to what might be causing this problem?

thanx in advance :)

---

### Post by chewearn on 2008-01-23
You might be able to get some clues, by looking at VLC log.  First, run vlc from terminal and see if there are any message.  Second, you can look into VLC menu > View > Messages.

.

---

### Post by gtkourounis on 2008-01-23
```

neudeck@neudeck-desktop:~$ vlc
VLC media player 0.8.6c Janus

** (.:6017): WARNING **: Invalid borders specified for theme pixmap:
        /home/neudeck/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Frame-Gap/frame1.png,
borders don't fit within the image

** (.:6017): WARNING **: Invalid borders specified for theme pixmap:
        /home/neudeck/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image

```

does this help? btw i dont understand what the borders problem is :/ which is probably what the problem is about.....

---

### Post by gtkourounis on 2008-01-23
changing the them doesnt help me 

```

neudeck@neudeck-desktop:~$ vlc
VLC media player 0.8.6c Janus
neudeck@neudeck-desktop:~$ 

```

VLC opened normaly yet the same problem occured, could emerald be the reason for the problem?

---

### Post by chewearn on 2008-01-24
How about VLC Menu > View > Messages ?

---

### Post by gtkourounis on 2008-01-24
its empty, nothing shows up. 

btw this isnt only a vlc problem, i am having the same exact problem with any other media program that i use to see a video.

what is weird is that it works fine when its on full screen mode :/

---

### Post by eye208 on 2008-01-24
> **gtkourounis said:**
> its empty, nothing shows up.
Did you open the message view before opening the file?

---

### Post by chewearn on 2008-01-24
> **gtkourounis said:**
> its empty, nothing shows up. 

btw this isnt only a vlc problem, i am having the same exact problem with any other media program that i use to see a video.

what is weird is that it works fine when its on full screen mode :/

Since it's a common issue across all media players, it could be a problem with your video driver or xorg set-up instead.  What video card do you have?

-

---

### Post by gtkourounis on 2008-01-24
ATI Radeon 9550 256 mb

installed all the drivers necessary through envy

---

### Post by chewearn on 2008-01-24
I'm not familiar with ati issues, never got myself an ati card before; a quick search on google turned up this as the issue closest to yours:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/55646](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/55646)

Did you by any chance have a dual head set-up?

---

### Post by Speedoo on 2008-01-24
Have you tried playing your avi's with gxine?  I've occasionally found videos that totem and vlc don't like, and gxine seems to handle them.  Just a thought....

---

### Post by gtkourounis on 2008-01-24
> **eye208 said:**
> Did you open the message view before opening the file?

What was i thinking???? lol

here is the message windows



```

main warning: late picture skipped (14809)
main debug: decoded 96/100 pictures

```

installing gxine now....   and it has the same problem :(

---

### Post by eye208 on 2008-01-24
OK, obviously there is a bug in the display driver handling the hardware video overlay (aka XVideo). There are two possible workarounds:

1. Switch the driver to OpenGL overlay. This will make video display on an OpenGL texture. That's almost as good as XVideo, but it doesn't work with Totem-GStreamer. However VLC and MPlayer will work fine if you configure them accordingly.

2. Switch your media players to software rendering (aka X11). This is the worst solution because anti-aliasing will be gone (you will see pixels in fullscreen), but it always works, no matter what driver you are using.

I'd suggest you try the OpenGL option first. "sudo aticonfig --ovt opengl" will write the setting to your X.org config file. You need to restart X.org once to apply it. Then configure VLC to use OpenGL overlay (Settings --> Preferences --> Video --> Output Modules). The "-vo gl2" option will do the same thing for MPlayer.

---

### Post by gtkourounis on 2008-01-24
Thank you eye208 for the help, and i am sorry i missed your first post... i saw it a bit late.
thanks to you too altavista
the video works just fine now :D:D:D:D:D:D:D:D

---

