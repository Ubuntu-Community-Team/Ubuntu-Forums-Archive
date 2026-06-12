---
title: "ATI + Ubuntu(Jaunty) = video tearing"
date: 2009-09-09
forum: Multimedia Software
---

### Post by gully on 2009-09-09
Hi all.

I have the following problem: I have an XP/Ubuntu dualboot system with an ATI HD 4890 graphics card. In windows the 4890 is a monster that eats Crysis for breakfast, but in Ubuntu the monster seems to be chained by shitty drivers, it can play some older games (Stracraft and Mafia) smoothly without artifacts but it seems sluggish when handling desktop effects and it cannot play video (AVI, MKV) without tearing. The tearing looks like the tearing you see when you play a game with vsync turned off. 

There are some older threads (about older ATI cards) on Ubuntuforums that basically blame the issue on ATI's drivers and say there's nothing that can be done about it. 

I was wondering if there's been any progress in this department, or not, because Nvidia cards don't seem to have these issues in Ubuntu and this is 2009, so I'd like to get some decent video quality from my $250 graphics card.

---

### Post by adam.d.clemons on 2009-09-09
Most of those games you're running are windows native correct? you may want to try looking at this how-to. 

[http://www.fsckin.com/2008/02/21/how-to-run-call-of-duty-4-cod4-modern-combat-in-linux/](http://www.fsckin.com/2008/02/21/how-to-run-call-of-duty-4-cod4-modern-combat-in-linux/)

recompiling wine from scratch with the extra DLLs that this guy uses made my 3d games work a lot better. I haven't made Crysis run in ubuntu yet, but Cod4 runs great.

Also, ATI is a bit behind Nvidia as far as ubuntu graphics goes. I had an ATI card and had a lot of difficulty making ubuntu use it's full potential. Then i upgraded to an Nvidia card and it works fine. If the Wine recompile doesn't work, you may just have to keep the gaming on your windows partition.

---

### Post by gully on 2009-09-09
No, gaming isn't the problem, that's what I have Win XP for, but I want to play videos without tearing, that's all.

---

### Post by KJY9 on 2009-09-09
I'm using an ATI 4550 in my box and having the same problem, except worse. If I use the driver (or lack thereof) in the install cd, video is just ok (certainly not optimal). However when I upgrade to the latest driver through Ubantu, I can't use my correct resolution, and the video is absolutely horrible (choppy, no synch with the audio).
Am I to understand that ATI card users are simply stuck with no support for their cards?

---

### Post by markbuntu on 2009-09-09
The 4890 and 4550 and a bunch of other 4xxx series cards came out after the driver available with Jaunty was released. You need to get the latest driver from ati to get the best performance from those cards.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Be sure to remove the old driver before installing the new one.

---

### Post by gully on 2009-09-09
I already did that, the problem persists with Catalyst 9.8 drivers.](*,)

---

### Post by gully on 2009-09-13
I upgraded to Catalyst 9.9, or so I think, because the CCC doesn't say which version it is (yes, ATI found another way to screw us Linux folks over.)
Anyway, there's still tearing, nobody knows how to fix it and it's not even listed as a "known issue" in the release notes (while many thousands of people have reported the exact same problem), so I'm going to complain to AMD about it.

---

### Post by markbuntu on 2009-09-13
If you are using compiz then there is an fglrx option in the compiz settings. You should turn that on.

---

### Post by gully on 2009-09-13
I have the Compiz settings manager, but I can't find anything about fglrx in the settings.

---

### Post by gully on 2009-09-13
I think I solved the problem: install maplyer and then type in "mplayer -vo gl2" in the console. Then open mplayer --> preferences --> video and choose X11(OpenGl) as output and click ok, the next time you open mplayer video's won't tear any longer, this only works for mplayer though.

---

