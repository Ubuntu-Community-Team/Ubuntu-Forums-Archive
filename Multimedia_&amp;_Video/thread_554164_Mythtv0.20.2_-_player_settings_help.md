---
title: "Mythtv0.20.2 - player settings help"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by andyklaj on 2007-09-18
hi, ill try to keep this quick.
im kind of a noob so please keep the replies simple if possible

i cant get the videos to play in my mythtv.  after researching it a bit i found that the argument %s (in the player settings window of myth tv) only returns the filname to mythtv and not the path.
so for example the setting
xine %s
will execute
xine filename.mpg
instead of 
xine /home/andy/Desktop/....../filename.mpg
apparantly this is a unique problem to 0.20 : see external player configuration [http://www.mythtv.org/wiki/index.php/MythVideo](http://www.mythtv.org/wiki/index.php/MythVideo)

and this happens for mplayer as well.
I thought this problem could be sovled by the command
find /home/andy/Desktop/video/ -name %s | xine
i thought pipeing the information to xine would work (but it didnt)

help would be grateful, thanks

---

### Post by andyklaj on 2007-09-18
hey got it working - sorry about this

---

