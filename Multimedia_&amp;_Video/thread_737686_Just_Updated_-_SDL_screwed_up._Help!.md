---
title: "Just Updated - SDL screwed up. Help!"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by migszo on 2008-03-27
Hello,
I just updated through the update manager today, and that's when things went haywire.
Right off the bat my nvidia drivers were disabled, and my 4 workspace environments were gone and cut down to 2.  Desktop effects were not working either.  Got the nvidia driver reinstalled and solved all of those problems but now when I go to load apps like ScummVM or Wesnoth, I get these error messeges:

From ScummVM:
Could not initialize SDL: No available video device!

Wesnoth:
20080327 20:56:29 error display: Could not initialize SDL: No available video device
Could not initialize video. Exiting.

I tried reinstalling SDL but now when I do a make command I get this:

/bin/bash ./libtool --mode=compile gcc -g -O2  -I./include -D_GNU_SOURCE=1 -fvisibility=hidden  -DXTHREADS -D_REENTRANT -DHAVE_LINUX_VERSION_H -c ./src/video/x11/SDL_x11dga.c  -o build/SDL_x11dga.lo
 gcc -g -O2 -I./include -D_GNU_SOURCE=1 -fvisibility=hidden -DXTHREADS -D_REENTRANT -DHAVE_LINUX_VERSION_H -c ./src/video/x11/SDL_x11dga.c  -fPIC -DPIC -o build/.libs/SDL_x11dga.o
In file included from ./src/video/x11/SDL_x11video.h:53,
                 from ./src/video/x11/SDL_x11dga_c.h:24,
                 from ./src/video/x11/SDL_x11dga.c:30:
./src/video/x11/SDL_x11dyn.h:39:33: error: X11/extensions/XShm.h: No such file or directory
In file included from ./src/video/x11/SDL_x11dga_c.h:24,
                 from ./src/video/x11/SDL_x11dga.c:30:
./src/video/x11/SDL_x11video.h:80: error: expected specifier-qualifier-list before 'XShmSegmentInfo'
make: *** [build/SDL_x11dga.lo] Error 1

I'm a bit confused on what has happened here.  Any suggestions?

Thanks,
-Mike

---

