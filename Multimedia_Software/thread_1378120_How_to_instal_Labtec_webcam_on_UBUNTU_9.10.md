---
title: "How to instal Labtec webcam on UBUNTU 9.10?"
date: 2010-01-11
forum: Multimedia Software
---

### Post by Kohary on 2010-01-11
Hi,
I would like to make video calls on SKype with my Labtec laptop webcam, but the only picture I get is a green picture with some stripes...
Is it possible to do anything with it?

---

### Post by lorsen on 2010-01-12
Did you have a look at this page [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) ?

---

### Post by okkadiroglu on 2010-01-31
Hi,

I am trying to use A4 Tech PK-5 webcam with Skype on a AMD64. I get the usual green screen when I try the Options in Skype. I have Cheese working without any problems. I read and tried to do most of the things given in [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam). I tried to use easycam2 but could not find it and install it as well as phyton-xml. I had similar problem when I upgraded my computer to Kubuntu 8.04 but somehow it disappeared then. I guess it has something to do with the drivers related to webcam and Skype but I do not know what to do.

Manythanks fpr the help, Best Regards

---

### Post by okkadiroglu on 2010-02-02
Hi,

I have solved my problem.:D I downloaded Skype 2.1.0.81 and installed it in /usr/local/Skype Then created a skype file in /usr/local/bin with 

bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/local/Skype/skype'

and everything works well.;)

Many thanks for the help. I hope I can be help to others.


Best Regards

---

### Post by hencke on 2010-02-07
Thank you lorsen and okkadiroglu for the link and reporting the problem solved. I also got my webcam working thanks to the information. To sum up what I would do if I wanted video working in skype:

**1. Make sure your webcam works in other programs** (e.g. Cheese (Applications>Ubuntu Software center, type cheese, click install))

**2. Try** these commands in the terminal (or check with the File Browser to see where v4lcompat.so is located):

**```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' 
```**

(for 32-bit installations?)

```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
```

(for 64-bit installations?)

**3. Test that video works in skype** (Options>Video devices(>Select webcam)>Test

**4. When everything works**, open System>Preferences>Main Menu, choose Applications>Internet>Skype>Properties and **replace the Command with the command that worked in step 2.**

Additional information:

I used to use the Karmic medibuntu [1] package for skype (2.1.0.47) and my webcam worked fine. However, I uninstalled it and installed the new version (2.1.0.81) straight from the .deb-installer from the skype homepage [2]. The video didn't work in this new version and when I tried to install the old version from medibuntu I noticed it was no longer there. I managed to find the old version (2.1.0.47) as a static package and .deb-installer, but neither had working video. From link Ubuntu help [3]:

"old drivers (before Ubuntu 8.10) had the code to decode the data received from the webcam, the new drivers (since 8.10) don't. instead they assume decoding it always done somewhere else. The applications which use the older assumptions have to be provided with the additional (compatibility and decoding) library. "

I assume old drivers refers to v4l (v4l1) and new drivers refers to v4l2. Apparently skype doesn't load v4l1-compatibility (which is used for some older webcams) automatically (except for the medibuntu package? which is no longer available), but you have to do it manually by the command okkadiroglu used (probably for 64-bit users?) or the command found in the link [3] lorsen gave (which I used on my 32-bit Ubuntu 9.10).

Links:

[1] [http://www.medibuntu.org/](http://www.medibuntu.org/)

[2] [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

[3] [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by miroi on 2010-05-03
Dear all,

with my Labtec webcam, the solution of  bash -c 'LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype' is not working, neither the bash -c 'LD_PRELOAD=/usr/lib64/libv4l/v4l2convert.so skype command.

The error message is 
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

My skype is for ubuntu 64 bit package at [http://www.skype.com/go/getskype-linux-beta-ubuntu-64](http://www.skype.com/go/getskype-linux-beta-ubuntu-64).

Any help ?

Thanks.
=====================================
Now I have solved it ! Skype is linked against plenty of 32-bit libraries, as is clear from here:

ldd /usr/bin/skype 
    linux-gate.so.1 =>  (0xf77bb000)
    libasound.so.2 => /usr/lib32/libasound.so.2 (0xf76d0000)
    libXv.so.1 => /usr/lib32/libXv.so.1 (0xf76ca000)
    libXss.so.1 => /usr/lib3bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype'2/libXss.so.1 (0xf76c5000)
    librt.so.1 => /lib32/librt.so.1 (0xf76bc000)
    libQtDBus.so.4 => /usr/lib32/libQtDBus.so.4 (0xf7643000)
    libQtGui.so.4 => /usr/lib32/libQtGui.so.4 (0xf6bc7000)

I have to link it against 32 bit "libv4l" library:
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype'

Now accroding to Skype options the labtec camera is working well !
===============================================

I have also created the script which starts Skype properly;

1. sudo mv /usr/bin/skype /usr/bin/skype_orig
2. sudo vim /usr/bin/skype:
#!/bin/bash
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype_orig'
exit
3. chmod ugo+x /usr/bin/skype

---

