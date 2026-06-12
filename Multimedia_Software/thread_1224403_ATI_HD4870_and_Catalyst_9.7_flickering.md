---
title: "ATI HD4870 and Catalyst 9.7 flickering"
date: 2009-07-27
forum: Multimedia Software
---

### Post by Nizce on 2009-07-27
Hi,

I have read so many threads about people having problem with their ATI cards.
But i haven't found any answer to my problem:

I just bought a ATI HD4870. I've installed the new Catalyst 9.7 from ATI (also tried the proprietary one).
But my problem is that when i start for example Xbox Media Center, a game or just try to bring up the preferences for my screen it starts to flicker and while it flickers the computer gets terribly slow.
I don't have this problem when I'm watching movies with VLC or Mplayer(though it flickers while the program is starting) or starting any other "dekstop" programs.

btw i've tried to disable all effects in compiz but it makes no difference, have even tried Metacity with the same result.


Does any one else have this problem? or even better, a solution.


/Daniel

---

### Post by cozmicharlie on 2009-07-27
Have you tried Catalyst 9.6?  Catalyst 9.7 is new so it may still have some bugs to work out.  I have good results with ATI card using 9.6.

---

### Post by Nizce on 2009-07-27
ok thanks i'll try that right away

---

### Post by xzero1 on 2009-07-27
There are some compiz options that may help. See this post: [http://ubuntuforums.org/showpost.php?p=7659224&postcount=42](http://ubuntuforums.org/showpost.php?p=7659224&postcount=42)
Let us know how 9.7 works out.

---

### Post by Nizce on 2009-07-27
Just tried Catalyst 9.6 instead, but that didn't help either.
The screen still flickers when i start certain apps. 
I also noticed that the process xorg takes 100% of my cpu while the screen flickers, but when it stopsand the app has started(takes about 10 sec for xmbc) everything goes back the way it should.

I dont really know what to do except having to install windows and dual-boot, to play games etc.

---

### Post by xzero1 on 2009-07-27
How did you install it? Did you use this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by Nizce on 2009-07-27
I used ati's own guide.
But i'll try and see if i can find something new in the one that you posted a link to.

Thanks!

---

### Post by Nizce on 2009-07-28
Just got the tip to do the following:

aticonfig --set-pcs-str=DDX,EnableRandR12,FALSE

The problem was said to be: 
"The problem is a broken randr implementation in fglrx."

So i hope disabling it will solve my problem. I'm not sure though what ranr does and what will happen if i disable it.

---

### Post by cozmicharlie on 2009-07-28
> **Nizce said:**
> Just got the tip to do the following:

aticonfig --set-pcs-str=DDX,EnableRandR12,FALSE

The problem was said to be: 
"The problem is a broken randr implementation in fglrx."

So i hope disabling it will solve my problem. I'm not sure though what ranr does and what will happen if i disable it.

see this for an explanation [http://en.wikipedia.org/wiki/RandR](http://en.wikipedia.org/wiki/RandR) and more detailed info here [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

you should be OK - try it.

---

