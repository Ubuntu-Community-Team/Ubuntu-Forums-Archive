---
title: "DeVeDe and &quot;Menu generation failed&quot;"
date: 2009-02-02
forum: Multimedia Software
---

### Post by uhappo on 2009-02-02
Anyone else with this problem?

Everything is ok but when in the end, when I try to "end" session and make it a dvd, I always get "Menu generation failed"-error.

Whats this?

---

### Post by Dan Again on 2009-03-20
Bump...I am having the same problem.  Most of the time there is no problem, but with one particular avi Devede does not want to work.  Go through all the steps just like for the other avi's, click finish and then Devede starts to do its thing, but after a moment I get this error message.  I go to the destinaton directory and can see that Devede started to create the files, but for some reason got hung up.  Help!

---

### Post by Dan Again on 2009-03-21
Someone, anyone...halp?

---

### Post by bdcollignon on 2009-03-31
Got the same kind of problem.

Error message (translated from French) reads:

--------------
Error

Impossible to add the buttons to the menus.
It seems to be a bug with SPUMUX.
--------------

Any idea welcome for me too...

---

### Post by Dan Again on 2009-04-07
Bump

---

### Post by xc3RnbFO8P on 2009-04-07
Try to install or reinstall **imagemagick** in Synaptic Package Manager

---

### Post by coffeecat on 2009-04-07
> **bdcollignon said:**
> 
--------------
Error

Impossible to add the buttons to the menus.
It seems to be a bug with SPUMUX.
--------------

Yes, I was getting this too in the version that came with Intrepid (on two different machines). I never did find a fix. The good news is that I'm not getting this problem in DeVeDe in Jaunty. The even better news is that the design of the disc type chooser has moved into the 21st century at last.

---

### Post by gandaran on 2009-04-07
install the latest devede release from [devede]("http://www.rastersoft.com/programas/devede.html") website, scroll down to the bottom page and download the .deb package for ubuntu.

---

### Post by gfullmer1 on 2009-04-08
I had the same problem. In my case it was caused by a name in the path that had special characters.  In my case the culprit character was a "[".  Solution: move and/or change path and name so that special characters in the path do not occur.

Hope that helps,
Glen

---

### Post by Dan Again on 2009-04-17
Changing the path named worked.  Totally simple fix...you rock!  Thanks so much!

---

### Post by eladamri on 2009-06-10
I was having the same problem and changing the path name fixed it. Thanks!

---

### Post by dawg4fr on 2009-10-13
I had the same error msg.  Installing the latest version was no help.  I had been saving the generated iso file in the same directory as the avi  file I was converting,  which had previously been working.  I changed to saving the generated iso file to a new directory in my home folder and it's worked fine.  Go figure.  Does DeVeDe just want a shorter path  to save to?  
/home/name/working video  
 instead of  
/home/name/downloads/videos/avi/filename.avi

using jaunty 64 bit

---

### Post by sistematico on 2010-07-03
> **Dan Again said:**
> Changing the path named worked.  Totally simple fix...you rock!  Thanks so much!
Not worked for me.

---

### Post by mmaki on 2010-11-21
I had to recompile mplayer from source with png video support to get past the error. I do not use mplayer from the repositories. I don't recall the exact error I got but it did list something related to png.

---

### Post by jayboe on 2012-12-07
Might be a little late in the game, but I am using Ubuntu 12.04 Unity. I already had ffmpeg installed and when I have devede open I went to edit>prefernces and found that ffmpeg instead of mencoder was checked so I simply unchecked that and now it is working fine. Hope this helps...

---

### Post by oldos2er on 2012-12-07
Old thread closed.

---

