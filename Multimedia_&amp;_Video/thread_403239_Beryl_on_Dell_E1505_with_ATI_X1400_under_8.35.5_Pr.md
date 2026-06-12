---
title: "Beryl on Dell E1505 with ATI X1400 under 8.35.5 Problems"
date: 2007-04-06
forum: Multimedia &amp; Video
---

### Post by legzelda on 2007-04-06
Hello.  I just installed the Feisty Fawn beta and got everything working with the latest ATI drivers from their Web site.  Running 'fglrxinfo' gives me the right ATI drivers--NOT the Mesa drivers, thank goodness.  Any way, I thought I would give Beryl a go and have had no success.  I followed guides on this forum that suggested making a new Xgl session, and booting into that and trying to run Beryl does nothing, produces a white screen, or really distorts the graphics and makes the screen completely garbled, depending on whether or not the ATI drivers are installed.  When I try to run Beryl through a standard Gnome session, or through the Xgl session I created, when the right ATI drivers are shown through fglrxinfo, nothing happens.  Windows don't change, none of the fancy effects happen, etc.  At best, the screen flickers when I right click the Beryl diamond and select "Reload Window Manager."  Does anyone have any advice on how I might get Beryl to work on my system?  Thanks!

---

### Post by shoofy on 2007-04-12
I'm running the same configuration. After a lot of messing around and tweaking that I probably couldn't reproduce, I managed to get Beryl to work partially some of the time. Frequently when I log into the Xgl session I just get the garbled screen like you described. The other half I can get Beryl to start and show me the cube and skydome and all the effects, but it will not render any windows. They just appear as white rectangles. This includes the gnome panel.

I'm really missing Beryl, since I had it working perfectly on Edgy, so please let me know if you have a way to get it working.

---

### Post by legzelda on 2007-04-15
Thanks for the encouragement.  I'm still having no success with Beryl and my current configuration, but I will continue to tinker with things.  If anyone knows of a fix, please let me know!  Thanks!

---

### Post by shoofy on 2007-04-15
Success! I build my own debs using Trevino's script and they work perfectly. They're too big to post on the forum, but I'll try uploading them somewhere else and post the links.

---

### Post by shoofy on 2007-04-15
You can download them from [http://www.sharebigfile.com/file/144000/beryl-git-tar-gz.html](http://www.sharebigfile.com/file/144000/beryl-git-tar-gz.html)

---

### Post by legzelda on 2007-04-16
Oh my gosh!  It worked!  Thank you SOOOOOO much!  I never realized how impressive Beryl is!  Wow!  Thanks again!

---

