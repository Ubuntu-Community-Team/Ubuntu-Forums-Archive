---
title: "GIMPShop Doesn't recognise filetypes"
date: 2013-01-08
forum: Multimedia Software
---

### Post by VegasTamborini on 2013-01-08
Hey guys, first post, I hope I got the right category.

As part of some professional development for work I have to complete an online Photoshop course (my work obviously assuming I use Windows/Mac). I have tried installing Photoshop through WINE with no success and my next port of call was to get the Gimpshop addon for GIMP. 

I downloaded it from UbuntuGeek and installed it as per any program.
The program appears to start-up just fine, however, upon opening any type of image file I get the error message:

"_**GIMP Message**_

Opening '/home/user/filepath/imagename.jpg' failed:

Unknown file type"

It's the same for saving new images that I create inside GIMP.

Upon inspection of the terminal, this is the output:

"/usr/local/lib/gimp/2.0/plug-ins/xjt: error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory

(gimp:4137): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:4137): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/wmf: error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory

(gimp:4137): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/helpbrowser: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

(gimp:4137): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/jpeg: error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory

(gimp:4137): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/mng: error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory

(gimp:4137): LibGimpBase-WARNING **: gimp: wire_read(): error"

Tried to reinstall with the following command:
"sudo apt-get install --reinstall libgimp2.0"

But nothing changed.

Any input would be appreciated.

Thanks in advance, Vegas

PS, I know GIMP/Gimpshop still isn't Photoshop, but as long as I can just bang out some images and send them what I've done, it should be enough.

---

### Post by ibjsb4 on 2013-01-08
Could you give us a link to that download source.

---

### Post by VegasTamborini on 2013-01-08
Sure thing, here it is:

[www.ubuntugeek.com/images/gimpshop_2.2.11-1_i386.deb](www.ubuntugeek.com/images/gimpshop_2.2.11-1_i386.deb)

---

### Post by ibjsb4 on 2013-01-08
This looks like where you got your download.

[http://www.ubuntugeek.com/howto-install-gimpshop-in-ubuntu-hardy.html](http://www.ubuntugeek.com/howto-install-gimpshop-in-ubuntu-hardy.html)

If this is so, that download it for Ubuntu Hardy 8.04 and you are probably running 12.04 or 12.10.

I had a look around for an updated GimpShop and found this.

[http://askubuntu.com/questions/229513/gimpshop-2-8-available-for-win-mac-no-linux-version](http://askubuntu.com/questions/229513/gimpshop-2-8-available-for-win-mac-no-linux-version)

---

### Post by VegasTamborini on 2013-01-08
Haha, now I feel stupid, you're completely right. I found Ubuntu after 8.04 and didn't realise what 'Hardy' meant from the title. Thanks for taking the time to help.

---

### Post by ibjsb4 on 2013-01-08
If your not making mistakes, your not learning :) and welcome to the forums.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

