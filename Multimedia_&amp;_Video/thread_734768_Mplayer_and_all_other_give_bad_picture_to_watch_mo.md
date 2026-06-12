---
title: "Mplayer and all other give bad picture to watch movie."
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by cyntek on 2008-03-25
Okay, Hello all. Well Im new to ubuntu and I have been experiencing bad picture quality while playing a movie in all formats: .vob,avi,wav,dvd, I here sound but all I see is vertical lines and no image of the movie. Now I have installed mplayer,totem,vlc, and movie player. The codecs I have installed Klite codec pack, gstreamer and some others but i cant remember from the top of my head. However, this picture started when installed, nero, ffmpeg,? Is there a way to fix this?

[IMG]http://imageupload.com/out.php/i90753_Screenshot.png[/IMG]

---

### Post by uberlube on 2008-03-25
You need to install the restricted codecs from the repositories. Just do a search fot 'restricted' in synaptic and install the appropriate one (I use Mint so all the restricted extras come pre-installed and i never have to find them, so Im not entirely sure what the file is called)

---

### Post by uberlube on 2008-03-25
This will explain everything:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by cyntek on 2008-03-25
That's great, but this just recently happend and earliar today i was able to view all my movies is all the formats in which are playable. why is this happening now?

---

### Post by uberlube on 2008-03-25
If you didnt install the restricted formats then it was bound to break sooner or later. If you do have them installed then it may have something to do with your graphics driver. Just speculating though.

---

### Post by cyntek on 2008-03-25
well, I'm taking your solution and installing them to see if it will fix my problem.

---

### Post by cyntek on 2008-03-25
well, I have to say .... it didn't work!!

---

### Post by uberlube on 2008-03-25
If after you install them it still doesn't work then do a quick reboot and try again.

---

### Post by cyntek on 2008-03-25
reboot is underway, brb

---

### Post by uberlube on 2008-03-25
Also if you are trying to play a DVD, which it looks like you arem then you need to activate DVD playback.

---

### Post by uberlube on 2008-03-25
install libdvdcss2 from repos. that will activate DVD playback.

---

### Post by cyntek on 2008-03-25
okay, the solution was to "reboot" and now it works fine. However, you mentioned that if I were to play dvd, I would need to enable "dvd playback"?

---

### Post by uberlube on 2008-03-25
yup, check out my last post and grab that file.

---

### Post by uberlube on 2008-03-25
also install :
libdvdnav4
libdvdread3

---

### Post by cyntek on 2008-03-25
I believe I installed it already when i was installing mediubuntu.

---

### Post by uberlube on 2008-03-25
k well you should be good to go then. Hope this got it all working.

---

### Post by cyntek on 2008-03-25
Yes, It did, I would like also say " Thank You" for the help and quick response. However, I have one other question. How can I convert Avi to cd-r to playback on a standard dvd player?

---

### Post by uberlube on 2008-03-25
Grab devede. You may need to install the patch if your dvds have messed up noise though, but this doesnt happen to everyone. If it does just google 'devede patch' and it should take you to where you need to be.

---

### Post by uberlube on 2008-03-25
Just a tip too that you may not know, if you want to thank people, the best way is to click on the ribbon with the star in their posts. (not that a verbal isnt sufficient :))

---

### Post by cyntek on 2008-03-25
Well, I guess that's all for now, really, Thanks for the quick response.

---

### Post by uberlube on 2008-03-25
np :)

---

