---
title: "ATI Catalyst 10.7 is out. Anyone else tried it?"
date: 2010-07-27
forum: Multimedia Software
---

### Post by alphacrucis2 on 2010-07-27
I downloaded it from the AMD website but found that running the installer using --buildpkg Ubuntu/lucid doesn't seem to work to create the deb files. I gave up and just did a straight install, which means that the package manager is out of step. Oh well (shrug). The earlier 10.6 fixed the old slow window restore problem when running desktop effects and seemed generally faster all round but introduced an odd issue of webpage divs sometimes displaying as black rectangles in Firefox. Well I haven't seen this issue at all in 10.7. I think this version ought to replace the version 10.5 that Ubuntu have in the Lucid repos which has the annoying slow window restore bug. 

FYI I'm running an HD 3400 GPU. YMMV with other GPU's.

---

### Post by robotman5 on 2010-07-27
let me bump this for you;)

---

### Post by Scibax on 2010-07-29
I have installed it but catalyst is still reporting version 10.6 with driver version 7.23.  I have purged and reinstalled several times and it is still the same, 10.7 and driver version 7.53 never show in the control center.

---

### Post by smoosh on 2010-07-31
I upgraded from 10.5, and got the same issue as Scibax, where the Catalyst Control Center tells me I'm running 10.5 instead of 10.7. 

Other than that, it's OK. I was using the backclear patched Xserver before and now have upgraded to the standard issue xserver-common and xserver-xorg-core, and am seeing a little of the grey box syndrome in Chromium, but not bad enough for me to downgrade. Yet. Videos play great full screen with no tearing, so that's good...

---

### Post by smoosh on 2010-07-31
Just tried firefox, no grey boxes! Maybe I will switch back...

---

### Post by ZBlue on 2010-07-31
> **smoosh said:**
> I upgraded from 10.5, and got the same issue as Scibax, where the Catalyst Control Center tells me I'm running 10.5 instead of 10.7. 

Other than that, it's OK. I was using the backclear patched Xserver before and now have upgraded to the standard issue xserver-common and xserver-xorg-core, and am seeing a little of the grey box syndrome in Chromium, but not bad enough for me to downgrade. Yet. Videos play great full screen with no tearing, so that's good...


i'm not sure what patches you are referring to but can you confirm that the 10.5 drivers don't have the usual screen tearing problem in Ubuntu 10.04 ? I'm using an HD4870 and have horrible screen tearing in movies and even while moving stuff around on my desktop. 

i currently get this version from terminal :

```
 ATI Proprietary Linux Driver Version Identifier:8.72.11
```

---

### Post by chaos_efphect on 2010-07-31
Well i just tired it and i lose compiz, so am i the only one that issue happened to?

---

### Post by hamidoo on 2010-08-01
I tried v 10.7 and by the the way u can generate the debs from the installer gui (NOT the command line).

The terrible thing is that the delay bug prior to 10.6 reappears again!
but occasionally.

I also got reported that it's version 10.6!!
I ve attached a shot of my catalyst info.

Another thing, to view the actual catalyst version type this in terminal

```

grep "ATI .* Driver" /var/log/Xorg.0.log

```

The output of the above command is with catalyst 10.6 (NOT 10.7) is:
```

(II) [COLOR="Red"]ATI Proprietary Linux Driver[/COLOR] Version Identifier:8.74.4
(II) [COLOR="Red"]ATI Proprietary Linux Driver[/COLOR] Release Identifier: 8.741                                
(II) [COLOR="Red"]ATI Proprietary Linux Driver[/COLOR] Build Date: May 27 2010 12:52:28

```

---

### Post by Padakwaak on 2010-08-02
I really don't know what AMD did with this release. When you are on the download page, the name says 10.6, but the version says 10.7.

I've actually managed to get Catalyst 10.7 going on my Ubuntu 10.04 x64 with my Radeon HD5670, but I really struggled to get it working. Now I don't have the messed up login screen (where I used to switch between tty1 and tty7 to fix it) that I had with 10.6. My OpenArena is working again at like 400fps+, so I'm happy :D

