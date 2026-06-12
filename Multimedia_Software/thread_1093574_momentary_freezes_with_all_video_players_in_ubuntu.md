---
title: "momentary freezes with all video players in ubuntu 8.10"
date: 2009-03-11
forum: Multimedia Software
---

### Post by icemime on 2009-03-11
(sorry if this had already been posted)

I installed 8.10 on my Acer 9420 laptop recently and i've got everything working fine ecxept video seems to freeze for a few seconds randomly. I've tried different players, VLC, Kaffiene, Totem, Smplayer and it's the same thing with all of them.
i have nvidia geforce 7300 and i've tried all 3 drivers i can find in the driver repository but that doesn't change anything.
i've seen posts that people are having problems with VLC player, but with me it's all players:(

does anyone have this problem or know a fix?

---

### Post by kidux on 2009-03-11
Try turning off the desktop effects. I was having a similar problem and it was compiz. Do a search on my username and you should be able to find the thread with the things to try.

---

### Post by icemime on 2009-03-11
thanx i'm trying that out now, is there a single command i can use to turn off all desktop effects and to turn them back on, or should i just unchek the effects i set in the compiz manger?
--------------
it seems to be working fine now, thanks alot man, i also installed compiz icon so that i can just turn  compiz off and on with a click:)

---

### Post by icemime on 2009-03-12
nope spoke too soon.. still getting momentary freezes:s.. don't get it... have no idea what to try next.. don't want to give up on intrepid:s

---

### Post by eskararriba on 2009-03-18
hey, 

I've got the same problem, and it's seriously starting to rack my nerves. and can't watch DVDs, can't watch .avi - well, I can watch videos at all. I'm using the nvidia 177 driver, but the problem is the same when I use 173; 
now, I followed the steps in this thread: [http://ubuntuforums.org/showthread.php?t=1075503](http://ubuntuforums.org/showthread.php?t=1075503), but I don't really get the point cause the test screen looks always the same, whether I use "autodetect", "no XV" or "X11..."

disabling graphic effects isn't REALLY an option, don't you think? I mean, I just bought this computer, so it should be possible to watch a video and have the mouse shadow enabled... 

thanks for further help!

---

### Post by kidux on 2009-03-18
Try using the 180 series of drivers.
```
sudo apt-get install nvidia-glx-180
```

---

### Post by eskararriba on 2009-03-20
okay, thanks kidux - installed it and now I ll try to watch something

---

### Post by eskararriba on 2009-03-20
with the 180 driver, I could watch the video perfectly, without any interruptions. 
but unfortunately, after rebooting, I could only get to the login-screen. after that, the screen turns black, or turns off. I suspended the computer, and when I logged in again, the screen came back. what can I do about THAT?

---

