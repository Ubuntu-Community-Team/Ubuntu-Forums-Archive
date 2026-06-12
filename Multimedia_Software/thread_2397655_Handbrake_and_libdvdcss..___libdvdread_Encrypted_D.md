---
title: "Handbrake and libdvdcss..   libdvdread: Encrypted DVD support unavailable."
date: 2018-08-01
forum: Multimedia Software
---

### Post by NMeyne on 2018-08-01
Hi All,

VLC is installed and plays my DVD perfectly on bionic, but for some reason Handbrake fails to unscramble the video and gives the message libdvdread: Encrypted DVD support unavailable.   I have followed instructions to uninstall, reinstall and configure libdvd-pkg.  libdvdcss2 version 1.4.2.1~local is installed.  Perhaps handbrake-jz isn't able to invoke it?    Videos (Totem) just crashes...   no errors given.
Any ideas / suggestions?  Thanks,  Nick

---

### Post by deadflowr on 2018-08-01
Isn't handbrake-jz the snap version.
In which case it has no access to the standard system libraries such as libdvdcss.
Perhaps look for the Debian/apt version of handbrake.
There should be a version in the Ubuntu repositories.
Or I think it still has a PPA, if that suits you:
[https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases")
The apt version should give access to the system libraries and allow use of the libdvdcss libraries.

---

### Post by NMeyne on 2018-08-01
Thanks!  I have tried it with both the snap and apt versions and unfortunately they give the same result.
By the way, there is another error in the log:
LibThai: Fail to open dictionary at '/usr/share/libthai/thbrk.tri'.
libdvdread: Encrypted DVD support unavailable.

thbrk.tri exists and is owned by root...  maybe it's corrupt?

---

### Post by NMeyne on 2018-08-01
Wait...  NO!   I hadn't properly purged the snap version.  Sorry!.   Many thanks for help...  looks OK now!

So: snap versions are best avoided where access to non-standard libs, multimedia files and codecs are involved.

Regards and Thanks,  Nick

---

