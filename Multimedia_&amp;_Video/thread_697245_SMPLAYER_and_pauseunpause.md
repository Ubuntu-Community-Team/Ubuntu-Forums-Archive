---
title: "SMPLAYER and pause/unpause"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by yochaigal on 2008-02-14
Hello.  In totem I can press spacebar to pause the video I'm watching, and then press it again to unpause it.  In SMPLAYER I have to press P (for previous) to unpause it.  If I press spacebar, it just skips one frame ahead.  Annoying. I've tried every possible configuration in preferences, what gives?

Thanks

---

### Post by rvm4000 on 2008-02-15
Strange, the default behavior is the one you want.

Anyway you can change it: Preferences->Keyboard and mouse. Assign the Space key to the "pause" action (and not "pause_and_frame_step").

---

### Post by yochaigal on 2008-02-17
I tried to set the space bar as Pause, and it doesn't work!   It still pauses and then won't unpause, it just frame skips.  I have to press P in order to play again!
Any ideas?
thanks though

---

### Post by rvm4000 on 2008-02-17
What version of smplayer are you using?

Have you checked there are no conflicts with other actions? (the space is not assigned to another action)

---

### Post by yochaigal on 2008-02-17
This is SMPlayer v. 0.5.62 (svn r418) running on Linux

regardless, it's always done this.  in totem, i can press spacebar to pause AND unpause.  

there are of course no conflicts; look--- none of the regular stuff applies here. Does anyone else have smplayer running successfully with pause/unpause being the same button?

thanks!

---

### Post by mc4man on 2008-02-17
smplayer 0.5.62 (svn r51<eight>) - pause/unpause  works fine with spacebar (was/is the default)
maybe try complete removal - reinstalling

edit: spacebar also works in mplayer the same -  try using mplayer and see if it works - i'm using the latest mplayer compiled from source
I believe there's an mplayer precompiled for ubuntu on the smplayer site  [http://smplayer.sourceforge.net/downloads.php?tr_lang=en](http://smplayer.sourceforge.net/downloads.php?tr_lang=en)

---

### Post by yochaigal on 2008-02-17
I completely removed smplayer (don't worry I know how to do a full uninstall), including deleting my .smplayer folder in my home directory, and the problem persists.  Maybe it has to do with my keyboard?  Like, is my spacebar somehow special? I use a logitech keyboard, pretty standard issue.

regardless, with the default settings it still doesn't work!

thanks

ps i use mplayer, it works fine, i used to use it till i saw smplayer.

---

### Post by mc4man on 2008-02-17
spacebar = pause/unpause should work in mplayer - is that the case?

---

### Post by mc4man on 2008-02-17
missed your ps. - if your using the ubuntu repo ver. of mplayer I'd remove it and either use the one from site i mentioned or compile the latest yourself. It's pretty straightforward and if wanted/needed you can patch dvdread for add. playability
patch thread [http://ubuntuforums.org/showthread.php?t=652528](http://ubuntuforums.org/showthread.php?t=652528)  #10,11

---

### Post by rvm4000 on 2008-02-17
> **yochaigal said:**
> This is SMPlayer v. 0.5.62 (svn r418) running on Linux

Could you try [version 0.6.0rc2](http://downloads.sourceforge.net/smplayer/smplayer_0.6.0rc2_i386.deb)?

There was a bug which was fixed in 0.6.0rc1, althought I don't know if it's exactly the same problem you're having, but I think it's worth trying:

> 
(2007-11-27)
 * If mplayer is compiled with gui support, it seems pause may not work properly. I think this is fixed now, by changing the PAUSE command in input.conf. Should fix bug #1839110.


---

### Post by yochaigal on 2008-02-17
I followed the sourceforge link, removed smplayer and installed the deb.  

works!! i can now pause and unpause with the same key! thanks everybody!

---

### Post by yochaigal on 2008-02-18
I just want to say again how happy I am that this works!

---

