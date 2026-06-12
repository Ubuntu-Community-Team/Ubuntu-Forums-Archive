---
title: "ATI 8.6 Catalyst drivers are out"
date: 2008-06-18
forum: Multimedia Software
---

### Post by MadeR on 2008-06-18
but ubuntu uses a really older version

can anybody post here a step by step guide to create packages that exactly replace the official ones, with dependencies and everything?

---

### Post by markbuntu on 2008-06-18
If you want or need the newest driver from ATI you can download it from here:
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

The directions for installing it are here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Please use the search feature of the forums before starting a new thread. Many threads on the same subject fragment information and make it more difficult for people to find help.

---

### Post by Neo4 on 2008-06-18
well,

If I try to install it by just doing:

sh ati.....run --buildandinstall Ubuntu/hardy

at the end it gives me an erros saying that coulnt edit the xorg.conf

If I try like in that page tuturial no erros show but If i go to catalystic center it says 8.50.3 on the version! shouldn't it say 8.60?!

---

### Post by MadeR on 2008-06-19
I was simply wondering whether the howto really covers every necessary step or not.

---

### Post by mgbridges on 2008-06-19
I downloaded the 8.6 drivers and tried running the installer, but I get an error:
```
martin@Vetinari:~/Documents/Downloads$ ati-driver-installer-8-6-x86.x86_64.run
bash: ati-driver-installer-8-6-x86.x86_64.run: command not found
```

Any ideas? I'm using an AMD64 system with Gutsy.

Martin

---

### Post by Canis familiaris on 2008-06-19
Incorrect Post!
Sorry!

---

### Post by Canis familiaris on 2008-06-19
> **mgbridges said:**
> I downloaded the 8.6 drivers and tried running the installer, but I get an error:
```
martin@Vetinari:~/Documents/Downloads$ ati-driver-installer-8-6-x86.x86_64.run
bash: ati-driver-installer-8-6-x86.x86_64.run: command not found
```

Any ideas? I'm using an AMD64 system with Gutsy.

Martin
I installed the older driver using this method.

```
./ati-driver-installer-8-6 x86.x86_64.run --buildpkg Ubuntu/hardy

```
Replace Hardy by Gutsy if you use Gutsy
```

sudo dpkg -i fglrx-kernel-source*

```
```

sudo dpkg -i xorg-driver-fglrx_8*

```

If it works kindly reply and tell me if the ATi driver worked correctly the older driver gave problems to me.

---

### Post by mgbridges on 2008-06-19
This kinda worked. I replaced 'hardy' with 'gutsy' as I'm using Gutsy not Hardy and most of the installation went OK, but I was left with some broken packages.

Still can't get any desktop effects to work.

Martin

---

### Post by mgbridges on 2008-06-19
An update - I tried re-running the installation as originally directed by the ATI website and it now worked. I did the Automatic installation and it ran to completion successfully.

However, it maintains it has installed the 8.501 driver, not 8.6.

If I try to set Visual Effects (in the Appearance control panel) to anything other than None, I get a white screen then it goes back to None.

Martin

---

### Post by markbuntu on 2008-06-19
The 8.501 driver is the 8.6 release. The 8.49.3 driver was the 8.5 release, go figure..

Anyway, I just checked and the installation instructions at:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

have been updated for the 8.6 driver.

the biggest change is in changing the numbers to 8.6 from 8.5 and from 8.49.3 to 8.501. Also, make sure you name the debs correctly when you install them.

one of the is named ....fglrx-dev_x86......not ..fglrx_x86...

If you followed the instructions on that page yesterday and did not notice this then you have a broken install that will leave you without desktop effects, dri etc. Just reinstall the debs with the correct naming and all will be fixed.

---

### Post by morgengenuss on 2008-06-20
i tried 8.6 driver today and have to say: nay. unfortunately the xvideo-extension is broken since 8.5 while in 8.4 it's still working. fortunately ati didn't introduce too many vital features in 8.5 and 8.6 so i can safely skip this month's release...


anyone else experience xvideo trouble with an x1400?

---

### Post by morgengenuss on 2008-06-20
okay. i gotta correct myself on that one. the xvideo-extension is not generally broken, but if i use compiz-fusion with 8.6 i have the flickering video trouble. at least when not in fullscreen playback (e.g. with vlc).

it's really been a while since i was into all of this, but was there a workaround for that one or not?
(when using xfwm4 instead of compiz fusion xvideo works without flickering even when not in fullscreen.)

---

### Post by MadeR on 2008-06-20
> **markbuntu said:**
> The 8.501 driver is the 8.6 release. The 8.49.3 driver was the 8.5 release, go figure..

Anyway, I just checked and the installation instructions at:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

have been updated for the 8.6 driver.

the biggest change is in changing the numbers to 8.6 from 8.5 and from 8.49.3 to 8.501. Also, make sure you name the debs correctly when you install them.

one of the is named ....fglrx-dev_x86......not ..fglrx_x86...

If you followed the instructions on that page yesterday and did not notice this then you have a broken install that will leave you without desktop effects, dri etc. Just reinstall the debs with the correct naming and all will be fixed.

I installed them with the right name but following the instructions.
The result was that the background of each window was missing...

---

### Post by markbuntu on 2008-06-20
> **morgengenuss said:**
> okay. i gotta correct myself on that one. the xvideo-extension is not generally broken, but if i use compiz-fusion with 8.6 i have the flickering video trouble. at least when not in fullscreen playback (e.g. with vlc).

it's really been a while since i was into all of this, but was there a workaround for that one or not?
(when using xfwm4 instead of compiz fusion xvideo works without flickering even when not in fullscreen.)

You can try changing TexturedVideo to "off". It worked for me and my HD3650 and AMD64 3800+ cpu for everything but some widescreen dvd playback in full screen. If you have a faster or multicore cpu it may work for you even with that. All you can do is give it a try.

---

### Post by f1r31c3r on 2009-05-11
well ati-8.600 and 8.601 needs more work as it hangs my x windows with horrible strange artefacts on the screen.

Also if i downgrade to any version lower than 8.6x it don't support xorg 7.4/xserver1.6xxx so i am pretty screwed until this gets fixed.

Also with the latest in ati drivers they do not provide a pre-compiled version of the driver any-more as they have stoped support for cards pre-dated R500.

the new drivers all seem be a different version numbers but 8.601 is released as beta for xserver 1.6xxx so with luck they should iron out its faults soon.:(:guitar::popcorn::KS

---

