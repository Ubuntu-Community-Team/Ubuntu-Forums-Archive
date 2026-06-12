---
title: "problems installing wxcam in karmic"
date: 2009-11-22
forum: Multimedia Software
---

### Post by Mojomagus on 2009-11-22
So yeah, the title pretty much says it, I can't install wxcam on karmic. 
The package installer gives me the following error:

Error: Dependency is not satisfiable: libmjpegtools0c2a (>= 1:1.8.0)

Anyone have any ideas?

---

### Post by Rytron on 2009-12-08
I too get this same message. Can anyone solve this?

---

### Post by Ferretti on 2009-12-31
Sorry for the late reply! I was stumbling upon these forums looking to find out what the problem was. I did, however, find a working version that will install on 9.10. Here is the direct link to the download: [http://mirrors.dotsrc.org/getdeb/ubuntu/jaunty/wx/wxcam_1.0.4-1~getdeb1_i386.deb](http://mirrors.dotsrc.org/getdeb/ubuntu/jaunty/wx/wxcam_1.0.4-1~getdeb1_i386.deb)

---

### Post by Rytron on 2010-01-01
> **Ferretti said:**
> Sorry for the late reply! I was stumbling upon these forums looking to find out what the problem was. I did, however, find a working version that will install on 9.10. Here is the direct link to the download: [http://mirrors.dotsrc.org/getdeb/ubuntu/jaunty/wx/wxcam_1.0.4-1~getdeb1_i386.deb](http://mirrors.dotsrc.org/getdeb/ubuntu/jaunty/wx/wxcam_1.0.4-1~getdeb1_i386.deb)

Thank you very much Ferretti. All sorted! :)

---

### Post by Ferretti on 2010-01-01
No problem! Glad I could help. Happy New Year!

---

### Post by redDEADresolve on 2010-01-03
[http://old.getdeb.net/release/4251](http://old.getdeb.net/release/4251)

wxcam 64bit .deb from getdeb.net

---

### Post by Doc_Jude on 2010-01-04
> **Ferretti said:**
> Sorry for the late reply! I was stumbling upon these forums looking to find out what the problem was. I did, however, find a working version that will install on 9.10. Here is the direct link to the download: [http://mirrors.dotsrc.org/getdeb/ubuntu/jaunty/wx/wxcam_1.0.4-1~getdeb1_i386.deb]("http://mirrors.dotsrc.org/getdeb/ubuntu/jaunty/wx/wxcam_1.0.4-1%7Egetdeb1_i386.deb")

the video is smooth and gorgeous compared to Cheese.... but no audio. at System>Sound>Input it's set to "0804 Analog Mono" which I believe is the webcam (Logitech Webcam C250, formerly worked in both Cheese and Skype just find)

---

### Post by no2498 on 2010-01-19
its odd but look at the colors green on left red on the right
1.0.2 works right on 804
im on 910 on this computer
and an going nuts trying to fix red green not green red
if you turn the cam pic color comes up right but pic is wrong
btw i can adjust the settings in cheese
but not in wxcam
best i can say is rgb is backwards in wxcam 104
and the fps is slow only 5 at best

---

### Post by Daymond on 2011-06-16
I am having a problem with installation of wxcam, but in Natty Warhal. I receive the following error when running the make command:


daymond@daymond-PowerEdge-SC420:~/Downloads/wxcam-1.1$ make install
Making install in src
make[1]: Entering directory `/home/daymond/Downloads/wxcam-1.1/src'
  CXX    audio.o
In file included from audio.cpp:21:0:
audio.h:22:28: fatal error: alsa/asoundlib.h: No such file or directory
compilation terminated.
make[1]: *** [audio.o] Error 1
make[1]: Leaving directory `/home/daymond/Downloads/wxcam-1.1/src'
make: *** [install-recursive] Error 1

---

### Post by Rytron on 2011-06-16
Hi Daymond. Can you try one of the deb files @ [http://sourceforge.net/projects/wxcam/files/wxcam/?](http://sourceforge.net/projects/wxcam/files/wxcam/?)

---

### Post by Daymond on 2011-06-16
> **Rytron said:**
> Hi Daymond. Can you try one of the deb files @ [http://sourceforge.net/projects/wxcam/files/wxcam/?](http://sourceforge.net/projects/wxcam/files/wxcam/?)

Hi Rytron. Are you suggesting using an older version of the deb? I am currently working with wxcam-1.1

---

### Post by Daymond on 2011-06-16
> **Daymond said:**
> Hi Rytron. Are you suggesting using an older version of the deb? I am currently working with wxcam-1.1

NM, I see what you were getting at here. I downloaded the tar.gz and by downloading the .deb I was able to install directly through the Software Center. Thanks! Now I just have to figure out why the Microphone on my Microsoft LifeCam doesn't work. I get great video, but no sound.

---

### Post by Rytron on 2011-06-17
> **Daymond said:**
> NM, I see what you were getting at here. I downloaded the tar.gz and by downloading the .deb I was able to install directly through the Software Center. Thanks! Now I just have to figure out why the Microphone on my Microsoft LifeCam doesn't work. I get great video, but no sound.

It is not just you, I have never got sound working in wxCam. Yes, I always noticed the video quality to be A1 in wxCam.

Try this:

```
sudo wxcam
```

It would be great if someone could post a way to get audio in wxCam. :idea:

---

### Post by Rytron on 2011-06-17
Actually I'm not sure if sudo wxcam is needed.

If you launch just wxcam and goto Video Preferences and select xvid – I was able to record internal audio but not my voice.

---

