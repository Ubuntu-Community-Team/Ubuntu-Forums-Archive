---
title: "Install Xlib/Xfree86??"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by SugarBlush on 2007-12-08
I tried to install wine 0.9.50 from source but I got this error while I ./configure it...

```
configure: WARNING: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need to install
development packages of Xlib/Xfree86 at the very least.

configure: WARNING: FontForge is missing.
Fonts will not be built. Dialog text may be invisible or unaligned.

Configure finished. Do 'make depend && make' to compile Wine.
```

The question is, where can I download Xlib/Xfree86?? I tried searching it on synaptic but its nowhere to be found.

Also, how do you install Xlib/Xfree86?

Thanks,
SugarBlush

---

### Post by SugarBlush on 2007-12-08
> **SugarBlush said:**
> I tried to install wine 0.9.50 from source but I got this error while I ./configure it...

```
configure: WARNING: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need to install
development packages of Xlib/Xfree86 at the very least.

configure: WARNING: FontForge is missing.
Fonts will not be built. Dialog text may be invisible or unaligned.

Configure finished. Do 'make depend && make' to compile Wine.
```

The question is, where can I download Xlib/Xfree86?? I tried searching it on synaptic but its nowhere to be found.

Also, how do you install Xlib/Xfree86?

Thanks,
SugarBlush

pls pls pls! anybody! pls!
how to install xlib/xfree86?

---

### Post by Yellow Pasque on 2007-12-08
[http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

The package you really want is probably x-dev

---

### Post by SugarBlush on 2007-12-08
> **Temüjin said:**
> [http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

The package you really want is probably x-dev

where & how can I get it?

---

### Post by Yellow Pasque on 2007-12-08
Is there a reason you're trying to build WINE instead of just getting the package straight from their repo?:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```

---

### Post by SamZor on 2008-05-15
This error means you do not have the appropriate packages installed when building wine. It still works however its missing functionality (most of which is required to run the fun stuff like 3d games :) )

[http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

apt-cache search and apt-cache install each of these:

# bison
# flex
# gcc
# libc6-dev
# libfontconfig-dev (libfontconfig1-dev)
# libfreetype6-dev
# libgl-dev (libgl1-mesa-dev or xlibmesa-gl-dev)
# libglu-dev (libglu1-mesa-dev or xlibmesa-glu-dev)
# libgphoto2-dev (libgphoto2-2-dev)
# libice-dev
# libjpeg-dev (libjpeg62-dev)
# libldap-dev (libldap2-dev)
# libncurses5-dev
# libpng-dev (libpng12-dev)
# libsm-dev
# libssl-dev
# libusb-dev
# libx11-dev
# libxcomposite-dev
# libxcursor-dev
# libxext-dev
# libxi-dev
# libxinerama-dev
# libxml2-dev
# libxrandr-dev
# libxrender-dev
# libxslt-dev (libxslt1-dev)
# libxt-dev
# libxxf86vm-dev
# make
# x-dev

then do this:

./configure CC=gcc-4.2 --verbose
(whatever version of gcc you are using... it wil tell you what you are missing.

---

### Post by Vock on 2008-06-17
> This error means you do not have the appropriate packages installed when building wine. It still works however its missing functionality (most of which is required to run the fun stuff like 3d games  )

[http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

apt-cache search and apt-cache install each of these:

# bison
# flex
# gcc
# libc6-dev
# libfontconfig-dev (libfontconfig1-dev)
# libfreetype6-dev
# libgl-dev (libgl1-mesa-dev or xlibmesa-gl-dev)
# libglu-dev (libglu1-mesa-dev or xlibmesa-glu-dev)
# libgphoto2-dev (libgphoto2-2-dev)
# libice-dev
# libjpeg-dev (libjpeg62-dev)
# libldap-dev (libldap2-dev)
# libncurses5-dev...........
Is it recommended to do this even if you install WINE straight from the depot? and also, by apt-cache install, do you mean apt-cache add? Install doesn't seem to be a valid option in ubuntu....

---

