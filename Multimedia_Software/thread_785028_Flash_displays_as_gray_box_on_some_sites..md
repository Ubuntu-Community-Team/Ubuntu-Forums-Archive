---
title: "Flash displays as gray box on some sites."
date: 2008-05-07
forum: Multimedia Software
---

### Post by mistersam on 2008-05-07
I'm having real trouble with the flash plugin. I am currently using the non-free adobe plugin. When I surf to some important websites that use flash, all I get is a big gray block.

ie:
miniusa.com
toyota.com


However, some other websites work perfectly:

youtube.com
2advanced.com


I have tried uninstalling and reinstalling many times in many different ways, but I still get the big gray box. Does anyone have a solution?


PS: Running FX3 Beta 5 on Hardy... althought I've tried other brothers with no luck.

---

### Post by robog2 on 2008-05-22
I have the same situation here, except that this happens for me with all sites.

EDIT: The flash will not always go straight to gray.  Instead, sometimes it will load, and then turn gray after a second or two (it will always turn gray though).

---

### Post by mistersam on 2008-05-22
This also happens to me somtimes: renders, then goes gray.

---

### Post by robog2 on 2008-05-26
Bump.  Any ideas?

---

### Post by otwr on 2008-05-26
I had this, intermittently. Also in konqueror, flash would occasionally hang the whole browser (for that, I would just do "pkill nspluginviewer" and that would fix it). Following the instructions in the sticky seems to have fixed both:

sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport

(edit) hm, crud. I spoke too soon it seems; Scrabulous has gone back to being a gray block.

---

### Post by robog2 on 2008-05-27
This behavior seems to have stopped, for me at least, upon installing and using OSS4 using these instructions:

[http://ubuntuforums.org/showthread.php?p=4874981](http://ubuntuforums.org/showthread.php?p=4874981)

In addition to the disappearance of the gray-box behavior, I no longer have the flash/other sound conflicts I had before (where only one source would play at a time), and everything (firefox included) seems to run slightly faster.  Good luck!

EDIT:  I was wrong.  The behavior is still present, though not as often as before.

---

### Post by c0rd3l1a on 2008-07-03
Has anyone figured this out yet? Scrabulous is my main issue. Scrabulous app on facebook and email Scrabulous show up as empty white boxes but if I click on them the board shows up and everything works fine, but solitaire and robot Scrabulous, all I get is a big grey box. No amount of clicking on it brings up a board.

---

### Post by walkeraj on 2008-07-08
Bump.  This also happens to me.  Frequently.

---

### Post by MaindotC on 2008-09-23
Bump - happening to me as well.  I didn't have any problems till I installed the new Mac4Lin theme and added the AWN repository so I could download their .deb, and I tried installing gDesklets to no avail and then installed Screenlets and some Screenlet extras.  I'm not sure if its related to that but flash was working fine up until then.

---

### Post by MaindotC on 2008-09-23
Problem solved per [this thread](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=908908).  There's a problem displaying more than one tab that has flash content.  Just keep one tab of flash open at a time and you should be good.

---

### Post by to young on 2009-08-15
Bump.   One tab per firefox window does not solve the problem.   sometimes I have to refresh page three times before I see the video.  

Please Help.

---

### Post by CarlC4 on 2009-08-16
I've tried everything, nothing works. :mad:

---

### Post by oboedad55 on 2009-08-16
> **CarlC4 said:**
> I've tried everything, nothing works. :mad:

Same problem here with Hardy, okay in Jaunty. I get a grey box with a large arrow in the middle. I can get audio but no video. Oh, Opera works fine, it's just Firefox.

---

### Post by teflashfire on 2009-08-16
I had this problem for a long time; the solution for me was a classic.

Ensure that you are using the latest version of Adobe flash player. You can find the latest version, as well as installation instructions. This did it for me, I can't guarantee that it will work for you, and I'm sure many of you have tried this already.

---

