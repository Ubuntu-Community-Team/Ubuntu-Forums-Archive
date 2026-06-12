---
title: "[SOLVED] upgrade to .21 and keybindings no longer work"
date: 2008-03-17
forum: Mythbuntu
---

### Post by harlee188 on 2008-03-17
I mistakenly upgraded to mythtv .21.
I was doing an update and did not realized I selected "ALL"

Any way, now some of my key bindings do not work.
This is from my remote MCE, and from my keyboard.

I can not click on:
 Media Library >  "watch video"
Optical Disks > Play DVD
Optical Disks > Play VCD
Optical Disks > Import DVD

And probably others.

How do I correct this? Does the upgrade make a backup copy of the keybindings.
I do not know what file this is, or what the settings should be.

---

### Post by larsolav on 2008-03-17
Maybe this post may help: [http://ubuntuforums.org/showthread.php?t=722960](http://ubuntuforums.org/showthread.php?t=722960)

> to fix the mythvideo problem if you haven't fixed it already:

sudo aptitude remove mythdvd

sudo aptitude install mythvideo

---

### Post by harlee188 on 2008-03-17
Wow...
First why would I uninstall mythDVD?
And then reinstall mythvideo?

And why would this fool with my key bindings?

---

### Post by larsolav on 2008-03-17
Sorry, guess I didn't get your real problem. I just thought you weren't able to go to  Media Library -> watch video and you weren't able to watch DVDs, which there are a lot of posts on on this forum (e.g. [http://ubuntuforums.org/showthread.php?t=722756](http://ubuntuforums.org/showthread.php?t=722756) ). 

I am such a noob I have no clue what the keybindings are, so sorry to have sent you on a wild goose chase. :-\"

---

### Post by harlee188 on 2008-03-17
I can get to the list screen but when I try to click on "watch video" it does nothing.
Which I am assuming has to do with key bindings.

---

### Post by harlee188 on 2008-03-17
My apologies, you were right!
That was exactly what it was.

Working now!

---

