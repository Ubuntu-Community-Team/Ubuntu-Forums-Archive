---
title: "Help:mplayer error"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by melodyzm on 2007-12-14
Hi,everybody,i use ubuntu linux just for a few days,i came across a weird problem with the mplayer.
i just updated the system,and the system informed me,there was a updated version would replace the old one,so i clicked "yes"
after the the replacement,i use double-clicked on the video file(avi),it just told me that"failed to open file[....]".instead,i If I open a file through mplayer's internal browser it will open up fine.
i googled the problem,i found someone have the same problem,but with that solution(following) i couldn't fix it.
------------
Pretty tired right now but I will throw something out for the time being.

Make a file called opensesame.sh
Code:

touch opensesame.sh

Now we're going to open it up...
Code:

cat > opensesame.sh



Copy and paste the below, and then hit control+c
MAKE SURE YOU HAVE /usr/bin/gmplayer
Code:

#!/bin/bash
MPLAYER_BIN=/usr/bin/gmplayer
exec $MPLAYER_BIN "$*"


Make it executable
Code:

chmod +x ./opensesame.sh

--------------------------------------------

Have anyone know why this happened?I know i would solve the problem if i uninstall and reinstall mplayer,i just want to know why this happen and how to fix it.
my ubuntu linux is updated,7.10.updated just now
i hope someone could help me.
Thanks

---

### Post by shirilover on 2007-12-14
Or, you could edit /usr/share/applications/mplayer.desktop and change the follwing line from
Exec=gmplayer %U
to
Exec=gmplayer %F

---

### Post by melodyzm on 2007-12-15
i have tried, but i can't just find the mplayer application in the folder:(:(
did i misunderstand what you said?

---

