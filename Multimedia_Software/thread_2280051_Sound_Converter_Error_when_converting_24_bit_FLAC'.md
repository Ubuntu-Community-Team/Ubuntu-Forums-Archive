---
title: "Sound Converter: Error when converting 24 bit FLAC's."
date: 2015-05-27
forum: Multimedia Software
---

### Post by warren3 on 2015-05-27
Hi.

I am using Sound Converter 2.0.4. and Ubuntu 14.04.

Now when I try to convert 24 bit FLAC's to m4a I get a Gstreamer error.  The funny thing is I converted the same files using another install of Ubuntu 6 months ago and they converted fine.  Now maybe I installed something different back then I do not know.  

Is there any way this can be fixed?

Also, how can I upgrade to the latest Sound Converter (maybe this could help?).

Thanks.

---

### Post by ajgreeny on 2015-05-27
You could try using **avconv** in the command line, or if you want a GUI application try **winff** which uses avconv (or ffmpeg if you really want it to).

---

### Post by Rob Sayer on 2015-05-29
I use audacity for 24 bit to redbook conversion.  Great program.  As good as winff is bad, frankly ...

If you want to convert a whole CD in a folder with individual tracks you can do batch processing with the audacity chains function.

---

### Post by Yellow Pasque on 2015-05-31
You could try 2.1.4 from here:
[https://launchpad.net/~tsvetko.tsvetkov/+archive/ubuntu/trusty-backports](https://launchpad.net/~tsvetko.tsvetkov/+archive/ubuntu/trusty-backports)

If that does not help, please give the specific gstreamer error. Run from the terminal if you have to.

---

