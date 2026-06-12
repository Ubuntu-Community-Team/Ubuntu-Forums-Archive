---
title: "Blender wants to update every time"
date: 2011-07-27
forum: Multimedia Software
---

### Post by SoFl W on 2011-07-27
I recently installed OpenShot video editor.  I wanted to try out one of the animated titles and it told me my Blender version is too old.  I searched around and found this thread
[http://ubuntuforums.org/showthread.php?t=1184942](http://ubuntuforums.org/showthread.php?t=1184942)
and added the PPA
ppa:cheleb/blender-svnHowever everytime I do an update it tells me there is a update for Blender.  The version number is the same as the one installed.  (2.58)

I am using 10.4.3 64 bit.

Any ideas why it is asking me to constantly upgrade?

Just for fun I typed "blender -v" at the command line
```
 blender -v
Blender 2.58 (sub 1)
    build date: 20:12:42
    build time: BUILD_TIME
    build revision: 38739
    build platform: Linux
    build type: RelWithDebInfo
    build c flags: -g -O2  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -fopenmp  -msse2  -msse -pipe -fPIC -funsigned-char -fno-strict-aliasing  -Wall -Wcast-align -Werror=declaration-after-statement -Werror=implicit-function-declaration -Werror=return-type -Wstrict-prototypes -Wno-char-subscripts -Wno-unknown-pragmas -Wpointer-arith -Wunused-parameter -Wwrite-strings
    build c++ flags: -g -O2  -D__STDC_CONSTANT_MACROS -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -fopenmp  -msse2  -msse -pipe -fPIC -funsigned-char -fno-strict-aliasing  -Wall -Wno-invalid-offsetof -Wno-sign-compare
    build link flags: -pthread
    build system: CMake
```

---

### Post by SoFl W on 2011-07-28
I un-installed  Blender and used a tried the PPA information from [OMGUbuntu]("http://www.omgubuntu.co.uk/2011/04/blender-stable-released/").

It will not tell me it needs to be upgraded if I do the upgrade, exit and recheck the upgrades.  It seems to only tell me to upgrade when there is something else that needs to be upgraded.

---

### Post by jerrrys on 2011-07-29
being a PPA, i would think its a work in progress and subject to constant upgrades.  you could try locking the version in synaptic package manager and see if that will stop upgrades.

---

### Post by mcduck on 2011-07-29
That repository automatically compiles the development builds from SVN, and does it quite often. So yes, it's normal that you'd get a lot of Blender updates if you use a Blender repository that's constantly updating. ;)

You could either disable the repository and only enable it when you wish to update blender, or just download the Blender package from Blender's web site (it's pre-compiled, all you need to do is extract it somewhere and run from there).

---

### Post by SoFl W on 2011-07-29
Thank you both for your help.

> **jerrrys said:**
> being a PPA, i would think its a work in progress and subject to constant upgrades.  you could try locking the version in synaptic package manager and see if that will stop upgrades.
That could be what it is, I have other PPAs but those don't seem to have frequent upgrade notices.


> **mcduck said:**
> That repository automatically compiles the development builds from SVN, and does it quite often. So yes, it's normal that you'd get a lot of Blender updates if you use a Blender repository that's constantly updating. 
Sounds good I thought it was just a current stable release PPA, not a development release.

> **mcduck said:**
>  You could either disable the repository and only enable it when you wish to update blender, or just download the Blender package from Blender's web site (it's pre-compiled, all you need to do is extract it somewhere and run from there).
I tried the Blender site but I could only find the .tar.bz2 files and assumed I would have to compile myself.  I did not see any .deb files.


I wish I had more time to spend with Blender and video editing, I used to edit video professionally and enjoy it as a hobby, I just don't have the time.  I wanted to make a quick video for the family and then started to get these "problems."

Thank you again for your help.

---

