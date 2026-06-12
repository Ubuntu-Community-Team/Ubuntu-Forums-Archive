---
title: "webcam woes"
date: 2008-05-13
forum: Multimedia Software
---

### Post by princess laya on 2008-05-13
:confused::confused::confused:i'm a linux noob and i am desperately trying to figure out how to get my Trust WB-3320X webcam to work in Ubuntu 8.04. i know that i need a driver but can't find one on the manufacturer's website. the one who has the force gets to see the princess' first live broadcast ;)  :popcorn:we

---

### Post by linuxwizard on 2008-05-13
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If the webcam does not work post the results of the command > lsusb

---

