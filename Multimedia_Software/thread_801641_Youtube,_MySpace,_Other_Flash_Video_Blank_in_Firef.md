---
title: "Youtube, MySpace, Other Flash Video Blank in Firefox 3"
date: 2008-05-20
forum: Multimedia Software
---

### Post by Dr. Faustus on 2008-05-20
For some reason in Firefox 3 beta flash video and players keeps coming up blank in Hardy.  It never happened before the upgrade.

I found this thead, [http://ubuntuforums.org/archive/index.php/t-679446.html]("http://ubuntuforums.org/archive/index.php/t-679446.html"), on the subject.  I thought I'd try their solution

While competent, I'm not terribly savy and my xorg.conf file doesn't have a "driver" section.   I thought "no problem, I"ll just add one."

When I added:

```

Section "driver"
         Option "XAANoOffscreenPixmaps" "true"  
EndSection


```

To my xorg.conf file it failed on the restart and I had to change it back in safe mode.  

What is to be done?   Any help is greatly appreciated.

---

### Post by konungursvia on 2008-05-20
Did you install or enable Noscript? If so, make sure you temporarily allow the web page in question, by right clicking on it, then enabling under Noscript. Also, look up a search including the terms "flash enable hardy" and make sure flash is enabled.

---

### Post by Dr. Faustus on 2008-05-20
I have flash enabled.  The other night I re-installed the plugins for Flash 9, and I could watch Youtube vids again.  Today when I started the computer back up it didn't work.  I suppose I can re-install the flash plugin again, but I can't be doing that every night.  

I'm fairly certain it's a problem within Firefox 3 Beta and not Ubuntu itself.   I only tried messing with the xorg.conf file because I'm at a loss for how to fix this.


The Noscript thing sounds promising though.  I'm attempting that as we speak.

---

### Post by Dr. Faustus on 2008-05-20
Okay, so I installed the NoScript add on, and when I allow a band's MySpace or a Youtube vid, it allows it and then shows a white box.  What's that all about?

---

### Post by Dr. Faustus on 2008-05-20
I found this old thread

[http://ubuntuforums.org/showthread.php?t=774830]("http://ubuntuforums.org/showthread.php?t=774830")

On the same subject.  I probably should have searched more beforehand.

edit:  To hell with it.  I'm just going to go back to Firefox 2 and wait for the proper release of Firefox 3.  Hopefully they'll fix it by then.

---

