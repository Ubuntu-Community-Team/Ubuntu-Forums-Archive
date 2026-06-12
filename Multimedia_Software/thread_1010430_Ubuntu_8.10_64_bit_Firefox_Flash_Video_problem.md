---
title: "Ubuntu 8.10 64 bit: Firefox Flash Video problem"
date: 2008-12-13
forum: Multimedia Software
---

### Post by art_s on 2008-12-13
Hi there,

When playing some video in 64-bit Firefox under 2.6.27-9-generic #1 x86_64 GNU/Linux (Ubuntu 8.10) strange thing happen: the whole flash area becomes gray and does not respond to any input.

The only solution is to restart the browser.

I tried the 'complete fix' from the sticky post in this forum, which actually helped to cure the java applets problem, but this one.

I wonder did anyone had that as well and may have fixed that? 

Thanks in advance!

---

### Post by art_s on 2008-12-14
Bumping up with hope that someone got across that as well...

---

### Post by ubuntergeist on 2008-12-20
I've got the same problem. I have to refresh pages on firefox to get the correct display, but on some websites it is merely impossible (especially when the flash videos on these sites are hosted on youtube or on any other external video hosting site)

BTW, the problem occurs much less frequently on epiphany.

any idea ?

---

### Post by Stratis on 2009-01-11
Non 32 bit Firefox flash video issues on Ibex with me too. 

They just won't play; a black box is displayed (though I can right click to get the installed flash version). 

I haven't found many search results of people reporting this issue; I **have** found many people reporting flash sound issues though.

It isn't a flash issue as I can play any flash videos I come across (and do) in Galeon.

---

### Post by Kleist on 2009-01-11
I'm running 64-bit ubuntu and I had a lot of problems with flash. All was gone when I installed the 64-bit version of flash. Try this and see if it helps:

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)

---

### Post by inmicta on 2009-03-28
PLEASE HELP ME...

Someone out there knows the fix to this problem.  Please share your knowledge.

My current problem:
*sigh*
I am using 64-bit 8.10 Intrepid Ibex.
I can watch some youtube videos with sound and everything just fine with no problem.  Then I get a black screen with no sound on other youtube videos.  What I do get is the status bar filling up but when I hit play I get nothing more.  The same thing happens on any website using flash.  I've had the same results while using Firefox, Epiphany, and Galeon. 

Please provide as many suggestions and fixes as possible. Thanks in advance.

---

### Post by SuperSonic4 on 2009-03-28
```
sudo apt-get purge flashplugin-nonfree
```

Get the 64bit version of flash [here]("http://labs.adobe.com/downloads/flashplayer10.html") and extract it to the desktop

```
sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so
```

*from:[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)*

---

### Post by jo4hnc on 2009-03-28
Here's a pretty good How To.

[http://ubuntuforums.org/showthread.php?t=772490&highlight=flash+problems](http://ubuntuforums.org/showthread.php?t=772490&highlight=flash+problems)

---

### Post by inmicta on 2009-03-30
> **SuperSonic4 said:**
> ```
sudo apt-get purge flashplugin-nonfree
```

Get the 64bit version of flash [here]("http://labs.adobe.com/downloads/flashplayer10.html") and extract it to the desktop

```
sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so
```

*from:[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)*

Did you experience the same problems?  Did this fix it?

I've tried something similar and it did nothing to fix the problem.  I will try again though and will let you know how it turned out.

---

### Post by SuperSonic4 on 2009-03-30
It worked for me in Kubuntu 8.10 x86_64 and an adapted version worked in arch

---

### Post by gatorbrit on 2009-04-02
Worked for me also.  Thanks


> **SuperSonic4 said:**
> ```
sudo apt-get purge flashplugin-nonfree
```

Get the 64bit version of flash [here]("http://labs.adobe.com/downloads/flashplayer10.html") and extract it to the desktop

```
sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so
```

*from:[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)*

---

