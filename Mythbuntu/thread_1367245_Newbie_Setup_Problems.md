---
title: "Newbie Setup Problems"
date: 2009-12-29
forum: Mythbuntu
---

### Post by c152flying on 2009-12-29
I am starting out with Mythbuntu for the first time. Whilst i have been using Ubuntu and Suse for a number of years, I am purley a desktop user and have no terminal/command line Knowledge. I have gone through the installation process without knowing what a front or back end is! I have stuck to the suggestions on installation. When it searched for my tv card (HUP Nova T DVBT Model 909) it didnot alow me to scan channels. Also it didnt have information for the UK, the nearest info being Ireland. When the system boots into Mythtv, I cant watch TV, an error message tells me that "all inputs are being used". 
When I look into the setup pages, its all a foreign language to me!
I have heard many good things about Mythbuntu for building HTPC boxes but I am getting very confused at the first hurdle.
Please could you help me.

Many thanks  C152flying

---

### Post by Quickblood on 2009-12-29
I'll be very interested to see how it goes for you. I've just given up on Mythbuntu cause while Ubuntu is nice and easy Mythbuntu set-up isn't at all and I'm sick and tired of reinstalling it each time to try a different tutorials settings. I'm going back to Windows where setting up a DVBs card made sense.

If you ever figure out how to do it seriously put up a step by step video on Youtube cause if there were some instructions for people who'd genuinely never used Linux before it would really help and may even tempt me to try it out again. But for now I'm effing sick of the sight of it. lol!

Good luck!

---

### Post by lanierbrian on 2009-12-29
C152 Flying, I will also be closely watching the responses to your thread.  I am almost to the point of Quickblood myself.  It seems like every guide and tutorial I can find is written for an audience of Linux developers.  There seems to be a very generous community of support, but I'm not sure I even know what questions to ask.  I'm a Linux newbie myself, but I was able to set up an Ubuntu server at home to share files and printers with relative ease, and I feel fairly confident in my ability to securely administer it.  If I can't make MythTV work on my HTPC soon, I'm going to have to go the Win7 route myself (ugh).  Maybe after some more time with the home server I'll give it another shot.  I get a lot of enjoyment out of working on airplanes, but ultimately I'd rather be flying!

I'll post my own situation in a new thread and see if I can find some enlightenment :)

---

### Post by ubnewbie2 on 2009-12-29
> **c152flying said:**
> I am starting out with Mythbuntu for the first time. Whilst i have been using Ubuntu and Suse for a number of years, I am purley a desktop user and have no terminal/command line Knowledge. I have gone through the installation process without knowing what a front or back end is! I have stuck to the suggestions on installation. When it searched for my tv card (HUP Nova T DVBT Model 909) it didnot alow me to scan channels. Also it didnt have information for the UK, the nearest info being Ireland. When the system boots into Mythtv, I cant watch TV, an error message tells me that "all inputs are being used". 
When I look into the setup pages, its all a foreign language to me!
I have heard many good things about Mythbuntu for building HTPC boxes but I am getting very confused at the first hurdle.
Please could you help me.

Many thanks  C152flying

"all inputs are being used"  also means you have no inputs :-)  

OK, so tuner cards are handled by the backend, and are set up in the mythtv-setup program for the backend.  For a fully supported card, you choose the card type from the top pull down menu - DVBT in your (and my) case.  The other pull down should then show each card of that type that linux has found present in your system.  I have 3.  Each one is added, one at a time.

It is important to select the right country in the 'general' settings for the backend, first, so that the correct set of frequencies, and other setup is used for the scan.  There is a "try-all" choice for the country - will that work?

---

