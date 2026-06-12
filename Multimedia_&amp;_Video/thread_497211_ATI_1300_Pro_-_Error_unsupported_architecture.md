---
title: "ATI 1300 Pro - Error: unsupported architecture"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by JesterDev on 2007-07-10
I'm trying to install the drivers from ATI.com:

[PHP]
bash ./ati-driver-installer-8.38.6-x86.x86_64.run --buildpkg Ubuntu/feisty
[/PHP]

and this is the result:

[PHP]
Generating package: Ubuntu/feisty
./packages/Ubuntu/ati-packager.sh: 180: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.o19936
[/PHP]

Now I'm assuming that there is no package for ubuntu in there? Any suggestions?
The drivers install fine on OpenSuse, and DreamLinux but it did you good there anyway.

---

