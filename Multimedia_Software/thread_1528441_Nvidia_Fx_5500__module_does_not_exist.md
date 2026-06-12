---
title: "Nvidia Fx 5500  module does not exist"
date: 2010-07-10
forum: Multimedia Software
---

### Post by jdougmoore on 2010-07-10
I have tried just about everything, except for the right thing. 

Tried:
nvidia-xconfig
Booting with no xserver, running the Nvidia shell script package to install 173.14.25 pkg, nothing
And about 48 other things

I can't get my Gforce Fx 5500 to run in 1920x1024 mode.  Have googled  and edit xconfig.conf about 50 times, with zero results my log files gives me:

II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.
Fatal server error:
no screens found

UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

WTH? I can see using the "hardware" module that 173 is being used and active.

What am I missing here

---

### Post by jdougmoore on 2010-07-12
> **jdougmoore said:**
> I have tried just about everything, except for the right thing. 

Tried:
nvidia-xconfig
Booting with no xserver, running the Nvidia shell script package to install 173.14.25 pkg, nothing
And about 48 other things

I can't get my Gforce Fx 5500 to run in 1920x1024 mode.  Have googled  and edit xconfig.conf about 50 times, with zero results my log files gives me:

II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.
Fatal server error:
no screens found

UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

WTH? I can see using the "hardware" module that 173 is being used and active.

What am I missing here

Bump..

---

