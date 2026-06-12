---
title: "Nouveau 3D?"
date: 2010-07-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-07-15
How do I actually get this experimental basic 3D support? Are there any PPAs available or do I need to compile it myself?

---

### Post by gnomeuser on 2010-07-15
thou shallth enable xorg-edgers and install the nouveau-firmware package. Then wisdom can be found by installing the gallium package (seek and thee shall find.. I'm to lazy to recall the precise package name as I am on the bus).

reboot and hope nothing blows up

---

### Post by MacUntu on 2010-07-15
> **gnomeuser said:**
> Then wisdom can be found by installing the gallium package
](*,)#-o:-\"

Thanks! ;)

--- EDIT ---

Had to purge nvidia-current, because X still loaded the Nvidia glx module. Now it works (as expected not as fast as I'd like, but it works). :)

---

### Post by gnomeuser on 2010-07-15
> **MacUntu said:**
> ](*,)#-o:-\"
Had to purge nvidia-current, because X still loaded the Nvidia glx module. Now it works (as expected not as fast as I'd like, but it works). :)

It's enough to use jockey (the hardware driver thingy) to uninstall the proprietary driver.

---

### Post by vkontakte on 2010-07-15
> It's enough to use jockey (the hardware driver thingy) to uninstall the proprietary driver.
Lol. Change stable and high-performance driver to buggy and slow one )))

---

### Post by RAOF on 2010-07-15
You can get the nouveau 3D support (for nv3x+ cards or above - that's GeForce FX or newer) from the regular archive packages, too - the libgl1-mesa-dri-experimental contains these.

---

### Post by MacUntu on 2010-07-16
Thanks for the hint! :)

---

### Post by davidwillis on 2010-07-18
> **RAOF said:**
> You can get the nouveau 3D support (for nv3x+ cards or above - that's GeForce FX or newer) from the regular archive packages, too - the libgl1-mesa-dri-experimental contains these.

I can't see that package when I search in synaptic.  How do I get it?

---

### Post by ranch hand on 2010-07-18
> **davidwillis said:**
> I can't see that package when I search in synaptic.  How do I get it?
System>Aministration>Software Sources go to "Updates" tab.  Enable "Pre-release updates (maverick proposed)".

Or in Synaptic, Settings>Repositories then the same directions as above.

Will update when you close the box.  Should do it.

---

### Post by mc4man on 2010-07-18
> I can't see that package when I search in synaptic. How do I get it?

Either you haven't updated in a bit or you're hand typing the search name incorrectly - it's sitting right there. (better to search less specific in synaptic

> doug@doug-desktop1:~$ apt-cache search libgl1-mesa-dri
libgl1-mesa-dev - A free implementation of the OpenGL API -- GLX development files
libgl1-mesa-dri - A free implementation of the OpenGL API -- DRI modules
libgl1-mesa-dri-dbg - Debugging symbols for the Mesa DRI modules
libgl1-mesa-dri-experimental - A free implementation of the OpenGL API -- Extra DRI modules
libgl1-mesa-dri-experimental-dbg - Debugging symbols for the experimental Mesa DRI modules
libgl1-mesa-glx - A free implementation of the OpenGL API -- GLX runtime
libgl1-mesa-glx-dbg - Debugging symbols for the Mesa GLX runtime

> 
...(maverick proposed
what's that.

---

### Post by Starks on 2010-07-18
maverick-proposed is a staging repo. You enable it in the update tab of Software Sources.

However, you don't need to enable it for the experimental drivers. Last I checked, libgl1-mesa-dri-experimental was a main archive package, not a maverick-proposed package.

You'll need to run synaptic and reload to see it listed.

---

### Post by davidwillis on 2010-07-18
strange, mine does not have it> david@david-desktop:~$ apt-cache search libgl1-mesa-dri
libgl1-mesa-dev - A free implementation of the OpenGL API -- GLX development files
libgl1-mesa-dri - A free implementation of the OpenGL API -- DRI modules
libgl1-mesa-dri-dbg - Debugging symbols for the Mesa DRI modules
libgl1-mesa-glx - A free implementation of the OpenGL API -- GLX runtime
libgl1-mesa-glx-dbg - Debugging symbols for the Mesa GLX runtime


also in the software sources it has lucid proposed, not maverick proposed....

I wonder if something got messed up when I upgreded to lucid?

---

### Post by MacUntu on 2010-07-18
You do know this is the "Maverick Meerkat Testing and Discussion" forum, don't you? :P

---

### Post by davidwillis on 2010-07-18
> **MacUntu said:**
> You do know this is the "Maverick Meerkat Testing and Discussion" forum, don't you? :P

I feel dumb... I just did a google search and found this, and didn't even see that it was in the maverick meerkat testing...

Sorry...

---

### Post by roberto.tomas on 2010-09-26
> **gnomeuser said:**
> thou shallth enable xorg-edgers and install the nouveau-firmware package. Then wisdom can be found by installing the gallium package (seek and thee shall find.. I'm to lazy to recall the precise package name as I am on the bus).

reboot and hope nothing blows up

can you (or anyone else here) provide a more thorough write up of what is required?

I have a weird situation in that, after upgrading form 10.04 x wouldnt start. I removed xorg.conf and voila, x runs just fine. Ive installed the firmware, and also tried the lib-mesa-dri-experimental .. neither of them seems to work according to glxinfo.

looking into it a bit more, I discovered I could wholely uninstall xserver-xorg-video-nouveau and xserv...-nv and still get X, but if I remove xserv...-fbdev it goes away. Yet lsmod|grep nouveau sows it there.Im not sure my system is even in a consistent state anymore and .. ideally I could repair it to have 3d :) but Id need to see more complete instructions than appear to be available online at this time.

---

