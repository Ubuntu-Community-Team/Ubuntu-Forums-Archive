---
title: "[SOLVED] &amp;quot;xrandr: screen cannot be larger than&amp;quot; ..."
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by hanzj on 2007-10-27
Hello, 
I'm trying to configure my dual-monitor setup.

> $ xrandr --output DVI-0 --left-of DVI-1 
xrandr: screen cannot be larger than 1600x1200 (desired size 2880x1200) 

How come xrandr says the above, and how can xrandr fix it? I prefer it if I don't have to mess around with xorg.conf.

Thank you.

---

### Post by Koziasty on 2007-10-28
same problem for me.... any help?

---

### Post by hanzj on 2007-11-03
Koziasty,
I found the answer. We do have to make a small edit in xorg.conf. 

Please refer to: 
[http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/](http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/)


I got mine fixed by following his instructions!

 xrandr --output DVI-1 --left-of DVI-0

---

### Post by m4cks on 2008-01-16
For those that cannot be bothered following the link, you need to add a "Virtual" line to your 'Screen' section. His example below:

Section "Screen"
Identifier “Default Screen”
Device “ATI Technologies Inc Radeon…”
Monitor “Generic Monitor”
DefaultDepth 24
SubSection “Display”
Modes “1024×768&#8243;
**Virtual 2624 1200**
EndSubSection
EndSection

Mine was

SubSection "Display"
  Dept 24
  Modes "1280x1024"
**  Virtual 2560 1024**
EndSubSection

open source ati driver working beautifully...so far, much nicer than the ATI proprietary crap.

---

