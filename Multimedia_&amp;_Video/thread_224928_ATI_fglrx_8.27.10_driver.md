---
title: "ATI fglrx 8.27.10 driver"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by pRedat0r on 2006-07-28
Anyone get this driver installed and see how it works?  It says it is compatible with Xorg 7.1 now and fixed a screen 0 issue with XGL.

If you have tried this please let everyone know how it works, how you installed it, and if it fixed any issues for you / caused new ones..

Thanks!

---

### Post by d3viou5 on 2006-07-29
I just installed these drivers following the instructions provided here:

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

So far everything is working fine.  Just for the record I have an ATI 9800 Pro and am running Xorg 7.0.  I'll report back if I discover any issues.

---

### Post by Eversmann on 2006-07-29
Working fine in my laptop using Xpress200M. Still have the usb ports freeze after a while, but running ok.

---

### Post by Treviño on 2006-07-29
Anyone is running XGL here?

From release notes we can read

> #  Resolution of an XGL startup issue that prevented users from starting XGL on display :0. Further details can be found in topic number 737-22841
 Who can try it?
I'm still running XGL in :1... -_-

---

### Post by plutoprime on 2006-07-29
I tried it and used the :0 with the second method in the XGL howto. And NO .. it still doesn't work. Not only that but I get the mesa spew when running XGL on :1 .. as soon as I start a normal X session I get:

```
xxx@Aida:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.5946 (8.27.10)
```

Obviously works flawlessly without XGL... I have given up on ATI ... why this incremental release of broken drivers?? Wait 3 months, hire some decent driver developers and release a polished product.

---

### Post by ltmon on 2006-07-29
> **plutoprime said:**
> 
Obviously works flawlessly without XGL... I have given up on ATI ... why this incremental release of broken drivers?? Wait 3 months, hire some decent driver developers and release a polished product.

That's pretty harsh on the ATI driver developers :)

I'm not sure you can legitimately bash them for not having flawless support for an experimental X server that has not yet stabilised and has only been in public view for < 6 months in any case.  Especially when you said yourself that they "obviously work flawlessly" in a standard setup.

You might have noticed that they have accelerated their linux driver development considerably over the last year.  They should be applauded for that at least.

