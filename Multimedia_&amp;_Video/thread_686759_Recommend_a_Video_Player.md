---
title: "Recommend a Video Player?"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by sindyr on 2008-02-03
I have a few simple requirements:

1) It must have Full Screen Mode
2) It must have some kind of indicator of where you are in the video file, like a bar with an indicator that moves along the bar as the file is played.
3) I must be able to click on any point on the bar and have the playback jump to that spot.  Note:  I don't want to drag to that spot, I want to be able to do a simple single click on the bar and have the video jump to that spot in the video.  For example, if I click in the middle of the bar, the video jumps to the middle of the video.

Any suggestions?

---

### Post by jrusso2 on 2008-02-03
I use Kaffeine but VLC works too.

---

### Post by Aquaman420 on 2008-02-03
VLC or Smplayer are good.

---

### Post by sindyr on 2008-02-03
OK, very frustrated right now.

Either I am not doing it right, and I'm the moron, or

Whoever said I should use VLC is a moron for not taking the time to actually READ what I was looking for before recommending it.

VLC does NOT let you "click-to-skip" - requirement 3 above.

Am I not being understood?  Are my requirements difficult to grasp?  Did I explain them poorly?

Let me try again.

I am looking for a media player that
-can go fullscreen
-while in fullscreen has a bar indicating where in the playback we are, from beginning to end, and
-when you click on the bar of the indicator, jump to start playing at the part of the bar where I clicked.

Make sense?

Will try SMPlayer and Kaffeine - but both of those folks recommended VLC so they may not have had a real grasp on what I was asking for in the first place.

---

### Post by Aquaman420 on 2008-02-03
Smplayer for sure does it.  In options click OSD-seek bar.  Hope that helps.  No reason to get rude and call the people that took time to help you "morons"

---

### Post by Cew27 on 2008-02-03
ok they missunder stood, try not to be to edgy or people wont help ;)

---

### Post by sindyr on 2008-02-03
Sorry if I was too hostile, one of my "buttons" is people who want to feel good by helping people, but don't make an effort to actually try to help or read the full post.  It makes me feel like I am not being heard by the people claiming to be helpful.

Anyways, thanks to everyone who really is trying to help.

Now, SMPlayer and Kaffeine both have the requested featues (yay!) *but* the video is oversaturated, like watching it on a TV from 1970.  This is true for both of them.  On the other hand, VLC, Totem, and MPlayer get the tones and video right, but don't have the click on progressbar feature.

Any thoughts?

---

### Post by Aquaman420 on 2008-02-03
My Smplayer looks fine. I use it to watch store-bought dvds  Your problem might be conflicting libraries or frontends.  I would recommend   uninstalling mplayer and installing mplayer-nogui.  Those are the thoughts I have.I think I remember having weird problems when I had the mplayer with the gui installed.  The video output drivers for Smplayer and Kaffeine may be wrong also. They can be changed in the preferences section Those depend on what graphics card/driver you have.  I use XV but yours maybe different.  I have run out of time, but will check back later tonight when I get back from dinner. Good luck in the meantime!

---

### Post by rvm4000 on 2008-02-03
> **sindyr said:**
> Now, SMPlayer and Kaffeine both have the requested featues (yay!) *but* the video is oversaturated, like watching it on a TV from 1970.  This is true for both of them.  On the other hand, VLC, Totem, and MPlayer get the tones and video right, but don't have the click on progressbar feature.

SMPlayer is a front-end for MPlayer so if the latter display the image correctly, SMPlayer should do the same. Go to Preferences and try selecting a different video output driver, or activate the software equalizer in the video tab.

Alternatively you can open the equalizer (Video -> Equalizer) while playing a file, and adjust it until the image is good, and then click on the button "Set as default values", that will make to use that adjustment as default for all videos.

---

### Post by Bablefish on 2008-02-03
I admit I have had problems both with VLC and MPlayer. I just use Kaffiene

---

### Post by sindyr on 2008-02-03
Tweaking the Video Equalizer settings seems to fix it - I have to lower the Saturation and Brightness.

Thanks! :)

---

### Post by disturbedite on 2008-02-03
smplayer all the way.  (i personally use kaffeine for dvds with menus tho, since mplayer doesn't support menus).

---

### Post by rvm4000 on 2008-02-03
> **disturbedite said:**
> ...mplayer doesn't support menus).

I compile quite often mplayer from svn and in the last weeks they've made great improvements on support for dvd menus. Not usable yet, but maybe in the near future we could have good news.

---

