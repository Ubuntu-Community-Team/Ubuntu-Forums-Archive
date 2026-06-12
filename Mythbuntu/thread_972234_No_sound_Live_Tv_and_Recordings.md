---
title: "No sound Live Tv and Recordings"
date: 2008-11-05
forum: Mythbuntu
---

### Post by Rompalle on 2008-11-05
Hi Everyone,

As stated in the subject i have no sound for Live Tv & Recordings.

I have a Hauppauge WinTv PVR-150 MCE that has a Viewsonic STB connected to the Composite inputs on the PVR card. Video works but no sound. I know it does actually work since it use to when i was on a Windows system.

I checked the all the inputs on the mixer and they are all at max.

is there anything else i can check or do ?

thanks for any help.

---

### Post by mjezell on 2008-11-05
This may sound silly but I've made this mistake recently. In alsamixer below the graphic bars for volume there are small squares with either two "0"'s or two "M"'s in them. The MM's indicate that that paticular funtion is disabled and the OO's indicate that it is on. Hitting the M key on the keyboard taggles between them. Hope this helps.

---

### Post by Rompalle on 2008-11-05
> **mjezell said:**
> This may sound silly but I've made this mistake recently. In alsamixer below the graphic bars for volume there are small squares with either two "0"'s or two "M"'s in them. The MM's indicate that that paticular funtion is disabled and the OO's indicate that it is on. Hitting the M key on the keyboard taggles between them. Hope this helps.

thanks for the reply but i have no idea what your talking about.

also i have confirmed that it works outside of Mythtv by typing the following command.

mplayer /dev/video0

opens mplayer with live tv from my STB and there is sound !

so why does sound not work in Mythtv ?

---

### Post by Rompalle on 2008-11-06
i figured out my problem. So if anyone ever has the same issue with a STB here was my stupid mistake.

Since i have an optical out into my sound system i never use the volume on the STB, so guess what it was set all the way down!

volume up on the STB increases sound to the capture card. dumb mistake but i guess thats all part of the learning curve.

I also ran this from the command line to be sure.

```
amixer set Capture,0 100%,100% captur

```

---

