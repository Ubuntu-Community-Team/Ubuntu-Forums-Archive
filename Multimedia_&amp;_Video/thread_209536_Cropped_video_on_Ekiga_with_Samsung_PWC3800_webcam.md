---
title: "Cropped video on Ekiga with Samsung PWC3800 webcam"
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by Pulka on 2006-07-05
Hi,

I recently bought a Samsung Pleomax PWC3800 webcam which uses the spca5xx driver provided by the kernel (2.6.15-25). I bought it because it was highly recommended by the driver developer(?) in [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html), six out of five stars. The webcam works out of the box, video and microphone, without any tweaking. My only complaint is Ekiga cropping the video so much, people can only see half of my face :smile:. When I choose fullscreen, Ekiga only uses the lower-right quarter of the screen, with the same cropped image. In windows, the webcam works flawlessly. Is this an Ekiga or driver problem? Has anyone had the same problem?

Thanks in advance, Pedro

---

### Post by Pulka on 2006-07-08
bump

---

### Post by argotnaut on 2007-01-14
From [http://www.gnomemeeting.org/index.php?rub=3&pos=0&faqpage=x201.html](http://www.gnomemeeting.org/index.php?rub=3&pos=0&faqpage=x201.html) :

> 7.1.2. Ekiga only displays a part of the real picture in the video window, what can I do?

If your driver doesn't natively support 176x144, Ekiga will try capturing at a larger size, and scale the picture down. If the picture isn't scaled, please report the problem to us on the mailing list. 

---

