---
title: "Totem: &quot;Failed to connect stream: OK&quot;"
date: 2008-10-18
forum: Multimedia Software
---

### Post by sicofante on 2008-10-18
Open a movie file with Totem. Move the timeline slider back and forth playfully and sooner or later you'll see this:

"Failed to connect stream: OK"

And the viewport will go black. No picture by moving the slider. The picture will be back when you hit play again, and you'll be able to play with the slider again too. 

What does this error mean?

Is it a bug?

---

### Post by tomas.sprlak on 2008-11-09
Hi, I have the same problem. I can't use totem to play my dvd's, I get this message after 5 sec of playing.

---

### Post by mlissner on 2008-12-07
yeah, me too...arg.

---

### Post by scottuss on 2008-12-27
Same here, BUMP?

BTW guys does your DVD playback work OK with something else such as MPlayer or VLC?

---

### Post by ChibaCityBlues on 2008-12-31
Me too...

---

### Post by vegas588 on 2009-01-01
I have the same problem. It was working before I did the latest update. Has there been any progress on this topic? Does anyone know of a fix or a workaround?

---

### Post by vegas588 on 2009-01-05
I played around with the settings this weekend for Sound and I was able to solve this problem by clicking on System>Preferences>Sound and changed each of the settings on the Devices tab from AutoDetect to ALSA or Advanced Linux Sound Architecture and now DVD movies work.

---

### Post by neorou on 2009-01-06
I have the same problem and error message (dvd failed to connect stream: OK). Then I changed my sound settings to ALSA to see if that solves it for me, and now I get a different message:

Error: could not read from resource

I found this post:
[http://ubuntuforums.org/showthread.php?t=763006](http://ubuntuforums.org/showthread.php?t=763006)

but it did not fix my problem. So, I updated the libdvdcss to version :1.2.10, the post had version 1.2.8, I think.

[http://download.videolan.org/pub/libdvdcss/1.2.10/deb/](http://download.videolan.org/pub/libdvdcss/1.2.10/deb/)

And now, at least VLC works fine. MPlayer or xine still do not work.

Good luck.

---

### Post by mconway on 2009-03-01
Using Totem (Intrepid), I play a DVD from the desktop or autorun, and get errors like "Failed to connect stream..." and "Internal data flow error."  :-k

When I ran Totem from a terminal to check the output, I navigated to the DVD from the menu, and it played just fine. I was not root.

However, I tried again from the terminal--this time with a different DVD--and I get the "internal data flow error" again!   ](*,)

**EDIT: VLC works like a charm even for that last DVD.**

---

### Post by cornish12 on 2009-03-01
I got this message when I selected the episode I wanted to play on the DVD. I followed vegas588 advice and it worked. Thanks :KS

---

### Post by dskyracer on 2009-03-02
Thanks Vagas588 I was having a problem running my DVD movies in Intrepid and made the changes you suggest and then the movie ran fine.

---

### Post by llawwehttam on 2009-10-13
Well that fix didn't work for me so I 'sudo apt-get install totem-xine' and that works great. I now prefer it to normal totem or Vlc.

---

