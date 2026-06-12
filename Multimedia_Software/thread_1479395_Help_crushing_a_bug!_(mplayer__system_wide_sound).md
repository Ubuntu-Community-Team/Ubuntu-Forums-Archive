---
title: "Help crushing a bug! (mplayer / system wide sound)"
date: 2010-05-10
forum: Multimedia Software
---

### Post by plafuro on 2010-05-10
... or at least what i think is a bug!

Hi everyone...

I just made a fresh install of Lucid, and i noticed that while playing music (with rhythmbox, for instance), if an instance of mplayer is executed (from the command line, even with no parameters or a file to open) sound seems to just stop system wide, until I close all applications that may have been playing any sound.

I would really appreciate if any of you with a standard Lucid 64bit system (just to try to replicate more or less the same environment) took the time to install mplayer and execute it from the command line while playing sound somewhere else. If you can replicate this issue and have a launchpad account, please add a +1 over here [https://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/575368](https://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/575368) , if not I will look down in shame and try to figure out (again) why is this happening in my computer :)

Thank you very much in advance!

P.D.: Just as some background information: i found out about this as my favourite screensaver, [electricsheep]("http://electricsheep.org"), would stop my music from playing every time it activated itself... It runs thanks to mplayer... you definetly have to check it out!

---

### Post by plafuro on 2010-05-14
For anyone having this kind of problem: there is now a new openal library in the lucid-proposed repos (libopenal1 is the name of the package). This package fixes the issues mentioned in my previous post (they were related to the outdated openal library).

See [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)  for documentation how to enable and use -proposed.

Cheers

---

