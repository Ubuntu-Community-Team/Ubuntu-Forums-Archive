---
title: "philips SPC210NC  skype not displaying the video"
date: 2009-01-02
forum: Multimedia Software
---

### Post by Ant68 on 2009-01-02
Hi,
I am running intrepid (8.10). I have just set up Skype 2.0.0.72 (of the skype website.

I have a webcam  Philips SPC210NC - 0471:032d that I can see works when I start Cheese. I have read the page [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) that says this webcam works for Skype & ubuntu 8.10

When I try to use this webcam with skype, skype video window shows a weird output (see attached image). It does not display the video?

Anything I should do?

thanks for your help.

---

### Post by Ant68 on 2009-01-02
hi,
more details. I have run lsmod and got:

my-desktop:~$ lsmod | grep videodev
videodev               41344  1 gspca_main
v4l1_compat            22404  1 videodev


I have also set up the following package:
skype-debian_2.0.0.72-1_i386.deb 

[http://skype.com/intl/en-gb/download/skype/linux/choose/](http://skype.com/intl/en-gb/download/skype/linux/choose/)
coming with ubuntu 7.x 8.04 (there is no ubuntu package for 8.10 on the skype website).

any ideas how to troubleshoot this issue?

---

### Post by /carlito on 2009-01-02
I'm experiencing the same problem on my mothers pc. I'm checking on how to troubleshoot this issue and will inform yuo when i get the error fixed. 

Since it's working with cheese it shouldn't be to hard to resolve this issue imho.

---

