---
title: "Xine, Gxine and Totem dont play MPEG Layer 2/3 Movie Files"
date: 2006-05-29
forum: Multimedia &amp; Video
---

### Post by James Gardner on 2006-05-29
Hi!
I've just installed Ubuntu Dapper Drake 6.06 beta 2 and I'm very impressed with how easy it is to install, configure everything (my printer only took about 15 seconds to set up!!) however.. i seem to be having some problems playing MPEG Layer 2/3 audio through xine, Gxine and Movie Player... they dont seem to be able to find the required audio codec... I've searched these forums for similar topics and found [This Thread]("http://http://ubuntuforums.org/showthread.php?t=36141&highlight=Mpeg+Layer+2%2F3") which says i should install libmad0.. unfortunately this lib is already installed.. and reinstalling the library still doesn't make xine find the audio codec...

i have libxine-main1 1.1.1+ubuntu2-7 and
          xine-ui  0.99.4-0ubuntu6
packages installed...
any suggestions what to do next???
Thanks In Advance..
    James

---

### Post by frodon on 2006-05-29
You should read that : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by James Gardner on 2006-05-29
Success!
After reading the RestrictedFormats page, i installed all the gstreamer plugins... however apt-get couldn't find libxine-extracodecs
after a quick google search, i found packages.ubuntu.com which gave me download
[locations]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fx%2Fxine-extracodecs%2Flibxine-extracodecs_1.1.1%2Bubuntu1-2_i386.deb&md5sum=5512ee45d3d0c9dd30f2588512729aa8&arch=i386&type=main") for the package... i tried my local mirror (planetmirror.com.au) and it doesn't seem to have libxine-extracodecs so i downloaded it from another site and installed it with
dpkg -i libxine-extracodecs_1.1.1+ubuntu1-2_i386.deb
and everything seems to be running fine... although xine doesn't use the system volume level
Thanks for your help!
    James

---

