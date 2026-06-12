---
title: "Audacity segmentation fault"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by jornat on 2007-11-05
When trying to run Audacity 1.3.3 (exactly the same for 1.2.6) in Ubuntu 7.10 (Gutsy) with kernel 2.6.22-14-rt (same with 2.6.22-14-generic) and GNOME 2.20.0 I get the message "Segmentation fault" and Audacity hangs without starting up its GUI. 

However, this only happens when I have an ALSA-compliant soundcard loaded. When the default is the onboard non-ALSA soundcard, Audacity starts up as it should.

I have searched the net a couple of weeks now but haven't found a solution :(. I have tried a number of fixes, e.g. running "aoss audacity". I also tried the fix from [http://ubuntuforums.org/showthread.php?t=129147](http://ubuntuforums.org/showthread.php?t=129147) (touch /etc/ld.so.nohwcap), but I have no /etc/ld.so.nohwcap file.

Please help me!

---

