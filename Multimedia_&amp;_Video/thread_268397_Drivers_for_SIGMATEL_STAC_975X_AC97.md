---
title: "Drivers for SIGMATEL STAC 975X AC97?"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by Zach1188 on 2006-09-30
My sound card is a SIGMATEL STAC 975X AC97, is there any Linux drivers for it? 

Honestly, it sounds like crap on Linux. I can hear it fine, but everything is high-pitched. And the subwoofer (I know that sounds weird for a laptop) doesn't work.

Any help?

(P.S. My laptop is a Dell Inspiron 9300).

---

### Post by Zach1188 on 2006-09-30
Can someone please reply? I can't find anything about it on google.

---

### Post by Zach1188 on 2006-10-03
Someone? Please, I really need the help.

---

### Post by ProtoBot on 2006-10-04
I have a  SigmaTel STAC9200, on a Dell Inspiron 9400 and I'm having the same problem as the thread starter with the subwoofer. I've tried numerous solutions including directly modifying Master mono through alsamixer and amixer to no avail, since "Master Mono" (and hence the subwoofer) isn't recognized by alsa. Is there anything I can do to correct this? Would compiling from the latest ALSA source help at all?

I won't complain about the speaker's pitch though :p

---

### Post by ProtoBot on 2006-10-07
Should I assume no one has gotten the sigmatel sound cards subwoofer on the latest Inspiron's working under ubuntu?

---

### Post by darkrider01 on 2006-10-12
Refreshing thread. Got the same problem as well. Adjusting master mono is quite annoying...

---

### Post by ProtoBot on 2007-01-21
I'm bumping this thread just in case someone knows the answer now, after some months have passed :p

---

### Post by SarahKH on 2007-01-27
Unfortunately the STAC line of audio chips don't seem to be well supported at the moment. Like yourself I'm able to get noise out of my XPS (STAC 9200) but nowt outta the sub, not tried plugging in headphones to see if the cutout to speakers works or not yet though. 

To be honest, google seems to point all over the shop; although it seems that things died off around Nov 06... that could be me being specific to the 9200 and not the whole range though :) 

I honest don't know what to suggest; I'm not aware of an 'ndiswrapper' style program for sound drivers that could hook in to ALSA and from poking around OSS has even worse support.    

The real downer is that it's a universal issue and not distro specific due to ALSA, so it's not like grabbing Fedora or anything else will fix it :(

---

### Post by GrejpFrut on 2007-01-28
Well I have a Dell Inspiron 9300 and I had this same issue.  Here is a thread that fixes the issue:
[http://ubuntuforums.org/showthread.php?t=199579]("http://ubuntuforums.org/showthread.php?t=199579")

What I did was use the Keytouch program that mentioned in that thread.  That program allows you to bind a command to a specific key.  Use the amixer commands for the volume keys and you should be set.  Good luck.

---

### Post by Thug14 on 2007-02-25
does ne1 have the drivers for SIGMATEL STAC AC97,I need them too

---

