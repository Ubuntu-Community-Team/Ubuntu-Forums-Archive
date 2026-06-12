---
title: "Trouble Watching Videos"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by nullfactor on 2007-06-05
I'm not sure what hardware info you need to troubleshoot this, so let me know, I'll get it for you.  The problem is, when I attempt to watch videos, I either get a blank video player (I hear sound, but no picture), or I get an annoying green bar that takes up 25% of the picture and the video is shoved down so only 75% of the picture shows.

I've tried watching video through Movie Player and VLC... they both have the same issue.

Any help would be mucho appreciated.

_dan

---

### Post by mainalisuyog on 2007-06-05
Which video card are you using? I used to have similar problem with savage video cards, but then i got a nvidia card and everything's fine.

---

### Post by nullfactor on 2007-06-05
Hi... thanks for the reply.  I'm using a Toshiba Satellite notebook.  If I do a "lspci", I find the following lines:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Expr
ess Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Exp
ress Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express In
tegrated Graphics Controller (rev 03)
```

Seeing that it's a laptop, I can't think of any good ways of upgrading the video, unfortunately.

Thanks again for the reply.

_dan

---

### Post by mainalisuyog on 2007-06-06
Intel graphics card should work without driver problems. I am sorry i don't know much about laptops. Are you running something like gdesklets, superkaramba or something that refreshes every few seconds? Try playing video after disabling any such programs. Maybe it will help.

---

### Post by nullfactor on 2007-06-06
Yeah... Intel devices usually work pretty good with Linux distros.

The only thing I can think of that I have running that may affect the video is Beryl-Manager.  I disabled that to see if that was interfering with the video playback... no difference.  Maybe I'll mess around with various resolutions.  Or do you think that's a lost cause?

Thanks!

---

### Post by mainalisuyog on 2007-06-06
Nothing is a lost cause. There's a solution to every problem. Yes, you should try changing the resolutions and colour depths. Maybe that will help. or you could try reconfiguring your xorg again with sudo dpkg-reconfigure xserver-xorg

---

### Post by nullfactor on 2007-06-06
Awesome... I thought I was the only one who used the "there's a solution to every problem" phrase!  I'll give the resolution experimentation and the Xorg reconfig a try and post my findings.  Thanks for sticking with it!

_dan

---

### Post by nullfactor on 2007-06-06
Nope... reconfiguring X and resolutions/color depth changes proved unsuccessful.  Any other ideas I can try?  Thanks again.

---

### Post by nphx on 2007-06-25
VLC > Settings > Preferences > click Advanced options > Video > Output modules > Select alternative from Default, try out some other modules and see which one works best. Remember to click on Save after making changes.

---

