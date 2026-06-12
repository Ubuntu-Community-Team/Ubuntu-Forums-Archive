---
title: "VLC fonts problem in Karmic"
date: 2009-11-04
forum: Multimedia Software
---

### Post by nu2linux6 on 2009-11-04
Hi,

Just upgraded to Karmic from Jaunty. All went well, but for some reason the fonts in VLC are all jagged (i.e. no font smoothing).

This seems rather odd as they were fine in Jaunty, and I don't have any problems with fonts in other applications.

Tried upgrading to VLC 1.0.3, but the jagged fonts remain.

Any help would be much appreciated! Thanks.

---

### Post by uniden9 on 2009-11-04
I believe videolan / VLC uses qt for fonts.  I know to increase the size of the fonts the only place I could do it.  It also lets you specify the fonts.  You may have to install qtconfig package, as it was not installed by default on earlier releases of ubuntu.   You should see it under System->Preferences->QT 4 Settings    this may fix your problem.

sudo apt-get install qt4-qtconfig


Justin

---

### Post by ~unknown on 2009-11-04
VLC has the same problem as Firefox, or at least the solution to the Firefox font problem fixed VLC and Skype also. See this link for more info: [http://www.webupd8.org/2009/07/fix-fonts-in-firefox-35-and-ubuntu.html](http://www.webupd8.org/2009/07/fix-fonts-in-firefox-35-and-ubuntu.html)

---

### Post by nu2linux6 on 2009-11-04
Thanks for the replies. I followed the instructions to create .fonts.conf, and that fixed the problem. It seems QT4 needs that file to render fonts properly, whereas QT3 doesn't.

Thanks again.

---

