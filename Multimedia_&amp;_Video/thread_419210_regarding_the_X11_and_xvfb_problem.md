---
title: "regarding the X11 and xvfb problem"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by ahhock on 2007-04-22
hi friend,

i just install apt-get install xvfb

but i fount out this problem appear in my debian and openoffice. That why the openoffice is cannot start to run since it's require x-server to support it
last time i try to solve this problem
i'm just solve 2 font path problem for debian

Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi, removing from list
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi, removing from list
Could not init font path element /usr/X11R6/lib/X11/fonts/cyrillic, removing from list

now i just left 2 thing need to solve: below misc and type1


fax:/usr/lib/asterfax/bin# /usr/X11R6/bin/Xvfb :25 -screen scrn 800x600x16
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!


i try to xhost + localhost:
error message:
xhost: unable to open display ""

/usr/X11R6/bin/Xvfb :1 -screen 0 800x600x16 -fbdir /var/tmp/tempfb
error coming out:
open: No such file or directory
open /var/tmp/tempfb/Xvfb_screen0 failed, errno 29
Fatal server error:
Couldn't add screen 0
unlink: No such file or directory
unlink /var/tmp/tempfb/Xvfb_screen0 failed, errno 2fax:~#


itry to use openoffice command:
/usr/bin/openoffice
error message:
Failed to open display
/usr/lib/openoffice/program/soffice.bin X11 error: Can't open display:
Set DISPLAY environment variable, use -display option
or check permissions of your X-Server
(See "man X" resp. "man xhost" for details

_X11TransSocketINETConnect() can't get address for localhost:6099: Name or service not known
/usr/lib/openoffice/program/soffice.bin X11 error: Can't open display: :99
Set DISPLAY environment variable, use -display option
or check permissions of your X-Server
(See "man X" resp. "man xhost" for details)

---

