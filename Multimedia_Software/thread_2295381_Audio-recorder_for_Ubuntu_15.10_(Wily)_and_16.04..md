---
title: "Audio-recorder for Ubuntu 15.10 (Wily) and 16.04."
date: 2015-09-18
forum: Multimedia Software
---

### Post by moma on 2015-09-18
EDIT: Audio-recorder for Ubuntu 17.04 (Zesty Zapus) is ready!  
Please See:
[https://ubuntuforums.org/showthread.php?t=2349495](https://ubuntuforums.org/showthread.php?t=2349495)
------------

Audio-recorder v1.7-5 is now ready for Ubuntu 15.10 and 16.04:
You are welcome to use it. 

PACKAGES FOR UBUNTU 15.04, 15.10, 16.04 AND LATER:
THIS IS A NEW PPA THAT BELONGS TO THE TEAM AUDIO-RECORDER.
[https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa)

PACKAGES FOR UBUNTU 14.10 AND OLDER:
THIS INCLUDES LINUX-MINT 13, 17 AND ALL 17.x.
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

SOURCE CODE:
[https://launchpad.net/~audio-recorder](https://launchpad.net/~audio-recorder)

This version can be compiled and run on any modern Linux-distro that has GTK 3.14+ and Gstreamer 1.4.
[[IMG]http://bildr.no/thumb/1305665.jpeg[/IMG]]("http://bildr.no/view/1305665")

[[img]http://bildr.no/thumb/TEVJUUdL.jpeg[/img]](http://bildr.no/view/TEVJUUdL)

Sejam bem-vindos!
Moma, 
Palmela/Portugal -- rocks too.

---

### Post by moma on 2015-11-22
Re-hi,
Audio-recorder is already available for 16.04 Xenial Xerus (pre).

---

### Post by oygle on 2016-11-03
> **moma said:**
> Re-hi,
Audio-recorder is already available for 16.04 Xenial Xerus (pre).

I installed vers 1.7.5 today and got an error message ..

```
audio-recorder
```

> audio-recorder: error while loading shared libraries: libappindicator3.so.1: cannot open shared object file: No such file or directory

I installed it as per the instructions at [https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa)

---

### Post by mc4man on 2016-11-05
> **oygle said:**
> I installed vers 1.7.5 today and got an error message ..

```
audio-recorder
```



I installed it as per the instructions at [https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa)
You would need to have the libappindicator3-1 package installed to get that .so Whether that's an issue in Kubuntu no idea..

To check if there are any other missing run this, look for any  'not found'
```
ldd /usr/bin/audio-recorder
```

---

### Post by oygle on 2016-11-05
> **mc4man said:**
> You would need to have the libappindicator3-1 package installed to get that .so Whether that's an issue in Kubuntu no idea..

The change log for that package states ..

> 
libappindicator (12.10.1+15.04.20141110-0ubuntu1) vivid; urgency=low

  [ Lars Uebernickel ]
  * scroll-event: change parameter to the right type

 -- Ubuntu daily release <ps-jenkins@lists.canonical.com>  Mon, 10 Nov 2014 16:30:06 +0000


But I'm not sure of other packages that are dependant upon it. Synaptic package manager tells me that libappindicator3-1 package is **NOT** currently installed.

> **mc4man said:**
> 
To check if there are any other missing run this, look for any  'not found'
```
ldd /usr/bin/audio-recorder
```

Only one entry found ..

> 
libappindicator3.so.1 => not found


Thanks for your help.  :)

---

### Post by mc4man on 2016-11-05
> **oygle said:**
> The change log for that package states ..



But I'm not sure of other packages that are dependant upon it. Synaptic package manager tells me that libappindicator3-1 package is **NOT** currently installed.



Only one entry found ..



Thanks for your help.  :) Well I guess you could try to install it though 15.10 (wily) is end of life so not sure where you'd stand there. (- did you switch to old-release repos? or consider moving to 16.04

On a side note, libappindicator3-1 is not an install dep but libappindicator3-dev is a build dep. Probably libappindicator3-1 should have been explicitly added to the package's control file.

---

### Post by oygle on 2016-11-05
> **mc4man said:**
> - did you switch to old-release repos? or consider moving to 16.04

Have done a fresh install of 16.04.1 in the last few weeks. So, not wanting to change releases.  :)

> **mc4man said:**
> 
On a side note, libappindicator3-1 is not an install dep but libappindicator3-dev is a build dep. Probably libappindicator3-1 should have been explicitly added to the package's control file.

Do you think if I install the package libappindicator3-1 , that will fix the problem at present ?

---

### Post by mc4man on 2016-11-05
> **oygle said:**
> Have done a fresh install of 16.04.1 in the last few weeks. So, not wanting to change releases.  :)



Do you think if I install the package libappindicator3-1 , that will fix the problem at present ?
Try - I not sure why I thought you had wily (15.10), probably from the thread title

---

### Post by oygle on 2016-11-05
> **mc4man said:**
> Try - I not sure why I thought you had wily (15.10), probably from the thread title

Yes, I should have started a new thread possibly.  :)

---

### Post by moma on 2016-11-06
Hello,
Look, audio-recorder is a GTK/GNOME application. I do not know if it can run on a KDE-based desktop (like Kubuntu).
KDE has propably its own audio stack and recorder software.

Nevertheless, try search for libappindicator package in your system. Run: 
$ apt-cache search libappindicator

Then, if the package is found, apt-get it with: 
$ sudo apt install PACKAGENAME

---

