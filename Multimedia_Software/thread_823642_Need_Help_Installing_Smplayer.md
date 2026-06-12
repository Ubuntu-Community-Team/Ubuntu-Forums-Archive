---
title: "Need Help Installing Smplayer"
date: 2008-06-09
forum: Multimedia Software
---

### Post by Jenga-kun on 2008-06-09
Here's my story. Back when I was using Feisty I installed smplayer and it worked beautifully. I was able to play everything even my 720p .mkv movies and anime. I updated to Gutsy about 2 weeks ago and installed smplayer through the package manager. I found that I could not use the xv driver and that the only ones that worked best were x11, gl, and gl2. So I could play any sd video and hd videos could only play properly as long as it wasn't in fullscreen (when it is in fullscreen audio and video go out of sync). I'm pretty sure I was able to use the xv driver when I was on Feisty so I poked around and found that I'm not even using the most up to date version of smplayer. So I uninstalled it and downloaded the .deb from the smplayer website but when I start it up I get this error: Error: Dependency is not satisfiable: libqt4-core

Can somebody please help me? I really want my smplayer back and more importantly I want it to work properly.

---

### Post by rvm4000 on 2008-06-09
The deb package for i386 is compiled in a Ubuntu Feisty. Maybe in Gutsy the name of the Qt packages have changed. I suggest you to compile smplayer yourself. It's very easy, just take a look at Install.txt. Or look for a package for Gutsy:
[http://smplayer.wiki.sourceforge.net/Contributed+Packages](http://smplayer.wiki.sourceforge.net/Contributed+Packages)

If you're using Compiz try to disable it. I think xv doesn't work with Compiz.

---

### Post by mc4man on 2008-06-09
> Error: Dependency is not satisfiable: libqt4-core
You might want to resolve that issue, the latest smplayer should install on feisty, gutsy and hardy. Go into synaptic, search libqt4-core and find out what the problem is. (also ck. your software sources and see if any feisty repos are enabled/ present)
As far as xv and compiz if it's not working then it's an issue related to your video adapter and what driver your using. I'm running compiz and xv on 3 setups (ati 9500 pro, ati 200m, nvidia 7800gs) with no issues.

---

### Post by Jenga-kun on 2008-06-09
Thanks for all your help.

I never had compiz on to begin with so I don't think that's the problem. 

As for installing the latest version of smplayer, I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=551231](http://ubuntuforums.org/showthread.php?t=551231) and now I'm up to date. Unfortunately I still have the same problem: I can't use xv. I really don't know what the problem is, I'm absolutely certain that I was able to use xv before on feisty so I don't understand why I can't use it now. Do you think I should get a new video card. To be honest I'm still using the built in video card on my computer. 

Do you think these will support xv:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130062](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130062)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130085](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130085)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150229](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150229)

---

### Post by mc4man on 2008-06-09
I would say any of those cards would do fine. I'm still in the AGP world
but my BFG GeForce 7800gs OC works great.
Do a little browsing, I've seen more posts (issues) mentioning the 8000 series vs. the 7000 series. (I'd always go for better card if possible)
If you go for 7000 series a 7800 is markedly better than 7600

---