After I ran the 10.7 setup and rebooted Ubuntu, it didn't want to load X11! I've tried to install 10.5 & 10.6 again, but neither of them worked. I tried installing the xserver-xorg-video-ati/xserver-xorg-video-radeon/fglrx packages and none of them worked either.
I think I might've fixed it by deleting /usr/share/ati and then running the 10.7 setup and using the recommended, not distro dependent settings.
The distro dependent (Ubuntu/lucid) also failed to build.

---

### Post by rockdj on 2010-08-04
Installed the 10.7 drivers for my HD 2400 XT and I'm having major issues with OpenGL and Compiz being enabled.  When running any OpenGL application (eg glxgears) when Compiz is enabled, the output flickers severely -- almost like it's tearing the output.  Enabling 'Sync to VBlank' on both Compiz and in the Catalyst control centre doesn't make any difference.  

Disabling Compiz makes things fine, and interestingly, any OpenGL apps that I've got left open when I try and enable Compiz again continue working fine.

Didn't have this trouble on 10.6, and none of any of the vertical sync options were enabled.

---

### Post by djscribe on 2010-08-23
Onboard HD4290 512 DDR5 on an:
ASUS M4A89GTD PRO USB3 mobo
AMD 890GX chipset

Had Lucid native drivers and all worked except for the Cairo Clock in OpenGL among some other trivial OpenGL rendering, but I figured since this is a new PC, I wanted everything working. Well, loaded new ATI 10.7 drivers and now have no OpenGL. Although I haven't done extensive testing, even opening Cairo OpenGL crashes PC [irrecoverable freeze requiring hard boot]. 

Still researching - anyone please let us know if there is a workaround. I've tried rolling back to previous driver to no avail.

Results from running $ **grep "ATI .*Driver" /var/log/Xorg.0./log** in term:

(II) [COLOR="Red"]ATI Proprietary Linux Driver[/COLOR] Version Identifier:8.75.5
(II) [COLOR="Red"]ATI Proprietary Linux Driver[/COLOR] Release Identifier: 8.753                                
(II) [COLOR="Red"]ATI Proprietary Linux Driver[/COLOR] Build Date: Jun 29 2010 22:08:06

---

### Post by djscribe on 2010-08-23
Went back to native drivers until ATI gets their act straight. I'd rather have 50% OpenGL than none.

...

---

### Post by hamidoo on 2010-08-29
ok guys, 10.8 IS OUT!

So far it is AWESOME!! 

No windows delay, no black window bug!

At last, a descent driver from ATI

version info command:```
grep "ATI .* Driver" /var/log/Xorg.0.log
```

Result

```

(II) [COLOR="Red"]ATI Proprietary Linux Driver[/COLOR] Version Identifier:8.76.7
(II) [COLOR="Red"]ATI Proprietary Linux Driver[/COLOR] Release Identifier: 8.762                                
(II) [COLOR="Red"]ATI Proprietary Linux Driver[/COLOR] Build Date: Aug  3 2010 21:16:01

```

---

### Post by 0004tom on 2010-08-29
> **hamidoo said:**
> ok guys, 10.8 IS OUT!

So far it is AWESOME!! 

No windows delay, no black window bug!

At last, a descent driver from ATI

Really? within 10 minutes after installing I My unified floders in Thunderbird went black. Within an hour and opening a preference window guess what, black borders...

---

### Post by hamidoo on 2010-08-29
ooh, it works gr8 for me
been using it for 2 days with standby, and never seen black borders!

did u intall it from the generated debs?
and did u run "aticonfig --initial" after installing it?

---

### Post by yopensource on 2010-08-30
```
$ grep "ATI .*Driver" /var/log/Xorg.0.log
(II) ATI Proprietary Linux Driver Version Identifier:8.76.7
(II) ATI Proprietary Linux Driver Release Identifier: 8.762                                
(II) ATI Proprietary Linux Driver Build Date: Aug  3 2010 21:16:01
```

I still have problem with back windows issue in thunderbird. :confused:

---

