---
title: "Overscan adjustment"
date: 2010-07-20
forum: Mythbuntu
---

### Post by williammanda on 2010-07-20
I just replaced a bad Nvidia 7300 video card with a Zotac GeForce 8400 GS. Also I'm using the TV-out to a 25" crt TV. Every thing seems to work well but I'm getting overscan, the desktop or picture is larger than the screen. I can't seem to find where to make this adjustment. Any ideas?

---

### Post by endotherm on 2010-07-20
if it is there, it will appear in nvidia-settings under the node "CRT0" or "DFP0". hunt around a little, and hopefully it will be there. besure to run nvidia-settings with gksu.

the nvidia 8300-8600 are not 100% compatible with the nvidia drivers nowadays. I have had 2 8400/8500 cards that never provided overscan control in nvidia-settings, and what is worse, they ignored the setting if I put it in the xorg manually. 

one of my 8400 cards mysteriously gained overscan control with the restricted driver when I upgraded to lucid. which version of ubuntu are you on?

---

### Post by williammanda on 2010-07-20
Yes I'm running lucid. There is no setting for the overscan in the nvidia settings.

---

### Post by endotherm on 2010-07-20
as a workaround, I usually use smplayer. it has a zoom feature that is very useful, especially when watching something with subtitles. zooming out just shrinks the video a little on each side, so you should be able to find a setting that makes the whole video vissible.

---

### Post by williammanda on 2010-07-20
Thanks I appreciate that but I use this computer as a desktop too. So I would like to get the solution that fixes the overscan.

---

### Post by endotherm on 2010-07-20
> **williammanda said:**
> Thanks I appreciate that but I use this computer as a desktop too. So I would like to get the solution that fixes the overscan.
some people have had some success with creating custom modelines in their xorg to recalc the screen geometry, or tweak the hsynch/vref in the monitor section, but I'm afraid I can;t help you there. There is a tool called xvidtune that may help, but I never had any luck with it. I also found that sticking to NTSC-M resolution (720x480 I believe) did help matters (and made text readable) but was still never perfect.

you can try configing the overscan directly into the screen section of your xorg.conf, with a line like this
```

Option         "TVOverScan" "0.00000"
```where 0.0 is no overscan, and 1.0 is all overscan. 

good luck. in the end, after a full year fighting this, the best solution I found was to install my older but infinitely better 7950GT. it had OS control, and ran 45Deg C cooler.

---

### Post by williammanda on 2010-07-20
Well I was wrong. I went back for the 10th time and there was a slider bar to adjust the overscan. I have never seen that selection before. So after making that quick adjustment everything works fine.

---

