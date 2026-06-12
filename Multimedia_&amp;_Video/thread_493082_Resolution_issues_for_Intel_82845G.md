---
title: "Resolution issues for Intel 82845G"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by ironfistchamp on 2007-07-05
Hey all,

Having major problems with a Intel Corporation 82845G and a 19" Wide screen monitor. I can only get 640 x 480. I tried changing stuff in xorg.conf but I totally messed it up. I can't now get a GUI. I would change it back but I cannot see the current line in the terminal. Also using dpkg-reconfigure gives me a really distorted view so I can't actually change anything.

I tried using both the i810 and the intel drivers but neither of them helped.

Can anyone give me any help?

Thanks


Ironfistchamp

---

### Post by moore.bryan on 2007-07-05
[I]you can try installing 915resolution...
```
sudo aptitude install 915resolution
```
[/I]

---

### Post by ironfistchamp on 2007-07-06
Yeah I did try that but was really unsure on how to use it. I put a line similar to that in the readme (but suitable for the res we wanted) in the file specified but that didn't do the trick.

I also tried following advice from this post [Ubuntu Forums - View Single Post - screen resolution]("http://ubuntuforums.org/showpost.php?p=151596&postcount=4") but that didn't help either. Just broke Xorg to the point where I had to reinstall. It's odd because everytime I bork the conf file I have to reinstall. Even restoring a backup or re-editing the file to put it back won't work.

Any other ideas?

Thanks

Ironfistchamp

---

### Post by moore.bryan on 2007-07-06
*really?  that is weird... have you checked out the [modeline generator]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl") and putting that into your xorg.conf? *

---

### Post by ironfistchamp on 2007-07-07
Thanks for the link. Where exactly would I put that in the xorg.conf?

---

### Post by ironfistchamp on 2007-07-07
OK this is really getting to me now. I tried the modeline thing. Killed X. I went to the terminal, stopped X, used 915res to select what I wanted. It said it worked. Started X and, would you look at that, we are still in 640x480. What the hell is going on with this thing?

Anyone else got any ideas?

---

### Post by ankush on 2007-07-07
I m having the same problem if i set my resolution to higher my screen starting blinking ..goes blank for a moment and comes back ...some one plzz help i tried xorg.conf file modification but didnt help ...is there any other method ..driver or setting

---

### Post by moore.bryan on 2007-07-08
> **ironfistchamp said:**
> Thanks for the link. Where exactly would I put that in the xorg.conf?
*at the end of your "screen" section.  just keep trying things... i know it's frustrating.  it took me almost a month to get my monitor working correctly with breezy, but sticking to it worked out, eventually.*

---

### Post by ankush on 2007-07-10
hey thanks i tried installing intel drivers and it worked this is a nice link for the same ..try using it ...i hav intel 82845

[http://ubuntuforums.org/showthread.php?t=324379&highlight=installing+intel+extreme+graphics+on+linux](http://ubuntuforums.org/showthread.php?t=324379&highlight=installing+intel+extreme+graphics+on+linux)

---

