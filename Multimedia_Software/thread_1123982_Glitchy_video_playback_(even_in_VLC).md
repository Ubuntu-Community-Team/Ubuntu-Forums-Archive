---
title: "Glitchy video playback (even in VLC)"
date: 2009-04-12
forum: Multimedia Software
---

### Post by Acoustyk on 2009-04-12
Hey guys,

I've had this problem for awhile and have dealt with it but I've recently been getting fed up with it.  I, sadly, think that all is lost because I have an ATI card but I figured you all could help me out.

When I play back video (yes using VLC) it tends to be glitchy.  It will often run for awhile before tearing and freezing.  It usually fixes itself after maybe 10 seconds but that is incredibly annoying so I am usually forced to pause and unpause quickly so that the video will sync up properly.

I have this problem with all file types, even avis, and have no idea what the problem is or if it can be fixed.  Also, HD video playback is practically impossible.  (Res too small for 1080, but 720 should work)

I have installed medibuntu repositories, have all codecs, and I am not running compiz or 3D effects.  If you need more info let me know because I am hoping for a solution.  If not I am sadly looking back towards at least a dual boot with windows to work around the problem.  If there is another distro that will not have this problem I am open to that as well.  (I am currently looking into Fedora)

I have been dual booting Ubuntu since Edgy and have been 100% Ubuntu since the Hardy release.

Thanks for any help!

---

### Post by soltanis on 2009-04-13
What's your RAM usage like? Maybe another application is sapping all your memory and degrading the performance of your media playback.

---

### Post by Acoustyk on 2009-04-13
I usually keep the amount of programs running pretty sparse when I'm watching a video for that reason.  The only resource "heavy" programs running would be Firefox (62 megs) and Deluge (less), but I don't usually run those.  Nothing more resource heavy than firefox is running and the smaller background programs are pretty much the bare necessities with the exceptions of dropbox and gnome-do.

---

### Post by Acoustyk on 2009-04-14
bump

---

### Post by wolfen69 on 2009-04-14
are you using the ati drivers? if you don't need 3D or compiz, uninstall the drivers and go with the default ones.

---

### Post by Acoustyk on 2009-04-14
@wolfen69

I uninstalled the drivers and I'm using the standard ones now but it's still pretty rigid playback.  I wouldn't say that it really made it any better.

---

### Post by conorsulli on 2009-04-14
do you want to try different playback options?? such as xv  or opengl??There is sefinatley an option to change this under The generic plain Mplayer, I think Vlc can do it too but im not sure..

---

### Post by celem on 2009-04-14
My experience, for whatever it's worth. I ran around and around with the same issue with a Biostar TF8200A2+'s integrated Nvidia video (Yes, I see that you are using ATI). I finally gave up and put XP on that box, which worked perfectly. Anyway, the problem was that this motherboard used a combination of support chips and Nvidia chips that wasn't really supported by Linux, even though this Nvidia chipset was individually supported. Anyway, my point is that the COMBINATION of support chips AND the video chips MUST be supported. Bottom line, you may have to do what I did - use a different motherboard - preferably a more Linux friendly one than Biostar.
Good Luck!

---

### Post by elevashun on 2009-04-15
I too are having similar issues with video playback. I am experiencing occasional video pauses / sound stutters when playing videos in VLC player. 

My rig is a similar Dell laptop with an x300 ATI video card with the most recent drivers. 

Would there be any correlation with the sound stuttering at random points?

---

### Post by Acoustyk on 2009-04-21
@ Celem
I was kind of scared that this was the root of the problem and have been hoping that there the problem could be solved without the "aide" of installing XP.  I suppose this a lost cause but if anyone has solved this problem on Dell hardware I'm all ears.  I hope Jaunty will make some headway on this issue but I don't anticipate it.  

@elevashun
If you find a solution please let me know!

---

