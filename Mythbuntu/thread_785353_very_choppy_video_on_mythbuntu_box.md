---
title: "very choppy video on mythbuntu box"
date: 2008-05-07
forum: Mythbuntu
---

### Post by kameleon25 on 2008-05-07
I am having a little issue with video playback on my mythbuntu 8.04 box. No matter what video player I try (xine, mplayer, Internal, VLC) or even live TV it plays like one frame a second. But when I go to choose a pre-recorded show the "preview" in the bottom right shows at a full framerate. This has me boggled. I have a Gigabyte motherboard with the 690G chipset (ATI Xpress 1250 video IIRC) and had video working fine before the upgrade from 7.10. Could it be that I need to reinstall the video drivers?

---

### Post by metallocene on 2008-05-08
Deja vu.  

My Biostar 690G board has exactly the same issues,  I as soon as I upgraded to 8.04 on the weekend, the recordings and live TV stutter, single image every 2-3 seconds(strangely the sound doesn't) but the preview video in the recordings library plays perfectly.  

Totem plays DVD's no problem.

I've Google'd a lot but have yet to come up with a solution.   

I've:
  - loaded the latest ATI drivers but no luck.
  - tried a lot of different resolutions and refresh rates
  - made many backend and frontend changes

Mythbuntu was great on Gutsy,  so far no luck with the bird.

Any other 690G users, have the same issue?

---

### Post by slund on 2008-05-15
I got the same problem with 8.04 (new user though) and having installed a diskless client i was wondering if that would have something to do with things. 

Other posts talk about dma being needed on harddrives and rom drives, in order to get smooth playback, others say processor priority on the mythfrontend needs to be high to improve playback, but to no avail so far.

I will also be trudging on trying to find an answer. I was going to re-install a harddrive in my frontend, but I guess that would make no difference, reading the previous posts.

S.

---

### Post by kameleon25 on 2008-05-15
I have found that mplayer and xine both will play relativly decent if in a small window on the desktop. But vlc is the only one that will do full screen worth a darn. The internal player is even very choppy. I am leaning toward it being my video drivers although they should not have been overwritten since they were straight from source before the upgrade.

---

### Post by copycat on 2008-05-15
Same here,

did somebody already found a solution.
I had alread a view on de DMA... it is only when you have a IDE drive.  For sata it isn't a setting.

I wish a didn't upgrade it.
DVD is also not working fine (that's why I upgraded)

kind regards,

Christian:popcorn:

---

### Post by metallocene on 2008-05-16
I checked the DMA settings on mine as well, were fine.  

Got desperate yesterday and installed an NVIDIA video card from another system.   After 2 reboots Mythbuntu worked like a charm,  could watch all the recordings again.

Thus it looks like yet another ATI (AMD) driver issue (the 690G uses intergrated graphics from ATI).   Bummer, I like supporting the underdog but I may end up buying an NVIDIA card for this system.

Will hold off a bit and see if any new AMD driver fix the issue.

Sorry to hear that there are others in the same boat, but nice not to be alone...

---

### Post by kameleon25 on 2008-05-16
Yes it does appear to be the infamous ATI driver issue. While I, like a previous poster, like to support the underdog I am looking at getting an nVidia chipset card. I am actually looking at this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814125062](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125062) Seems to be reasonably priced, is a name I trust, and has the component output that i need to hook into my sharp Aquos 42" lcd. I will keep you guys updated.

---

### Post by copycat on 2008-05-16
Downgraden to 7.10 (fresh install) again. My records are backupped buth the nam doesn't tell anything except for the date and time they where recorded.

My wife and kids are already asking to set XP MCE backup ... NOW WAY...:guitar:

---

### Post by metallocene on 2008-08-24
Yep,  going back to 7.10 Ubuntu (the Gusty G) and reloading MythTv did the trick as well.   Video playback to the VGA monitor is great.

S- Video playback to our TV,  is now a black screen though... (Bios info shows up but nothing for Ubuntu).   At least the monitor works.

Seems to always be something with this ATI 690G and linux.

---

