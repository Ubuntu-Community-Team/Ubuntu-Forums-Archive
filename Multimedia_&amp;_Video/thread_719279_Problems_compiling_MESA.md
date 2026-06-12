---
title: "Problems compiling MESA"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by Vaftrudner on 2008-03-09
Hello people!

I'm using Ubuntu Gutsy, and everything works for me except for some games with wine, probably due to my Intel ICH8 chipset. I posted the bug on wine's bugzilla, it turned out to be known ([here](http://bugs.winehq.org/show_bug.cgi?id=10674)), and fixed upstream in mesa. I am a bit new to Linux in general, but attempted to get the latest mesa via git and compile it following [these instructions](http://dri.freedesktop.org/wiki/Building). However, when I get to actually making the files, with the "make linux-dri-x86" command, I get the following errors:

> **"console"]makedepend: warning:  indirect_vertex_array.c, line 32: cannot find include file "GL/glxproto.h"
        not in ./GL/glxproto.h
        not in ../../../include/GL/glxproto.h
        not in ../../../include/GL/internal/GL/glxproto.h
        not in ../../../src/mesa/main/GL/glxproto.h
        not in ../../../src/mesa/glapi/GL/glxproto.h
        not in /usr/local/include/GL/glxproto.h
        not in /usr/local/include/drm/GL/glxproto.h
        not in /usr/X11R6/include/GL/glxproto.h
        not in /usr/include/GL/glxproto.h
makedepend: warning:  indirect_vertex_array.c (reading indirect_va_private.h, line 39): cannot find include file "GL/glxproto.h"
        not in ./GL/glxproto.h
        not in ../../../include/GL/glxproto.h
        not in ../../../include/GL/internal/GL/glxproto.h
        not in ../../../src/mesa/main/GL/glxproto.h
        not in ../../../src/mesa/glapi/GL/glxproto.h
        not in /usr/local/include/GL/glxproto.h
        not in /usr/local/include/drm/GL/glxproto.h
        not in /usr/X11R6/include/GL/glxproto.h
        not in /usr/include/GL/glxproto.h
makedepend: warning:  indirect_vertex_program.c, line 31: cannot find include file "GL/glxproto.h"
        not in ./GL/glxproto.h
        not in ../../../include/GL/glxproto.h
        not in ../../../include/GL/internal/GL/glxproto.h
        not in ../../../src/mesa/main/GL/glxproto.h
        not in ../../../src/mesa/glapi/GL/glxproto.h
        not in /usr/local/include/GL/glxproto.h
        not in /usr/local/include/drm/GL/glxproto.h
        not in /usr/X11R6/include/GL/glxproto.h
        not in /usr/include/GL/glxproto.h
makedepend: warning:  singlepix.c, line 43: cannot find include file "GL/glxproto.h"
        not in ./GL/glxproto.h
        not in ../../../include/GL/glxproto.h
        not in ../../../include/GL/internal/GL/glxproto.h
        not in ../../../src/mesa/main/GL/glxproto.h
        not in ../../../src/mesa/glapi/GL/glxproto.h
        not in /usr/local/include/GL/glxproto.h
        not in /usr/local/include/drm/GL/glxproto.h
        not in /usr/X11R6/include/GL/glxproto.h
        not in /usr/include/GL/glxproto.h
glcontextmodes.c:42:23: error: GL/glxint.h: No such file or directory
In file included from glcontextmodes.c:67:
glcontextmodes.h:39: warning: type defaults to &#8216 said:**
> : *** [glcontextmodes.o] Error 1
make[2]: *** [subdirs] Error 1
make[1]: *** [default] Error 1
make: *** [linux-dri-x86] Error 2

"pkg-config --modversion libdrm" gives 2.3.1.

Could anyone tell me what seems to be wrong? Thanks in advance!

---

### Post by mc4man on 2008-03-09
maybe try installing  xl11proto-gl-dev  and related -devs

---

### Post by Vaftrudner on 2008-03-09
> **mc4man said:**
> maybe try installing  xl11proto-gl-dev  and related -devs
Yeah, that's right, I almost forgot about it. When i do "sudo apt-get build-dep libdrm mesa" I get the following: "E: You must put some 'source' URIs in your sources.list". Am I missing some source for dependencies?

---

### Post by mc4man on 2008-03-09
i don't have any 'unusual sources' enabled - in software sources  all 5 under ubuntu and in updates all 4 - running that shows 
 ```
sudo apt-get build-dep mesa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libdrm-dev
0 upgraded, 1 newly installed, 0 to remove and 138 not upgraded.
Need to get 89.8kB of archives.

```
I'm sure you'll see more - I have alot of build-deps already installed
for example  the package I mentioned before has glxproto.h in it

edit; never hurts to have -devs installed
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libdrm-dev 2.3.0-4ubuntu1 [89.8kB -  comes from gutsy/main

---

### Post by Yellow Pasque on 2008-03-09
To clarify what he said, go to System -> Administration -> Software Sources, and make sure all the options on the first tab are checked (specifically, your mesa build is complaining about the 'Source' repo not being enabled.

---

### Post by norsk on 2008-03-09
Aha thank you for the clarification, I was able to run apt-get build-dep libdrm mesa command

---

### Post by Vaftrudner on 2008-03-09
Yes, changing those sources and running apt-get again did it. I don't know what I was thinking when I skipped that step.. Well, we're all beginners at some point :) Thanks for the help!

---

### Post by Yellow Pasque on 2008-03-09
> Thanks for the help!
Aye. Enjoy. (You should also mark the thread as [SOLVED] with the option under the Thread Tools menu)

---

