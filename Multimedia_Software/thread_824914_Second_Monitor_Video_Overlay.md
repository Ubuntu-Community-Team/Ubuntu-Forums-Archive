---
title: "Second Monitor Video Overlay"
date: 2008-06-10
forum: Multimedia Software
---

### Post by Slaskpelle on 2008-06-10
Hello, 
Just a quick question regarding ATI driver setup. It's all working top with no errors as far as Ubuntu (8.04 x64) goes. I'm running on  a 19" LCD Flatscreen as my primary monitor, and a 32" widescreen TV as my second (Connected Through a S-VHS lead on my ATI HD2600xt). 

Back when I was using XP with this setup, i could have a video playing on my primary monitor in windowed mode, I could even minimize the video and still having it play fullscreen / Maximized on my TV. 
Is there a way to do this with Ubuntu? I've tried different players and different Large Desktop / Clone modes etc, but I can't achieve this, All I find on google regarding this is more people asking the same question without any working answers. 
Surely there's just some option i'm missing in my Xorg.conf ?

Cheers for any tips and hinters.

---

### Post by Slaskpelle on 2008-06-11
Also, please if this can't be done can someone please just let me know, to save me from wasting my time :lolflag:

---

### Post by markbuntu on 2008-06-11
Flash will do that if the video is already playing in your second monitor but the other video players will not with the 8.47.3 (current) driver. The new 8.5 ATI driver is supposed to fix this but I have not tried it yet.

---

### Post by Slaskpelle on 2008-06-13
Ok cheers for the reply, I will give that a go. 
I generally never have anything playing on my second monitor (TV) since it is in a separate room to my computer. However since I live with my girlfriend it's quite nice for someone to be able to do some work on the computer whilst the other one is watching stuff on the TV. I can do this at the moment, but I have to manually drag the player-window to the second screen and maximize it, which makes it a bit confusing later when you wanna watch something on the computer and the player window opens up in the other screen

---

### Post by markbuntu on 2008-06-13
I don't know how you can direct all your full screen video to the second screen. I have never had the need but it would be cool if there was some way to do that. 

The only question is how to word the google search.

---

### Post by firfin on 2008-07-03
Yeah.. give me the word :-)

Seriously tho .. not working for me yet either (although I'm trying using a Nvidia card) Shame that propriety drivers in windows DO let you set it up like that.
But then .. xorg IS infinitely more complex than the combined windows (98 till Vista) video-overlay workings/code, right :lolflag: 


Btw ((off-topic))
I couldn't get that kind of TVout usage working under windows xp either (Trying multiple Geforce 8 Series cards.) Took me some time conferring with NVidia tech support to find out the GF8 series couldn't do it all. I surmised it had something to do with overprotective HDCP-restrictions.

---

### Post by Slaskpelle on 2008-07-18
Hehe yeah I know, that's the original reason why I changed from Nvidia to ATI in the first place, their drivers let you do that. Nvidia shot themselves in the foot by crippling their drivers like that. 
Still no luck setting second monitor fullscreen up though, I assume it's not possible in Ubuntu, or just to advanced / complex for most users to do.

---

### Post by markbuntu on 2008-07-19
I have found that there is a way to do this and it is fairly simple. Something like setting vlc or whatever media player to use screen 1 instead of screen 0. There is also some option in aticonfig I think.....

But it is late, and I have been drinking and playing scrabble...........my memory is somewhat impaired.

---

### Post by vanadium on 2009-09-23
Bumping this issue from over one year ago ...

---