I used to be an ATI hater, but I think their new monthly release policy has led to much better drivers.  They currently arguably have more usable features than any other driver (dynamic display management comes to mind), have better installation and integration with distributions than any other closed source driver (their graphical installer is much better than nvidia's) and have been quite stable in a standard single X server configuration for a long time now.

Of course there is room to improve: increasing delivered frame rates to what you hardware can actually output, fixing the suspend-to-RAM hacks we all have to make and supporting their newest products quicker are the big things.

Increasing support for Xgl and AIGLX (glx_render_from_pixmap or whatever it is that's holding this up) is probably low on most of their users' priority list compared to the above.

L.

---

### Post by nimrod_abing on 2006-07-30
Anyone here using an R9200 card?

Does hardware accelerated OpenGL work with this new driver?

With the default package from the dapper repos, libGL.so is broken for R9200 cards.

---

### Post by robinlennox on 2006-07-30
I am a complete noob to Linux, I am a windows users from 3.1, so I thought i would try this... 

Great, only disappointment is that there are no deb for my ati card... i know there is a command line version. But tried that a few times didn't work so give up!

Great to see Linux, finally has the ultimate kill app! The exe (deb)!, come on ATI make some deb for us windows user wanting to migrate, can!

Hey All!

---

### Post by Treviño on 2006-07-30
> **plutoprime said:**
> I tried it and used the :0 with the second method in the XGL howto. And NO .. it still doesn't work. Not only that but I get the mesa spew when running XGL on :1 .. as soon as I start a normal X session I get:

```
xxx@Aida:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.5946 (8.27.10)
```

Obviously works flawlessly without XGL... I have given up on ATI ... why this incremental release of broken drivers?? Wait 3 months, hire some decent driver developers and release a polished product.
Well... I've tried to... No way to get fglrx working on Xgl in dispaly :0...
Both using KDM and GDM I always get Mesa drivers... So XGL loads using software OpenGL emulation I think, anyway no DRI available...

So I'm still running XGL in :1, and also in my PC fglrxinfo gives the same output, but to get the "old" one you should run fglrxinfo -display :1, and you'll get the well known message :(
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.2 (2.0.5946 (8.27.10))
```
So... Who knows what ATi is talking about when they state that this driver will solve the display :0 issue.

Anyway I know people that with older drivers were able to... Is there anyone who is using fglrx + XGL in :0 ?

Thanks!

---

### Post by Darth Tux on 2006-07-30
> **nimrod_abing said:**
> Anyone here using an R9200 card?
Does hardware accelerated OpenGL work with this new driver?
With the default package from the dapper repos, libGL.so is broken for R9200 cards.

Yea, i have a 9200,.....and sad to say, its still broken for us. I was hoping they would have fixed it by now.:-(

---

### Post by ktx on 2006-07-30
still no dri :(
no compositor in xfce
openGL works tho'

(i have a 9200)

---

### Post by Burkey on 2006-07-30
Not using xgl or anything fancy (I would love to but I understand it will nerf my opengl apps and games)

Otherwise installed fine (same as all releases recently) however glxgears -printfps only give me 125fps now!  I am guessing it is locked to the vsync (running laptop with X1400 on LCD) or something, just wondering if anyone else saw this?

Yes, I know glxgears is not a benchmark, I just am using it for indicative purposes... ut2004 is working fine

---

### Post by hypersonic5 on 2006-07-31
Wait, do these fix the problems with the Xpress 200M series cards?

---

### Post by rippon on 2006-08-01
I have these drivers installed, but I am only getting around 125fps in glxgears. What the heck! Any one know a solution?

---

### Post by tauko on 2006-08-01
There are a few people who have the same problem: when trying to create the debs packages it breaks with an error.

```
dpkg: /usr/i486-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/i486-linux-gnu/lib/libstdc++.so.5 not found.
dpkg: /usr/i486-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libgcc_s.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libc.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libdl.so.2 not found.
dpkg: /usr/i486-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libGL.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libXrandr.so.2 not found.
dpkg: /usr/i486-linux-gnu/lib/libXrender.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libfglrx_gamma.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
```

Followed the instructions on [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually")

Running Dapper with kernel 2.6.15-26-686 #1 SMP PREEMPT, on a i686 Laptop. Graphic card is ATI mobility radeon 9700.

Any ideas?


**UPGRADE:**
Well, the problem has been solved. It seems that it was trying to cross-compile. I removed the package *dpkg-cross* and now it works. Note also that I removed also others packages like the restricted-modules.

Hope it helps someone!

---

### Post by pRedat0r on 2006-08-02
I just installed the driver last night, dont seem to have any problems with it that werent present in the previous versions.  My LCD monitor still remains blank once it goes to sleep, or I turn it off, but that is fixed with flipping to a virtual console and back to the desktop quickly (annoying, but less annoying than WGA in windows).  I havent noticed any fixes to the issues that I had, I think there are still quirks in the big desktop mode, GL Apps (glxgears) seem to display only on the left side of the windows, etc.  Might give XGL a try again later to see if it can even start -- I get no screens found when I try to start that up (same thing following any tutorial on getting that running, but im betting it is related to the big desktop mode).

Anyone else have any outstanding issues fixed?  On the plus note, the transparency issue in the gnome panels was fixed in the last rollup of updates (not related to fglrx).  previously the transparent section had a colored hue -- apparently depending on something in the background wallpaper (some wallpapers caused a different hue in the transparent section -- it looked very ugly).

---

### Post by gustl87 on 2006-08-04
the driver does not support the ati M6 chip ! how old is this chip now ? and they still got no working driver ?

the "ati" or "radeon" drivers are buggy (freezing) so i am still waiting for an bugfix in the "ati" driver or an better fglrx closed source driver from ati - but i know they won't wake me happy^^.

---

### Post by whatever on 2006-08-04
> **rippon said:**
> I have these drivers installed, but I am only getting around 125fps in glxgears. What the heck! Any one know a solution?

this is not a bug, so there is no need for a solution.
[http://rage3d.com/board/showpost.php?p=1334478409&postcount=24](http://rage3d.com/board/showpost.php?p=1334478409&postcount=24)

---

### Post by disciple on 2006-10-14
> **tauko said:**
> 

Hope it helps someone!

it helped me.. !!!!!   after i removed dpkg-cross, i was able to compile again.  dont know where i picked it up, tho.. 

thanx

---

### Post by clau85 on 2007-12-01
> 
**UPGRADE:**
Well, the problem has been solved. It seems that it was trying to cross-compile. I removed the package *dpkg-cross* and now it works. Note also that I removed also others packages like the restricted-modules.

Hope it helps someone!

Thanks! Had the same problem and yours was the only solution I found. I also removed dpkg-cross and it worked. I wouldn't have ever thought of doing that...
Thanks again

---

