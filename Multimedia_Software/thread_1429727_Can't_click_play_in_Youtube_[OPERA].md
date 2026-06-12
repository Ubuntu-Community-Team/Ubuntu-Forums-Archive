---
title: "Can't click play in Youtube [OPERA]"
date: 2010-03-14
forum: Multimedia Software
---

### Post by incus on 2010-03-14
Hey,

I've recently installed Opera 10.10 and the newest flashplugin. I have a problem with youtube videos: whenever I stop playing, and then click 'play' again, nothing happens. Sometimes I cannot start them at all, especially those embedded on other sites. Everything seems to be ok on Firefox or Chrome.

If anyone is interested in what it looks like, I can make a video.


Thank you.

---

### Post by J_Stanton on 2010-03-14
how did you install flash?

---

### Post by exploitations on 2010-03-14
I have the same problem, but in Firefox..
Its only YouTube and a lot of other things that wont respond when you click on it..
Or, when you right click and go to settings it wont work..

Everything works fine on my laptop, but on my desktop it wont work.. 

It was working just fine before I set up both my monitor

---

### Post by incus on 2010-03-14
Thanks for your responses.

I've tried with two different versions of flashplugin, both installed manually and with apt-get.

Very strange...

(BTW, I can go to settings with no problem)

---

### Post by exploitations on 2010-03-15
Another thing I noticed, was that I can't use my webcam and microphone to do things like video chatting. I'd like to get this fixed... or is it not possible?

---

### Post by incus on 2010-03-15
After switching from compiz to metacity, everything works fine.

I found this:
[https://bugs.launchpad.net/compiz/+bug/410407](https://bugs.launchpad.net/compiz/+bug/410407)

but I have 32bit...

---

### Post by bro brian on 2010-03-17
I have a similar problem with Youtube, and this has been racking my brains for a few weeks now. I am running Firefox 3.5 (the latest as of March, 2010). While on Youtube, I can't use the cursor to either pause the video, nor operate the slide (to the right of the pause/play).
*
Note: This isn't a problem with ALL videos on Youtube - - My cursor will work on a few videos. Also, I can share a Youtube video on Facebook, and the cursor will work on Facebook where it won't on Youtube.
*
I've went as far as to un-install firefox & Adobe flashplayer, re-install flashplayer, and then re-install firefox. Also un-installed gnash & gnash-common, and anything else I thought may be interrupting Youtube's flashplayer protocol. There was no difference.
The only thing I can think of is that the problem is on either Youtube's end - or the videos I'm having problems pausing are in a different format or something.

---

### Post by andyhelloween on 2010-03-17
Same thing on this end, but not only with Youtube but other pages with embedded flashplayer. I'll take a look at the bug pointed by incus.
It's happening with Firefox 3.5 and Chrome, and running Compiz.

Cheers,

---

### Post by bro brian on 2010-03-17
> **andyhelloween said:**
> Same thing on this end, but not only with Youtube but other pages with embedded flashplayer. I'll take a look at the bug pointed by incus.
It's happening with Firefox 3.5 and Chrome, and running Compiz.

Cheers,
Yes, that was it. I switched back (from Compiz to Metacity), and everything worked as it should. Now, we're getting somewhere!
*

---

### Post by bro brian on 2010-03-18
> **incus said:**
> After switching from compiz to metacity, everything works fine.

I found this:
[https://bugs.launchpad.net/compiz/+bug/410407](https://bugs.launchpad.net/compiz/+bug/410407)

but I have 32bit...
[B]How did I overlook this post? I'm running 64 bit, so Compiz is doing it with both 32 bit & 64 bit.
      [/B]So far (mentioned on Post #74 of the link) This is the workaround that worked for me:
-
"Hold down the right button. Keep holding it down. Then left click somewhere on the page to get rid of the context menu. Now, still holding the right button, left click on flash buttons, etc. It should work."
-
This problem & workaround has also been posted on the forum here:
[http://ubuntuforums.org/showthread.php?t=1275500&page=2](http://ubuntuforums.org/showthread.php?t=1275500&page=2)

---

