---
title: "Play Video Games using a Tuner Card"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by jazee on 2007-06-20
I'm more or less just trying this out for fun to see what It can do but I have a PVR-150 Tuner Card installed in my Feisty box and what I am trying to do is use the Composite input to connect my GameCube to it to play it on my screen. What I am having trouble with is getting something to work to play the Video and Sound stream with out having a massive Video delay. I have messed with it in MythTV as well as VLC. From what I have found MythTV will not let you turn off the Video Recording Buffer and VLC I can't seem to figure out how to have it just stream it to the screen with out its own buffer causing the delay.

Does anyone know of something that will let me do this and maybe let me record it as I'm playing with out such a long delay.

---

### Post by dfreer on 2007-06-20
I'd try this:
Plug Gamecube into 2-way splitter. Have one end go into TV (so that you can play without lag), and the other end into your PC so you can record it. Of course, you'll probably have to hook up your Gamecube to the tv each time you want to play, and then hook your mythtv up when you want to use it. You could get a RCA selector so you can plug them both in and switch between the two when you need to. Hope this made sense!

EDIT: diagram:

```

GC -> splitter -> TV
           |
           V
           PC

```

---

### Post by jdeslip on 2007-09-02
I am really interested in the answer to the original question - i.e. get rid of the lag on prv 150 in linux in order to play video games.  

Here people seem to have found an answer on windows:  [http://forums.techguy.org/hardware/590527-solved-ps2-pc-lagging-pvr.html](http://forums.techguy.org/hardware/590527-solved-ps2-pc-lagging-pvr.html)  - can I do something similar on linux in vlc or mplayer?

---

### Post by jdeslip on 2007-09-06
I figured out a solution.  The key is to read from rawvideo off your tuner card and not from the mpeg stream.  I wrote a script that allows me to play video games from my Playstaion through my tuner card with now lag.  I have a pvr-150 with ivtv driver.  Here it is:

```

v4l2-ctl -v width=720,height=480
v4lctl setinput "Composite 1"
ivtv-tune -c1
aplay -q --buffer-time=100 -f dat /dev/video24 &
mplayer -rawvideo format=hm12:h=480:w=720:fps=29.97 -nocache -demuxer 26 /dev/video32 -framedrop -vo xv -monitoraspect 16:10 -aspect 4:3
killall aplay

```

I hope this helps you (the mplayer command should all be one line).

---

### Post by munchieattack on 2008-01-10
Hello, I am trying to play my wii through a Hauppauge WinTV HVR-1800 on Windows Vista Home Premium. I have Media Centre, which wont play it. I have WinTV which plays it but with major lag. I also downloaded VLC which plays it with a 1 sec delay. Does anyone know how to eliminate delay all together?

Thanks.

---

### Post by jdeslip on 2008-01-10
Well, I succeeded in getting rid of the lag in linux by using the above script.  So, a 'simple' solution would be for you to erase windows, install linux and use that script... ;) JK - I think if you google the problem you might find a program for windows that reads the rawvideo from the card instead of the mpeg stream... Good luck other than that, though.

---

### Post by munchieattack on 2008-01-25
Okay, so i've decided to go the linux route. I can't seem to find a good windows solution. I have a Hauppauge PVR-1800. People tell me you can run both linux and windows, just choose one at startup.  I've always wanted to play with linux so I'm going to take this as an opportunity. If you could help me out with this it would be great. At this point I know nothing about linux and what I would have to do to get this working.

Thanks

---

### Post by jdeslip on 2008-01-25
Glad to hear you are giving linux a shot.  I think walking you through an installation on the forum would be a bit painful any member, however.  I suggest you follow a couple guides:  [http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)  (is an example one - but not sure if they talk about dual booting).  

When you have ubuntu up and running on your PC, post back in this thread and I'll see if I can help you play your video game console.

---

### Post by Rand Som on 2008-02-18
Hey jdeslip!  Thank you VERY much for the script, works great.  I have a quick question tho.  Are you getting audio?  With that script, I get no audio.  The -ao alsa option doesn't work, so I'm kind of confused.  Thanks again!!

---

### Post by RuarriS on 2008-02-18
I use TvTime in linux, with a pcHD5500 card. I plugged my Wii into the composite cable, and it plays without lag as far as i can tell. The resolution isn't that great though..

---

### Post by jdeslip on 2008-02-18
RuarriS - your card does not have this issue because it does not convert the video to mpeg.  This conversion is very nice feature for mythtv/tvtime, but causes the lag for video games.  

Rand Som - I had to change my script a bit when I upgraded from Fedora 7 to 8.  I don't know if it will work on ubuntu.  But, I changed the aplay line a bit - perhaps it will work for you now?

```
v4l2-ctl -v width=720,height=480 -d /dev/video1
#sudo rmmod ivtv
#sudo modprobe ivtv
#v4lctl setinput "Composite 1"
v4lctl -c /dev/video1 setinput "Composite 1"
ivtv-tune -c1 -d /dev/video1
aplay -q -f dat /dev/video24 &
mplayer -rawvideo format=hm12:h=480:w=720:fps=29.97 -nocache -demuxer 26 /dev/video32 -framedrop -vo xv -monitoraspect 16:10 -aspect 4:3
killall aplay
```

I am not sure what you meant by -ao alsa - perhaps you meant you put that in the mplayer line?  This would not work because audio is /dev/video24 and video is /dev/video32.  Try the aplay command above.

---

