---
title: "Not able install VLC media player or media plugins after upgarding to Ubuntu 14.04"
date: 2014-08-30
forum: Multimedia Software
---

### Post by rakesh-r on 2014-08-30
Hi,

I upgraded my Ubuntu from 12.04 to 14.04. Now when i try to install VLC player, i get the following error...[B]
1. [/B]----------------------------------------------------------------------
" Package dependencies cannot be resolved"

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.1.4+git20140821+r54575+19+11~ubuntu14.04.1) but 2.1.4+git20140821+r54575+19+11~ubuntu14.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.19-0ubuntu6.3 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.5.2-1ubuntu2.2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
     Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.8.2-19ubuntu1 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
----------------------------------------------------------------------------
When i try to install media plugins for Videos,
**2.** -------------------------------------------
" Package dependencies cannot be resolved"

This error could be  caused by required additional software packages which are missing or not  installable. Furthermore there could be a conflict between software  packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

 The following packages have unmet dependencies:

gstreamer1.0-libav: Depends: libavcodec-extra-54 (>= 6:9.13) but 6:9.16-0ubuntu0.14.04.1 is to be installed
                    Depends: libavformat54 (>= 6:9.1-1) but 6:9.16-0ubuntu0.14.04.1 is to be installed
                    Depends: libavutil52 (>= 6:9.1-1) but 6:9.16-0ubuntu0.14.04.1 is to be installed
                    Depends: libc6 (>= 2.14) but 2.19-0ubuntu6.3 is to be installed
                    Depends: libglib2.0-0 (>= 2.37.3) but 2.40.0-2 is to be installed
--------------------------------------------------

Please help me to solve either one of the issues or both. I m not able to watch any videos on my Ubuntu.

---

### Post by TBerk on 2014-08-31
Q) What method are you using to install VLC?

Command Line/Terminal?
Software Center?
Synaptics?

Following the OS Update from 12.x to 14.x, youve rebooted the system at least once, correct?

Have you gone about verifying youve selected more than the minimal Repositories enabled during an Install/Upgrade?  (Multiverse, Restricted, Canonical Partners, etc). I've noticed some you might expect to be there get deactivated during the upgrade proccess. 

Following (re)eneabeling of those repositories, perform an update with the following command:

```
 sudo apt-get update
```

Also I'd run  ```
sudo apt-get install -f
```   to help resolve broken dependancies...

While we're at, it I was wondering if you had added a OS specic VLC repository entry in the past?

report back...

---

### Post by jimbob3 on 2014-08-31
thanks

---

