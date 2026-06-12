---
title: "KDE 4.5 Beta 1 - Xine broken ?"
date: 2010-05-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by vikrant82 on 2010-05-31
Is there anyone on kubuntu kde packages ? Looks like after recent updates to xine or with kde 4.5 beta packages, phonon is no longer working with xine backend. Can anyone else confirm the same ?

[Related thread in kde forums.]("http://forum.kde.org/viewtopic.php?f=19&t=88211")

---

### Post by tretle on 2010-05-31
confirmed

---

### Post by vikrant82 on 2010-05-31
[https://bugs.kde.org/show_bug.cgi?id=240255](https://bugs.kde.org/show_bug.cgi?id=240255)

Is that the right place to raise this bug ? Or it could be a packaging issue with Kubuntu packages ?

---

### Post by vikrant82 on 2010-05-31
OK after 2 hours of playing. Some more issues:

1. KDM greeter - Cannot change desktop manager.
2. Tray icons right click doesn't bring out application menu - observed with kalarm, kopete.
3. The add new widget strip is misplaced with compiz, {20% of it goes below bottom edge of screen, if panel is on auto hide}

---

### Post by Mamarok on 2010-05-31
Please report on Launchpad, this is likely a packaging problem

---

### Post by Mamarok on 2010-05-31
There is a big label that sais "beta", what do you expect? The forum is not the right place to report any issues, please report to either Launchpad or KDE's bugzilla

---

### Post by caryb on 2010-05-31
> **Mamarok said:**
> There is a big label that sais "beta", what do you expect? The forum is not the right place to report any issues, please report to either Launchpad or KDE's bugzilla

Sorry to disagree but all MM is Alpha or Beta at this point of time! Do you suggest we don't post any issues?

For my part I now know i'm not on my own & will contribute to the bug in Launchpad.

Cary

---

### Post by Reiger on 2010-05-31
> **vikrant82 said:**
> OK after 2 hours of playing. Some more issues:

1. KDM greeter - Cannot change desktop manager.
2. Tray icons right click doesn't bring out application menu - observed with kalarm, kopete.
3. The add new widget strip is misplaced with compiz, {20% of it goes below bottom edge of screen, if panel is on auto hide}

(1) There is a bug in the KDM package itself, the installation/update script which handles the KDM user account fails to chown /var/lib/kdm to have the appropriate ownership settings. So, as a result your system log will contain things like:
```

2010-06-01 02:47:18	akron	kdm_greet[1334]	Data directory "/var/lib/kdm" not accessible: Permission denied
2010-06-01 02:47:18	akron	kdm_greet[1334]	Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: No such file or directory

```
I'll be reporting a bug on launchpad if the server will cooperate for a moment... 

(2) Left click? IOW: works for me with network manager, klipper, kmix, power management etc.

(3) Works for me with KDM/KWin ?

---

### Post by xebian on 2010-05-31
> **vikrant82 said:**
> Is there anyone on kubuntu kde packages ? Looks like after recent updates to xine or with kde 4.5 beta packages, phonon is no longer working with xine backend. Can anyone else confirm the same ?

[Related thread in kde forums.]("http://forum.kde.org/viewtopic.php?f=19&t=88211")

Not sure if the timing has anything to do but just upgraded a few moments ago and I would say amarok 2.3.1 now rocks even better.  I stick with kde- phonon, no pulseaudio if that makes sense.

No compiz, but windows seems sluggish right now, understanble though.

---

### Post by Reiger on 2010-05-31
It doesn't make sense (phonon and pulseaudio are two completely different things, they don't even try to do the same thing). It will also be false once the Kubuntu developers get round to installing pulseaudio as part of the default installation:

[https://wiki.kubuntu.org/KubuntuMaverickKDEPackaging](https://wiki.kubuntu.org/KubuntuMaverickKDEPackaging)

---

### Post by vikrant82 on 2010-06-01
> (2) Left click? IOW: works for me with network manager, klipper, kmix, power management etc.

(3) Works for me with KDM/KWin ?

2. Yes, left click works for these. As I said, its happening for only certain applications like kalarm, amarok. Can you try, right clicking in tray icon for amarok, right clicking the tray icon doesn't bring up the application menu.

3. Yes, it works fine with Kwin. Issue is observed while running KDE with compiz. 

I have observed, with Kwin my graphics suffers. Although this is not benchmark test, but with Kwin, glxgears gives 2300 frames in 5 s, while with compiz i get upto 4200 frames in 5 s. 

Try KDE with compiz and see how snappy it feels, if you have a 3-4 year old machine like me.

---

### Post by Reiger on 2010-06-01
(2) No right click doesn't do anything for amarok, left click however brings up the entire window itself.

But right now my tray is a mess. It seems someone thought it a good idea to make the icons translucent and monochrome (white with grey outlines) and make the symbols look like they come from a GTK package. Suffice to say that it looks *horrible* on a white translucent panel, especially compared to the much more sophisticated icons of the previous iteration.

---

### Post by xebian on 2010-06-01
Fresh install from netboot image is working great- kde composting, amarok, xine1. Right click on apps on the systray is working fine.

---

### Post by vikrant82 on 2010-06-02
> **xebian said:**
> Fresh install from netboot image is working great- kde composting, amarok, xine1. Right click on apps on the systray is working fine.

Tried with fresh users on two different machines. Now that's not good.

---

### Post by wayneericgouin on 2010-06-02
In addition plasma crashes when using the Quick access browser, for me anyway.

---

### Post by Reiger on 2010-06-02
Some more digging into KDE 4.5 announcement type posts/articles; & systemtray stuff; the following might be useful:

(a) There's a new protocol for the system tray, which is how they do the new system tray features. It may be that Amarok etc. simply need to be patched to use the new protocol.
(b) The icons I dislike so much are svgz files in /usr/share/kde4/apps/desktoptheme/default/icons

---

### Post by vikrant82 on 2010-06-05
> OK after 2 hours of playing. Some more issues:

1. KDM greeter - Cannot change desktop manager.
2. Tray icons right click doesn't bring out application menu - observed with kalarm, kopete.
3. The add new widget strip is misplaced with compiz, {20% of it goes below bottom edge of screen, if panel is on auto hide}

OK the third one is fixed, with compiz 0.8.6. Looks like they added some KDE improvements.

But the phonon problem is getting irritating, as with gstreamer backend, the sound stutters here and there. Specially in amarok when it proceeds to next track, the sound stutters for 10-30 seconds before stabilizing.

Phonon-vlc backend is crashing like hell.

Phonon-mplayer works perfectly but, amarok loses its ability to seek in seekbar etc.. 

Ok so, how do we go about finding what's wrong with xine ? Nothing in amarok logs, when it fails to play. Where else can we look ?

EDIT: [https://bugs.launchpad.net/ubuntu/+source/phonon-backends/+bug/590244](https://bugs.launchpad.net/ubuntu/+source/phonon-backends/+bug/590244)

---

### Post by seeker5528 on 2010-06-05
Works fine for me, but then again I never saw a reason to screw up a perfectly good system by having a bunch of pulse-audio crap installed. :P ;)

Later, Seeker

---

### Post by vikrant82 on 2010-06-08
Sweet! Xine issue is fixed with latest updates on version,  4:4.7.0really4.4.2-0ubuntu1 of phonon related packages.

---

