---
title: "Red Channel suddenly disappeared in videos"
date: 2008-05-05
forum: Multimedia Software
---

### Post by RedRat on 2008-05-05
OK something really odd. Yesterday, when I played any videos, they all appeared normal. Today, however, it appears that the red channel has disappeared from only the video playback. I tried VLC, mplayer, movie player, etc. All the same. I all my still pictures, jpg, etc are all ok and the color is normal. 

I recently (about 5 days ago) updated to 8.04 LTS on my Dell 530n. Other than the red channel being gone, the videos and sound play normally.

Since it worked yesterday, I can't help think that some kind of update might have been pushed out, but normally Synaptic asks whether you want to install the new download.

Any ideas???

---

### Post by luisfcup on 2008-05-08
I am having a similar problem, at first I thought it was a problem with the gstremer but xine and vlc are all the same. I thought that the blue and red channels were swapped, but it also might be a problem with the red channel alone, I can't tell :s
Only happens in video files, regardless of the encoding (I tried with ogg and xvid).

I have an nvidia card and I can get good color if I go to the gstreamer-properties, in the video plugin and select (No Xv), but then the image quality if very poor.

---

### Post by ingrid_ozikem on 2008-05-08
I think I have the same problem. I have a clean install of Hardy 8.04 dual boot with Windows and video in any player (xine/ gstreamer through any of vlc, gxine, mplayer, totem etc etc) has some crazy colors.. I didn't think of it as a channel missing but that's probably the problem. The image just looks like very strangely colored, like you were looking at some sort of color negative or something..


All these videos for me also have a resolution problem. The horizontal lines of pixels seem a little too far apart. It looks like an ancient CRT TV set..

Please help! It's been this way since I installed Ubuntu!

---

### Post by ingrid_ozikem on 2008-05-09
Great, my problem above was solved by this website.

[http://www.mikesplanet.net/2007/05/im-so-blue/](http://www.mikesplanet.net/2007/05/im-so-blue/)

I ran gstreamer-properties and fiddled with the Video Output option.. changing it to X Window System without XV fixed all the color problems for me.. video is good now. 

Not sure why this worked .. gxine still gives me strange colors though.

---

### Post by luisfcup on 2008-05-12
Yes the (No Xv) workaround works for gstreamer, but didn't you notice any decrease in image quality?
The result is the same as if you use the open source drivers instead of the nvidia ones.

By the way, I get the sane result with xine so I think it's not a problem with gstreamer as suggested in the link mentioned.
[http://www.mikesplanet.net/2007/05/im-so-blue/](http://www.mikesplanet.net/2007/05/im-so-blue/)

---

### Post by RedRat on 2008-05-15
> **ingrid_ozikem said:**
> Great, my problem above was solved by this website.

[http://www.mikesplanet.net/2007/05/im-so-blue/](http://www.mikesplanet.net/2007/05/im-so-blue/)

I ran gstreamer-properties and fiddled with the Video Output option.. changing it to X Window System without XV fixed all the color problems for me.. video is good now. 

Not sure why this worked .. gxine still gives me strange colors though.

OK I tried this while VLC was still blue. After the supposed fix, I ran an AVI clip and it was still blue. The only way I can get this to go away is a reboot-restart of the computer then everything is normal. 

Mine occurs after I play a clip in VLC then switch to mplayer, things go blue.  I am running Hardy on a Dell 530N with Nvidia GT8600 card and nvidia driver. 

My conclusion is that the fix may not work.

---

### Post by Gyrotwister on 2008-05-16
Ubuntu8.04, ASUS P5KPL, Intel core 2 duo, GeForce 8600GTS

Same problem here.
:confused: Blue faces in all video formats.

Switching the Nvidia driver off stops it but I want my Compiz to work.

---

### Post by mc4man on 2008-05-18
read here
[http://ubuntuforums.org/showthread.php?t=769209](http://ubuntuforums.org/showthread.php?t=769209)
and here post 4
[http://ubuntuforums.org/showthread.php?p=4930593#post4930593](http://ubuntuforums.org/showthread.php?p=4930593#post4930593)

---

### Post by Gyrotwister on 2008-05-19
Thanks for the links mc4man!  That's got my video playback looking normal again.  

These forums are so big it can be difficult to find what I'm looking for sometimes.

---

