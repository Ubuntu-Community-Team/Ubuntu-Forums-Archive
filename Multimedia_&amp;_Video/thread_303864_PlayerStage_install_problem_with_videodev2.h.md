---
title: "Player/Stage install problem with videodev2.h"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by akhtet on 2006-11-20
I hope this is the right place to ask this.
When I tried install Player by .configure/make/make install
it cannot compile videodev2.h
This didn't happen in 6.06 ...
Now it's giving problem in 6.10.

The message is as follows. I hope C++ and linux experts can figure it out. Please give me suggestions.


Making all in uvc
make[5]: Entering directory `/home/akhtet/player-2.0.3/server/drivers/camera/uvc'
if /bin/bash ../../../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../libplayercore -I../../../../client_libs/libplayerc++  -Wall -I../../../..    -MT cameraUVC.lo -MD -MP -MF ".deps/cameraUVC.Tpo" -c -o cameraUVC.lo cameraUVC.cc; \
        then mv -f ".deps/cameraUVC.Tpo" ".deps/cameraUVC.Plo"; else rm -f ".deps/cameraUVC.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../libplayercore -I../../../../client_libs/libplayerc++ -Wall -I../../../.. -MT cameraUVC.lo -MD -MP -MF .deps/cameraUVC.Tpo -c cameraUVC.cc  -fPIC -DPIC -o .libs/cameraUVC.o
/usr/include/linux/videodev2.h:155: error: '__s32' does not name a type
/usr/include/linux/videodev2.h:156: error: '__s32' does not name a type
/usr/include/linux/videodev2.h:157: error: '__s32' does not name a type
/usr/include/linux/videodev2.h:158: error: '__s32' does not name a type
/usr/include/linux/videodev2.h:162: error: '__u32' does not name a type
/usr/include/linux/videodev2.h:163: error: '__u32' does not name a type

---

### Post by RFScheer on 2006-11-25
I'm at the same point with the same error.  Working on it!  Let me know if you solved this please.

---

### Post by RFScheer on 2006-11-25
After running make-clean in the player/stage install directory, I grabbed the latest from the sourceforge cvs repository for player/stage using:

```
cvs -z3 -d:pserver:anonymous@playerstage.cvs.sourceforge.net:/cvsroot/playerstage co -P /code/player
```

I didn't want to debug all the new modules so I just took the new uvc code from the new directory at 

.../code/player/server/drivers/camera/uvc

and swapped it for the old one in:

..../player-2.0.3/server/drivers/camera/uvc

then did:

```
aclocal
autoconf
automake
./configure --prefix=/my/install/dir
make
sudo make install
```

---

### Post by bnl on 2007-03-17
I could not get it to work.  I got the following error message after running aclocal, autoconf, and automake and then configure:

./configure: line 21506: syntax error near unexpected token `,'
./configure: line 21506: `    PKG_CHECK_MODULES(, ,'

Any thoughts?

(I'm using Xubuntu)

---

### Post by bnl on 2007-03-18
from [http://www.cs.gmu.edu/~sean/cs499/pmwiki.php/Forum/Solved](http://www.cs.gmu.edu/~sean/cs499/pmwiki.php/Forum/Solved)

"- open player-2.0.3/server/drivers/camera/uvc/v4l2uvc.h - find #include <linux/videodev2.h> and add #include <linux/types.h> directly above it. 

from http://sourceforge.net/mailarchive/message.php?msg_id=36997794"

---

### Post by Princegiri on 2007-12-04
[http://ubuntuforums.org/showthread.php?p=3889012#post3889012](http://ubuntuforums.org/showthread.php?p=3889012#post3889012)
this is a thread to a problem i have with player stage..... its tough to find player stage users in ubuntu forums.... so i pasted this here..... pls help me out. thanks

---

