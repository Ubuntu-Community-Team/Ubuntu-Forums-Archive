---
title: "Does this webcam work with Ubuntu?"
date: 2008-08-23
forum: Multimedia Software
---

### Post by Irihapeti on 2008-08-23
I'm inquiring on behalf of some friends. They have a webcam (still in its original packaging) with the following specs:

Sensor: OV9655 SXGA
ASIC: Sonix 202

1.3 MP, USB 1.1 and 2.0 compatible

The actual model name/number is DSE XH5222

Has anyone had any experience with a webcam of these specifications and can tell me if it will work with Ubuntu?

Thanks
Irihapeti

---

### Post by Crafty Kisses on 2008-08-25
This link may help you > [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by Irihapeti on 2008-08-25
Thanks for the link. Unfortunately, the webcam isn't on any of the lists.

It's a "house brand" webcam, packaged for DSE in New Zealand (and presumably Australia), meaning that it could be anything. It looks like the only way of finding out if it will work is to actually try it, which would mean opening the packaging. I may possibly recommend that my friends exchange it (unopened) for a Logitech model.

Irihapeti

---

### Post by Crafty Kisses on 2008-08-25
You could always try using Ekiga.

Open Ekiga and see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If none of that works post the results of > lsusb

---

