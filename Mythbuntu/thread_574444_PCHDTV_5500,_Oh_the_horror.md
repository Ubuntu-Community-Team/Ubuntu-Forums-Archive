---
title: "PCHDTV 5500, Oh the horror"
date: 2007-10-12
forum: Mythbuntu
---

### Post by ddover on 2007-10-12
First Off I want to thank everyone who involved with this project. Mythtv and espeicially mythbuntu have come a LONG way.

I had the system up and running about 4 months ago (I was using ubuntu fiesty and mythtv). I optimistically reformatted when linuxmce came out. Unfortuently, my hardware was not compatitble. I have switched to mythubuntu and most things now work...

I have two PCHDTV 5500 tuners running analog. V4L drivers They provide decent picture but terrible sound. It is crackily and speed up. I have tried all the recommendations I could find in this forum as well as (the useless) pchdtv forums.

I am able to play back dvds and movies no problem so i doubt it is the sound or video cards.

Any help would be appreciated.

---

### Post by superm1 on 2007-10-12
Have you tried both tuners to make sure that it's actually occurring on both?  I would almost want to suspect hardware issues, but don't want to jump the gun.

---

### Post by freddyg on 2007-10-13
are you trying to catch broadcast or qam?

---

### Post by ddover on 2007-10-13
> **freddyg said:**
> are you trying to catch broadcast or qam?

broadcast

and Since it worked earlier with mythtv earlier I don't think it hardware problems (HD works great now but my area only supports a few channels.) I suspect it is driver or setting problems. I have looked into both to no avail.

Any advice would be fanatastic (Let me know if you need more info)

Thank You

---

### Post by mhitchens on 2008-01-22
ddover,

I think I know what problem you're having. I ran into this several times when running my pcHDTV 5500 on Debian, on Ubuntu, and most recently, Mythbuntu. The good news is, it's fixed. Here's the deal.

There's code in the v4l-dvb project that has drivers for various different tuners, including the digital and analog components of the pcHDTV Conexant tuner hardware. The issue was patched by an enthusiast (nybbler on the pchdtv.com forums), and then was adapted by a developer into the v4l-dvb tree. Unfortunately, the version of the kernel in Mythbuntu is currently too old to have picked up the fix, so by default, you'll have the faulty code. All you need to do to fix it is to compile the v4l-dvb tree yourself and install it over your current kernel modules. It's easy to do and pretty quick.

1. sudo apt-get install gcc linux-headers-<version>-<kernel type> mercurial
2. hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb). This will create a folder called v4l-dvb in the current directory. I usually do this in a 'build' directory in my home dir.
3. make, then sudo make install
4. sudo reboot

Hopefully that fixes the issue for you. I know it's given me no end of frustration. Be comforted by the fact that, eventually, Mythbuntu and all linux distros will pick it up when it migrates into the kernel proper. Be advised that if Mythbuntu provides a new kernel that still doesn't have the fix, you'll need to repeat the process above as the modules you install manually are tied to the version of the kernel you're running.

Hope that helps!
matt

p.s. - Brand new Mythbuntu user as of this weekend and I'm totally digging it so far. Great job guys! Much cleaner than running my own distro, and I don't lose any of the control.

---

### Post by nedson on 2008-02-13
:Hi...

Just wanted to say thanks for the information.  Unfortunately, there is a lot of information about the pchdtv 5500 scattered about the net and one must put it together to get the card going...

I have two pchdtv 5500 cards and have spent a couple days figuring things out.  My hope is that this will fix some of the audio issues that I've had with analog stations.

Sometimes when flipping between digital and analog I get really lousy audio on the analog side...crackling...stuttering...sped up...I think this is what everyone else is describing...

Nonetheless, when I get things working I'm going to post a howto on how to setup two pchdtv 5500's using mythbuntu.  I think a succint guide on how to setup a couple of these cards one machine would be helpful...perhaps it exists and I just haven't found it :confused:

Anyhow, thank you.

---

### Post by Caps18 on 2008-02-15
I haven't had any problems with my pcHDTV5500 card once I switched one of the video processing drivers.  I can't remember which one right now, but it is the third one in the list of 4.  

I will be buying a second HD-5500 in the next few weeks in order to record two shows when studios try to put them on in the same time slot.  I would like to see your advice written up.

Thanks.

---

