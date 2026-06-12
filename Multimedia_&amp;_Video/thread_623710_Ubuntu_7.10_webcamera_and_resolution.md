---
title: "Ubuntu 7.10 webcamera and resolution"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by Blindet on 2007-11-26
Im building a webcam based monitoring system that takes a picture once in a minute, then uploads it to FTP server.
First i used zoneminder, but it was too complicated for a simple task, so i turned up using motion, i got i configured,, but it uses default 352x288 resolution, and always 50% of the image is good, then it has strange red lines, and in the end its totally black.
here's a print screen
[http://aycu37.webshots.com/image/36236/2005042832193130504_fs.jpg](http://aycu37.webshots.com/image/36236/2005042832193130504_fs.jpg)

When i tested it with camorama, it works nice, but only on 176x144 resolution, higher res and it will crash

I tried to set the resolution to higher (640x480), but then it motion didnt start
I setted the resolution to 176x144, and the picture looked good, but it was way too small.

My webcam is logitech quickcam express, and it works out of the box.

what is wrong

---

### Post by avdongen on 2007-12-05
Hi,

Well Blindet i had the same problem as you but i managed to fix it yesterday. It is most definitely a resolution problem.

I looked up my camera under working devices on the motion site and found the my logitech webcam (doesn't seem be a big difference in the logitech quickcame web, chat, express, etc) :

[http://www.lavrsen.dk/twiki/bin/view/Motion/WorkingDevices](http://www.lavrsen.dk/twiki/bin/view/Motion/WorkingDevices)

Apparently the best resolution it works on is 320x240. I have tested this and now it works fine :) 

Hope this helps!

Regards,

Adrian.

PS don't mind my bad English but its really early for me and the coffee has yet to set in ;-)

---

