---
title: "projectM install from source"
date: 2008-12-03
forum: Multimedia Software
---

### Post by hansoffate on 2008-12-03
I tried installing projectM from the repo but it is only integrated in Amarok.  I want to install the pulseaudio version of projectM 1.2.0, so that any audio that is playing through my computer, I can display projectM.  The main reason for me doing this is because it would be awesome if I could have projectM as my visualizer when using Songbird 1.0.

Link to package
[http://sourceforge.net/project/showfiles.php?group_id=104201&package_id=269729](http://sourceforge.net/project/showfiles.php?group_id=104201&package_id=269729)

Link to a howto
[http://linuxmint.com/wiki/index.php/Install_ProjectM](http://linuxmint.com/wiki/index.php/Install_ProjectM)

I installed the dependencies listed.  When I extract the package and try to ./configure, I get "No such file or directory."  I tried looking for the config script but I couldn't find it.  

Can someone check out the package and see if they can make it?  If you can, can you help me make this?

Thanks,
Hans

---

### Post by kostkon on 2008-12-03
> **hansoffate said:**
> I tried installing projectM from the repo but it is only integrated in Amarok.  I want to install the pulseaudio version of projectM 1.2.0, so that any audio that is playing through my computer, I can display projectM.  The main reason for me doing this is because it would be awesome if I could have projectM as my visualizer when using Songbird 1.0.

Link to package
[http://sourceforge.net/project/showfiles.php?group_id=104201&package_id=269729](http://sourceforge.net/project/showfiles.php?group_id=104201&package_id=269729)

Link to a howto
[http://linuxmint.com/wiki/index.php/Install_ProjectM](http://linuxmint.com/wiki/index.php/Install_ProjectM)

I installed the dependencies listed.  When I extract the package and try to ./configure, I get "No such file or directory."  I tried looking for the config script but I couldn't find it.  

Can someone check out the package and see if they can make it?  If you can, can you help me make this?

Thanks,
Hans
Try to follow [this how-to here]("http://ubuntuforums.org/showthread.php?t=749793"). It may work better for you.

---

### Post by hansoffate on 2008-12-03
> **kostkon said:**
> Try to follow [this how-to here]("http://ubuntuforums.org/showthread.php?t=749793"). It may work better for you.

Thanks for the link.  I just got it installed again after not using it for awhile.  They fixed the disappearing mouse bug too!  Now to enjoy some visualizations from Songbird via projectm-pulseaudio.

If anyone wants to get the current SVN 1199 with Interpid Ibex working, the steps are listed on page 19 of the thread.

[http://ubuntuforums.org/showthread.php?t=749793&page=19](http://ubuntuforums.org/showthread.php?t=749793&page=19)

> **Zularan said:**
> Just confirming this works fine for Intrepid.

Steps I used were:

```
sudo aptitude install libglew1.5 libglew1.5-dev ftgl-dev libpulse-dev subversion cmake libvisual-0.4-dev libsdl-dev libqt4-dev build-essential
```

```
cd ~
mkdir projectm
cd projectm
svn co https://projectm.svn.sf.net/svnroot/projectm/trunk projectM-Trunk
```

```
cd projectM-Trunk/src
```

```
ccmake .
```

> Now cmake will load. Press "c" to configure projectM. Highlight the CMAKE_BUILD_TYPE field, press enter and type "Release" there. Press enter again. Then highlight the CMAKE_INSTALL_PREFIX field and change /usr/local to /usr/. Then press "c" again to configure it with those parameters.

Had some warnings that looked like 


I went on anyway.

First make failed but lamelos' fix worked fine.

> **lamelos said:**
> I had the same problem, but seem to have 'fixed' it now.
The problem seems to be that FTGL.h is in lowercase (on my pc it was anyway - Intrepid 8.10) and thus it can't be found by the 'make'-command.

This is how i fixed it:

Before you do 'make'
```
cd libprojectM
gedit Renderer.hpp

```

then edit lines 28-30 from
this:
```
#include <FTGL/FTGL.h>
#include <FTGL/FTGLPixmapFont.h>
#include <FTGL/FTGLExtrdFont.h>
```
to this:
```
#include <FTGL/ftgl.h>
/**#include <FTGL/FTGLPixmapFont.h> */
/**#include <FTGL/FTGLExtrdFont.h> */
```

after this, exit gedit
and
```

cd ..
make

```

now the make succeeds, and you can proceed with 
```

sudo make install

```

Hope it works for you as well.



projectM-pulseaudio should be in Menu -> Sound and Video 
or cli ```
projectM-pulseaudio
```

---

