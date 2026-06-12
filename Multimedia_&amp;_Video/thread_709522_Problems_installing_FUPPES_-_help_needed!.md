---
title: "Problems installing FUPPES - help needed!"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by SumnerBoy on 2008-02-27
Hi - I am very keen to try FUPPES so I can stream FLACs to my XBox 360. I have been following the instructions at [http://ubuntuforums.org/showthread.php?t=597650](http://ubuntuforums.org/showthread.php?t=597650) as I am running Ubuntu 7.10 Server Edition.

However I am failing at the very first step! When I run the apt-get install command I get the following message...

```
ben@weka:~$ sudo apt-get install ffmpeg build-essential libavutil-dev libavformat-dev libavcodec-dev subversion libtool automake autoconf libsqlite3-dev libpcre3-dev libxml2-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
libavutil-dev is already the newest version.
libavutil-dev set to manual installed.
libavformat-dev is already the newest version.
libavcodec-dev is already the newest version.
libavcodec-dev set to manual installed.
subversion is already the newest version.
libtool is already the newest version.
automake is already the newest version.
autoconf is already the newest version.
autoconf set to manual installed.
libsqlite3-dev is already the newest version.
libpcre3-dev is already the newest version.
libxml2-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodeccvs51 (>= 3:20071206) but it is not going to be installed
          Depends: libavdevicecvs52 (>= 3:20071206) but it is not going to be installed
          Depends: libavformatcvs52 (>= 3:20071206) but it is not going to be installed
          Depends: libavutilcvs49 (>= 3:20071206) but it is not going to be installed
          Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
          Depends: libswscalecvs0 (>= 3:20071206) but it is not going to be installed
E: Broken packages
ben@weka:~$
```

Any one got any ideas as to why these dependencies are broken?

---

