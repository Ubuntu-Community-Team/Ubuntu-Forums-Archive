---
title: "Problem installing VLC 2"
date: 2012-07-05
forum: Multimedia Software
---

### Post by gamblor01 on 2012-07-05
I was attempting to install the latest VLC as documented in this post:

[http://www.omgubuntu.co.uk/2012/07/how-to-upgrade-to-the-latest-vlc-release-in-ubuntu-12-04](http://www.omgubuntu.co.uk/2012/07/how-to-upgrade-to-the-latest-vlc-release-in-ubuntu-12-04)


For some reason it failed to install.  I tried apt-get install -f but this resolved nothing.  It looks like someone commented on that post reporting the same issue but no one has offered any solutions.  I just installed this (64-bit precise) on this laptop like 3 days ago so it's a clean install.  I have installed a few packages thus far (restricted extras, build-essential, bless, meld, tofrodos, thunderbird) but otherwise I really haven't done much.  Any ideas?


```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.0.2+git20120704+r280-0~r39~precise1) but it is not going to be installed
       Depends: libvlccore5 (>= 2.0.0) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.0.2+git20120704+r280-0~r39~precise1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.2+git20120704+r280-0~r39~precise1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
bdmayes@ubuntubook:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by msammels on 2012-07-05
Please try installing VLC 2.0.2 from [here](http://www.videolan.org/vlc/download-ubuntu.html).

---

### Post by gamblor01 on 2012-07-05
Unfortunately that didn't work either.  I clicked on the link that they had and it launched software center.  However, it's still giving errors:

```

The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.2+git20120704+r280-0~r39~precise1) but 2.0.2+git20120704+r280-0~r39~precise1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.3ubuntu0.12.04.1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.3ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.1 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.1 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed

```


EDIT: Actually I'm thinking that this might be a problem with their PPA -- I just realized that the dependencies specify the specific git revision which doesn't seem right.  I would think that it should specify a particular branch.  Maybe I'm wrong but for now I just removed the PPA from my system and installed the older vlc package from the standard repo instead.

---

