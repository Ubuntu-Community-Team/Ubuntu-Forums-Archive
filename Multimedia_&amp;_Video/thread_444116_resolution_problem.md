---
title: "resolution problem"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by jeffrock on 2007-05-15
OK, so I've finally got 7.04 installed, and running, with network :-D

Installed the new nvidia drivers using this thread...
[http://doc.gwos.org/index.php/Latest_nvidia_feisty#WHAT_TO_DO_IF_THE_METHOD_YOU_CHOSE_DID_NOT_WORK_OR_WORKED_PARTIALLY](http://doc.gwos.org/index.php/Latest_nvidia_feisty#WHAT_TO_DO_IF_THE_METHOD_YOU_CHOSE_DID_NOT_WORK_OR_WORKED_PARTIALLY)
worked fine...no problems, I know they are installed correctly because it shows up under "restriceted drivers" and is enabled...
Anyways, the real problem...my resolution...
I cant get runnign at 1680x1050 :/
Ive also read the thread over editing xorg.conf, and adding modeline, etc...
here is a copy of my /etc/x11/xorg.conf, hopefully someone can spot out what i am doing/did wrong? 


Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-84
        VertRefresh     43-65
 # V-freq: 60.00 Hz  // h-freq: 65.35 KHz
 Modeline "1680x1050" 149.00  1680 1760 1944 2280  1050 1050 1052 1089
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV43 [GeForce 6600 GT]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1280x768"


I didnt include the videocard section, right above those sections, let me know if it would help,
Thanks everyone...

---

### Post by heimo on 2007-05-15
Some random collection of information, which may help:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/67369](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/67369)
[http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_(WSXGA](http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_(WSXGA))
[http://thoughtworker.in/2007/04/24/kubuntu-704-feisty-fawn-getting-right-resolution/](http://thoughtworker.in/2007/04/24/kubuntu-704-feisty-fawn-getting-right-resolution/)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/67369/comments/21](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/67369/comments/21)

---

### Post by jeffrock on 2007-05-15
Hey, I read those post, they seem interesting, but nothing that helped, tried manually editing the xorg file some more, but to no avail. I can't even get it out of 640x480, which sucks horribly, because the "quick reply" box on the forums takes the entire screen on firefox.. and I have to guess at context boxes that are out of my viewing range lol. 
but thanks for your help man, great help thread in your comment, I read over it at least a dozen times last night. Any other ideas would be great. 
I read the one post about that guy who updated his nvidia glx using apt,, but I was toying witht hat last ngiht, and it said there was a conflict with a package already installed, and I am guessing my nvidia driver is up to date regardless, so I didn't want to uninstall it and install that other package, if it won't help anything.Thanks again. 
Heart, jeff

---

### Post by heimo on 2007-05-15
If you can get decent resolution with nv driver, I'd use that. Actually, I do use nv driver.

---

