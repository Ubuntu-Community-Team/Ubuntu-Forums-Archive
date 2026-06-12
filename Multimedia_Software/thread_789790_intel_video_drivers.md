---
title: "intel video drivers"
date: 2008-05-10
forum: Multimedia Software
---

### Post by spudratic on 2008-05-10
Any one had any luck finding a fix for intel chip sets drivers.I run the 845g chip on P4 2gigs ram.The trouble is with compiz running and playing a video my cpu use is between 80% and 90% and that is all i can do.opening any other program causes the whole system to lag sound goes garbled.In gusty I could play 2 videos muted an album and have 3 web browsers open and the text editor with no trouble.I know we switched from xaa to exa for the driver.the ? is why would you have people use it if it is so bad.Should have left it xaa just like it was in gusty till it was all worked out.I can not change to the modsetting intel driver I get a black screen and error at reboot.This  i810 driver was crap for me in gusty also with this same sort of problem.So far I tried the proposed update for the driver did nothing no difference,also tried the debian driver which really slowed things down,

Is there a way to make hardy run in xaa like it did in gusty.tried to edit the xorg.conf file but it seems to make no difference same crappy performance which leads me to belive it's the driver and or xorg.My money is on the driver being fubar.


Can I compile the driver directy from the intel site? .I assume I can but I need a good set of instructions.It will be my first time for some thing like this.

If this is beyond me,can anyone recommend a distro with good intel support.I would go back to gusty but that is going backwards.been thinking of trying pclos 2008.Ran the live cd for a few weeks seems very stable,but so was gusty in live cd worked fine then  you install it and have all sorts of problems.

any help info thanks

Update: installed all proposed updates no help at all.cube rotation is slower and videos still run high cpu rates, to high.

---

### Post by spudratic on 2008-05-11
bunp

---

### Post by Yellow Pasque on 2008-05-11
The intel driver has very good performance for the hardware. Keep in mind that the chipset was designed for light Vista/Aero usage. Asking it to do full-fledged Compiz with spinning cube is a bit much.

If you really want the eye candy and you have a desktop with an AGP slot, then I would suggest an inexpensive nvidia 7300-series card.

---

### Post by spudratic on 2008-05-11
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492) Temüjin read this and then tell me how great it is roflmao.anyone else any help from anyone?

---

### Post by Yellow Pasque on 2008-05-11
Please spare me your indignant attitude. If you think the intel drivers should be more efficient, then I encourage you to participate in the Launchpad link you found, but don't get angry at the developers for giving you free support.

---

### Post by spudratic on 2008-05-11
I'm not angry per say just pointing out the problem to you.I do appreciate their hard work and yours for at least answering me.the fact intel was ok the way it was set up in gusty worked fine.I think they changed it because of the new xsever(not sure)but the fact is intel support at this point for me is fubar.


what I am angry at is this bug has beem there right from the beginning all through testing and released anyway with no warning at all.If I found the bug sooner I would have waited gusty was fine for me.the only thing I found on hardy before the release on intel was that the intel chip sets were fully supported for hardy.which is why I upgrade(which failed by the way).this tout of full support of intel chips is nothing more than a bold faced lie.telling lies pisses me off for sure.

I'm sorry if I offended you by pointing out your mistake of intel support.No offense was intended.the simple fact is if you go around saying that intel drivers are ok when they really are not just causes more confusion agian sorry.I must admit I am a little pissed after one failed upgrade and 3 reinstall's to try and figure this out.It was a waste of time and effort on my part since I guess nothing could be done at this time.

---

