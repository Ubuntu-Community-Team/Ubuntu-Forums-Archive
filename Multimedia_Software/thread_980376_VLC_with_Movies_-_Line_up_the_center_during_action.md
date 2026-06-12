---
title: "VLC with Movies - Line up the center during action scenes."
date: 2008-11-12
forum: Multimedia Software
---

### Post by Roasted on 2008-11-12
Question here... I tried playing a movie on my Ubuntu machine. I have all of the codecs installed and whatnot, medibuntu, etc... but in VLC (I think I remember even noticing this in Windows but I may be wrong) during action scenes when the actors are moving very fast, there seems to be a ripple line horizontally in the center of the screen. My question is, does Totem do this? I'd give it a shot if it wasn't for the fact I'm not home, but I just wanted to ask and get a quick opinion in case anybody else has noticed the same thing.

Thanks!

edit - so upon getting home I was reminded of how... lacking... totem can be in terms of functionality. Constantly freezing whenever I select any of the menus, coupled with the fact I oddly cannot fast forward at all. Imagine having a DVD player with no buttons on it except play, and no remote. What can you do? Hit play. You can't skip the previews. So, totem is out. And not only that, but totem still has the center screen choppy line as well. 

Is there a movie player that projects a clear, solid picture despite high paced action scenes? Also, VLC in Vista Ultimate yields better results than VLC in Ubuntu. *sigh*...

---

### Post by Roasted on 2008-11-14
Can anybody at least attest to what results that you get? It may be something hard to notice without knowing what to look for, but in actiony scenes it's kind of obvious, at least in VLC. Just remember, it's always horizontal. Not shooting up the vertical center. 

Maybe I don't have something configured right? I don't know.

---

### Post by Roasted on 2008-11-16
Here's what it is doing. Keep in mind, it happens really quick, but it happens often enough that you can constantly see it during quick paced sections of whatever I am watching.

This is a downloaded music video using VLC media player. 

[http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=SlashGuitarII.png](http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=SlashGuitarII.png)

---

### Post by L815 on 2008-11-16
It's called Video Tearing. Many of us Intel and Ati graphics guys/girls are having the same issue.

The only fix I found that works is go to VLC settings, set the video output to xVideo, and then look around the advanced options for the xVideo setting and there will be a -1, set it to 1.

---

### Post by Roasted on 2008-11-16
Intel and ATI?

I have a Nvidia 9600 GT. :mad::mad::mad:

Oh, and that is set on the xVideo setting. However, I didn't do the -1 and +1 thing. I can't find it...

EDIT - I've done more research on this since L815 gave me the name of the situation - "Video Tearing." I took the advice of some people on previous posts and disabled Compiz. then, I played Casino Royale (James Bond DVD for those who don't know) through VLC. Bam. Crystal clear. 

At least I know what it is now! But, I guess there's no official fix??

---

