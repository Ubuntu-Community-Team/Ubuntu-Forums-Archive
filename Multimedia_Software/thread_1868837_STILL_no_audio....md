---
title: "STILL no audio..."
date: 2011-10-24
forum: Multimedia Software
---

### Post by for_crap's_sake on 2011-10-24
I've followed *easily* over a hundred threads about fixing sound problems and here I am, four days later with no sound.

I'm running 64-bit 11.10 and have installed it fresh six times now with a boat-load of problems and crashes each time.

These are my two recognized audio devices:

00:1b.0 "Audio device" "Intel Corporation" "82801I (ICH9 Family) HD Audio Controller" -r02 "Intel Corporation" "Device 0012"

01:00.1 "Audio device" "nVidia Corporation" "GF108 High Definition Audio Controller" -ra1 "Micro-Star International Co., Ltd." "Device 2304"

The nVidia device is a video card with HDMI, and I can't uninstall or disable it. 

I just want to use my crappy on-board audio.

Volume is always 0%, kMix has nothing on it, and whenever I open Multimedia > Phonon it quickly freezes and crashes shortly after.

This is my last attempt before I put this distro behind me for good.

---

### Post by BicyclerBoy on 2011-10-25
Give up & try 11.04 or an earlier ubuntu..

There is something badly wrong with 11.10 & pulse audio..

You can disable the nVidia HDMI codec but there no point.
It can be done with modprobe options for snd-hda-intel module.

---

### Post by theanswriz42 on 2011-10-25
Yeah, I don't know what's going on with it. I have similar hardware: 


00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

---

### Post by BicyclerBoy on 2011-10-25
As a last gasp (attempt at a) solution:
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

### Post by for_crap's_sake on 2011-10-25
Thanks for the words of encouragement, er -- sympathy.  I'll take a look at that last link.

---

### Post by for_crap's_sake on 2011-10-25
Yeah, so I added that ubuntu-audio-dev repo but I'm not even showing the Alsa package when I search.  I think it may have something to do with the error message I received when reloading the package origins.

 p, li { white-space: pre-wrap; }  Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
 404  Not Found
 
 Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages
 404  Not Found
 
 Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
 404  Not Found

---

### Post by BicyclerBoy on 2011-10-25
Sorry that audio devs ppa does not have packages for 11.10

These have 11.10 builds
alsa:
[https://launchpad.net/~ubuntu-audio-...ive/alsa-daily](https://launchpad.net/~ubuntu-audio-...ive/alsa-daily)
pulse audio:
[https://launchpad.net/~ubuntu-audio-.../pulse-testing](https://launchpad.net/~ubuntu-audio-.../pulse-testing)

Try at your own risk..I have not needed to use..

---

### Post by for_crap's_sake on 2011-10-29
Anyone have any other ideas than the broken links thus far provided?

I've read another ~20 threads about the same exact issue and not a single one has a solution.  

This is ridiculous.

---

### Post by BicyclerBoy on 2011-10-29
poxy forum editor is wrecking the links now ..as well as adding crap & reformatting..must be MS word..

Why couldn't you find it yourslf ?

```

https://launchpad.net/~ubuntu-audio-dev

https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily?field.series_filter=oneiric

```

---

### Post by inobe on 2011-10-29
> **for_crap's_sake said:**
> Anyone have any other ideas than the broken links thus far provided?

I've read another ~20 threads about the same exact issue and not a single one has a solution.  

This is ridiculous.

not really that ridiculous, but i do understand your frustration.

> The nVidia device is a video card with HDMI, and I can't uninstall or disable it.

I just want to use my crappy on-board audio.

have a look here [http://ubuntuforums.org/showpost.php?p=11407142&postcount=2](http://ubuntuforums.org/showpost.php?p=11407142&postcount=2)

make the profile change in system settings> multimedia> on left pane hit phonon> hit audio hardware tab> drop down menu next to profile, select off.

i will keep an eye on this thread incase you have more issues.
:)

---

### Post by elt0r0 on 2012-04-11
Ran into this same issue.  I can turn off the GF108 HD Audio Controller and I can get audio output from the front inputs on my box (HP z400), however, I still don't get any audio out from the rear jacks.  My internal audio, when viewed through sound settings displays "1 Output / 1 Input"..should it include the rear outputs as well?  I would appreciate any thoughts.  Thanks!

---

