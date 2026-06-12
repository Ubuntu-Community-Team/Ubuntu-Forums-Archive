---
title: "flash crashing hardy"
date: 2008-04-23
forum: Multimedia Software
---

### Post by revelationman on 2008-04-23
I have both Ubuntu and Opera (shared) when I load a flash youtube the screen goes dark and then the force quit option appears, this really started to happen with Hardy 

Do you good folks thing I should just download Hardy and reinstall as fresh install or is this a common problem with Flash and Hardy 

Lets hope it is not this is a pain in the backside problem

---

### Post by benerivo on 2008-04-23
It shouldn't happen, and it doesn't happen on my hardy. What opera version do you use? I use the latest 9.5 beta from here [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/) and flash.so from here [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by revelationman on 2008-04-23
I have the version that was listed here 
Also Firefox crashes sometimes with Flash
If there is one thing that Ubuntu should not of done with Hardy was include a beta version of Firefox they should of stuck with stable version
I might just have to download hardy and reinstall 

Hardy is great but this Flash issue is a pain

---

### Post by Tulsapoke on 2008-04-23
I don't think this is a FF3 problem.  I am still on Gutsy, however I did install FF3 (after reading some good reviews).  Firefox 3 beta seems to be more stable than FF2 was.  I have completely switched over both my laptop and my desktop to 3 and have seen zero problems flash or otherwise over the last month.  I'm running a YouTube video in another tab while writing this just to beat on it some more... no problem.
__________________
Home made 6yr+ old POS ECS, Athlon 1600+
512Mb RAM
Ubuntu 7.10 - the Gutsy Gibbon

---

### Post by GreenMeanie on 2008-04-24
Firefox 8.04 and flash crash in youtube every time.

---

### Post by williambertram on 2008-05-02
Ditto here.  

Hardy, Firefox 3 beta 5 (the one installed with the os).  Absolutely no modifications made.  Fresh install.

Tried installing Adobe Flash Player from Add Remove Programs, crashes youtube every time.  *ANY* youtube video.  Just click on a few and it will eventually crash, but usually it's on the first one.

Tried copying the .so file to the plugins folder.  Still crashes.

Tried all of this on my laptop (Dell Latitude D610) and it still crashes.

Tried on a live CD on my computer at work (New HP, can't recall model) and still crashes.

Tried on my wife's laptop (Latitude C600) still crashes.

Tried Gnash, and the quality was bad.  Tried SWF plugin alternative, and it puts a big "Play" button instead of automatically playing the video, which I hate, but might end up using anyway just so it doesn't crash.

This is not specific to Hardy.  The Adobe Flash player for Linux was crashy on 6.04 and 7.10 as well.  Tried on several computers (Dell and HP models, Intel and AMD processors) and Firefox 2 crashed frequently with the Adobe plugin. 

Anyway, Nice distro guys.  I'm using Hardy on my main computer and loving it.  My wife has even been using it with no complaints (other than YouTube crashing Firefox :)

---

### Post by Zorael on 2008-05-02
Stick to FF2 for the time being, I'd say.
```
*<open up FF3, clean out cache>*
$ sudo aptitude purge firefox firefox-3.0
$ sudo aptitude install firefox-2.0
(optional): $ sudo ln -s /usr/bin/firefox-2 /usr/local/bin/firefox
```

---

### Post by williambertram on 2008-05-09
Well I've figured something out that might help developers in troubleshooting.  The Adobe Flash player never crashes any of my systems on FF3 if I pause the playing video before clicking on another.  If I just click on a Flash video while one is playing it crashes every time on my main computer and my laptop.  This is with Ubuntu installed to the hard drive, not running from a liveCD.

Took another posters advice and back leveled FF to version 2.  It's more stable but I can still crash it if I click on ~10 videos without pausing.

May not mean anything, but thought I would post it just in case.

---

### Post by sdowney717 on 2008-05-09
used to crash a lot on flash but not anymore.
I am using firefox 3.0b5 adobe flash hardy ati driver.

A couple weeks ago an update came out and it started working for me.

---

### Post by aikiwolfie on 2008-06-22
Flash 10 works better. But it still crashes.

---

### Post by Odrodzona-Sarmacja on 2008-06-22
Watching a vid with flash plugin on firefox does freeze my Xubuntu. Then I have to power down my computer to reboot it.

---

