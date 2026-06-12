---
title: "Version 10.10 and S-Video Issues"
date: 2010-11-12
forum: Mythbuntu
---

### Post by prof3205 on 2010-11-12
Good Evening All,

Here's a problem that's been plaguing me for the better part of the last month ...

I've been able to run version 9.10 using an nVidia 6800 card connected to a TV using S-Video with no problems.  But, when I tried to install v10.10 (or even 10.04 for that matter) the installation goes just fine, but after rebooting, the screen goes blank and I see just a flashing underscore cursor.  I've tried it with an ATI video card with the same result.  I've installed it with both the Open Source and proprietary drivers.  I've even tried using the VGA connection on the card connected to an LCD monitor ... same result.  And I have disabled the onboard video in the BIOS prior to installation.

Now, and this might have give a clue or two, when I install using the onboard VGA connected to an LCD monitor, everything works just fine.  The only problem is that the TV I'm using is an older "CRT" type and only has S-Video, not a VGA.

I could stay with 9.10, but I'd like to move up to 10.10 to take advantage of some of the new features in MythTV 0.24.

Any help would be GREATLY appreciated!
Thanks in advance

---

### Post by nickrout on 2010-11-14
can you get into the machine at all? try:

1. ssh in?

2. hit escape at the flashing cursor

3. hit ctrl-alt-f1 to get to a console

Then start looking at /var/log/Xorg.0.log

Also when starting the install from the cd, try starting the cd with some of the debugging options like noapci etc etc.

---

