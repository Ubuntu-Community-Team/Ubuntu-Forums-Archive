---
title: "Diskless frontend with weekly mythtv"
date: 2009-08-16
forum: Mythbuntu
---

### Post by row_perfect on 2009-08-16
Hi Guys,

I'm a mythbuntu newbie. I've set up the backend to use the weekly trunk build as described [here]("http://www.mythbuntu.org/auto-builds") and it's working nicely.

Prior to switching to weekly mythtv build, I successfully set up a diskless boot as using the mythbuntu control panel. After switching to weekly build, I deleted the /opt/ltsp/i386 and /var/lib/tftpboot/ltsp/i386 directories and tried to recreate the diskless image. Unfortunately both using the UI and instructions [here]("https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless") (using sudo ltsp-build-client --mythbuntu --mythbuntu-copy-user-credentials --copy-package-cache --copy-package-lists --copy-sourceslist) it always references the 0.21 myth packages.

I'm completely at a loss as to how to get the right packages in the image.

Any help would be greatly appreciated.

Paul

---

### Post by raptorjr on 2009-08-31
I have a question about this also. Also using weekly i have installed diskless-server and dhcp server manually. But in control-center there is no option to build the disk image. And in system roles the diskless server options is selected but all greyed out. I guess they are selected because i installed them, but i cant configure the diskless server. Is there a beta version or something for control-center that i could try where this works?

---

### Post by mitchell2345 on 2009-08-31
see [http://ubuntuforums.org/showthread.php?t=1219535](http://ubuntuforums.org/showthread.php?t=1219535)

---

