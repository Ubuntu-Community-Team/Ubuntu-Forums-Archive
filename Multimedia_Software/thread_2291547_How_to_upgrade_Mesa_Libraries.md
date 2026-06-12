---
title: "How to upgrade Mesa Libraries"
date: 2015-08-20
forum: Multimedia Software
---

### Post by convert_mrta on 2015-08-20
So my question is how do I safely install Mesa 10.5.2 or at least something better than 10.1.3?

I need to run a productivity application which needs the newer Mesa libraries than what I have installed - "opengl.version"="3.0 Mesa 10.1.3"
I found the latest production version for Mesa to be 10.5.2 and downloaded all of the .deb files for it from [https://launchpad.net/ubuntu/+source/me](https://launchpad.net/ubuntu/+source/me) ... ld/7120720

As I attempt to install the .debs with Ubuntu software center, I'm running into ominous warnings that I fear to ignore as I don't want to hose my system.
libegl1-mesa_10.5.2-0ubuntu1_amd64.deb warns Error: Breaks the existing package "libwayland-egl1-mesa"
libgbm1 - "error: cannot satisfy dependencies"
libgl1-mesa-dri_10.5.2-0ubuntu1_amd64 - "error: cannot satisfy dependencies"
libgl1-mesa-glx_10.5.2-0ubuntu1_amd64 - no error, but install button greyed out.
libglapi-mesa_10.5.2-0ubuntu1_amd64 - Error: Breaks the existing package "libgles2-mesa"

all the rest result in "error: cannot satisfy dependencies" ALL Say "An older version is available in a software channel. It is recommended to install the version from the software channel . . ." But I don't want OLDER, I need the new.

So I figure why not use synaptic and remove the old Mesa 10.1.3. Then install the new, avoiding the conflict. It gets even scarier! I tagged libGLU1 for removal and the "Mark additionial required changes" prompt pops up and dozens of my core apps are in the list . . . like cairo dock, everything libreoffice base core and calc etc., nemo, xorg, libqt, skype. I'm asked to select them too. Whoa, WHOAH, this is critical stuff! So I cancel.

So my question is how do I safely install Mesa 10.5.2 or at least something better than 10.1.3

I did an apt-get update, followed by apt-get dist-upgrade. Did nothing to mesa, still on 10.1.3.

Would I be better adding a _trustworthy_ repository and updating? What's the best way to do this?

Thanks much,

Greg

---

### Post by Bucky Ball on 2015-08-21
*Thread moved to **Multimedia Software**.*

---

### Post by monkeybrain20122 on 2015-08-21
Before you do anything make sure that newer mesa does support higher version of OpenGL because it can be that this is the best mesa or your graphic card can do. If you know that newer mesa would help then you have a few options:

There is [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) which offers mesa 11 (the same as mesa 10.7). But it only supports 14.04, 14.04.1 and 15.04 and will break your system if you have 14.04.2 or 14.04.3 from iso (ok if you installed 14.04 or 14.04.1  from iso and updated to 14.04.3  normally without using the hardware enablement stack)  [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa) offers the older 10.6 but the same story, not work for 14.04.2 and 3 if you have enabled hware enablement stack.

Have ppa-purge ready for either, in case things don't work you can downgrade the packages (or clone your system before). And if it works disable the ppa since you don't want to upgrade everyday (oibaf) or every few days (xorg-edgers) until your system breaks.

You can also try to compile mesa locally (build it in some local folder and use it by using environmental variables without installing into the system so it won't break things) [http://pkg-xorg.alioth.debian.org/howto/build-mesa.html](http://pkg-xorg.alioth.debian.org/howto/build-mesa.html)

Finally 15.04 comes with mesa 10.5 (so a simple way to find out whether a newer version of mesa would solve your problem would be to make a live usb for Ubuntu 15.04,  boot off it and install mesa-utils and check the OpenGL version)

---

