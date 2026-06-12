---
title: "Comedy Central Flash Player"
date: 2008-06-01
forum: Multimedia Software
---

### Post by MGStreak on 2008-06-01
I kept telling myself that if I just searched the forums long enough and tried enough Flash suggestions, I could solve this on my own.  Alas, the time has come for me to hang my head and beg the forums for assistance.

I cannot get Comedy Central videos to load.  I can see YouTube, DailyMotion, and various other Flash-based video sites, but I cannot get the videos from Comedy Central to play.  The applet loads, but when I click on the 'Play' button, it appears to immediately go to the end of the video, where I see a 'Click to Play Again?' button.  If I click on that button, the applet shows me that it is 'Loading...' the video, but nothing ever comes of it.

Attempting to resolve this issue, I have tried using Gnash, Swfdec, and the new Flash V.10 beta.  The first two were non-functional, and the third one crashed Firefox upon loading.  I tried the instructions and suggestions found in this topic 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
to no avail, being sure to fully purge each Flash program before trying the next.

I am using the following:
Current Flash version in the repos (flashplugin-nonfree version 9.0.124.0ubuntu2)
Firefox version 3.0b5
Hardy Heron version 8.04, 32-bit

All applications are up to date according to Synaptic/Update Manager.  If any further information is required, please don't hesitate to ask!  *Any* suggestions would be greatly appreciated.

---

### Post by MGStreak on 2008-06-02
Unfortunately, I have managed to solve this problem through continued Googling.  It turns out that the problem doesn't lie with my machine at all, rather, Comedy Central is blocking access to these videos in Canada:

[http://tdsdev.blogspot.com/2008/01/oh-no-canada_17.html](http://tdsdev.blogspot.com/2008/01/oh-no-canada_17.html)

Anyone have any suggestions?  I've tried some web proxies, but none are working out?

---

### Post by fa1512 on 2008-11-05
I have been having problems with this too but I don't think it is necesarrily because of ip blocking. I have a dual boot and I log into windows in order to watch Colbert Report. I am accessing this information from Germany where I am currently residing so I would find it strange that they block the UK and Canada but not German ips. Unless of course they don't block us here because we don't take up so much bandwidth.

---

### Post by vgrisham on 2008-11-28
Last I checked Texas (where I am) is still in the lower 48 (though John Stewart and Stephen Colbert might wish otherwise). I don't think it's being blocked regionally. It's gotta be something about Flash in Ubuntu. 

Here's a weird thing. I can watch this Comedy Central video of Wilco's recent, kickass, performance on the Colbert Report when accessing it from [this]("http://wilcoworld.net/news/index.php") external site and  [this]("http://ccinsider.comedycentral.com/cc_insider/2008/10/wilco-colbert-will-love-you-baby.html") external site, but it won't play [here]("http://www.colbertnation.com/the-colbert-report-videos/189726/october-30-2008/exclusive-wilco-song") on comedy central's website. 
Help me set Wilco free on Ubuntu! Don't make me dual boot for Jeff Tweedy and company, because I will! :guitar:

---

### Post by vgrisham on 2008-11-29
Installing Adobe's new 64-bit flash plugin resolved this!

Instructions are [here]("http://ubuntuforums.org/showthread.php?t=985479&highlight=comedy+central+flash").

---

### Post by carolinason on 2010-05-13
32 bit user here - in the states on the CC site i just get audio and no image - all other flash sites play - installed chrome says no flash - reinstalled flash still no flash don't like chrome anyway

works fine in win xp sad to say

---

### Post by BULLIT22 on 2010-05-13
Hey Guys. Had the same problem with my wifes laptop and a few Facebook Flash games. I used this unistaller/installer and have had no issues. I used the Flash 10.1 beta.
 
_[COLOR=#800080][http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595)[/COLOR]_[]("http://ubuntuforums.org/showthread.php?t=1414595&highlight=Yoville")
 
Hope this helps.

---

### Post by carolinason on 2010-05-13
- my issue is flashblock - i had to allow flash from the site. clicking to allow wouldn't work

---

