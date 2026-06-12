---
title: "Flash player plugin for Firefox no sound"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by williambertram on 2006-09-23
Adobe Flash player version 7.0.68.0
Ubuntu version 6.06
Hardware: Dell Latitude D600
Audio Hardware: Integrated Intel AC97
Web browser: Firefox 1.5.0.7 (also tested with latest Opera, and full Mozilla)

I'm getting no sound with the Adobe Flash player plugin for Fihttp://www.ubuntuforums.org/newthread.php?do=newthread&f=138refox.  It actually worked briefly after installing it, but after a reboot it stopped.  Completely re-installed Ubuntu and Flash and it's the same thing.

Actually installed Ubuntu and Flash on an identical Dell Latitude D600 and it does the same thing.

Sound works for everything else (including the mplayer plugin for Firfox when I view quicktime movies).

I downloaded Flash from [http://sdc.shockwave.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4](http://sdc.shockwave.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4)  

I followed the installation instructions from that web page.  I realize that the link above says shockwave, but this is the actual official web page for the Adobe Flash player for Linux.

I have attached the Dell product brochure for the Latitude D600 which lists all of the hardware for my laptop.

---

### Post by BitTorrentBuddha on 2006-09-23
Flash pipes audio through OSS, to "fix" it, install the alsa-oss package. then in the future use aoss firefox instead of just firefox. ```
sudo aptitude install alsa-oss
``` then change all launchers' commands to ```
aoss firefox
```

---

### Post by williambertram on 2006-09-24
Wow that works.  I've been combing forums for days and that's the first mention I've seen of that. 

Thank you for the quick and helpful answer.  Have a great day!!!!

---

