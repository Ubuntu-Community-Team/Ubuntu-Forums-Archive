---
title: "help in finding bootscript for slmodemd"
date: 2006-03-10
forum: Networking &amp; Wireless
---

### Post by melquiades on 2006-03-10
guys,

        I've a fresh installation of Ubuntu 5.10 in my lappy. I've successfully installed
my modem driver and I'm actually using a dial-up connection while composing this message. My problem is that I can't figure out how to load the modem driver and slmodemd automatically during bootup. I looked for a script on the downloaded SLMODEMD archive but I can't find one for ubuntu. Help anyone, please? I'd really appreciate some.

Thanks in advance,
melquiades

---

### Post by mpvano on 2006-03-10
I don't know how you installed things and set them up, but i'm using the sl-modem-daemon package from the breezy repositories to do all that.

This was the only package I needed to install to get support for my modem via the intel audio ALSA driver which is already present in breezy.

sl-modem-daemon added the init scripts, and config files and set things up so it automatically is installed at boot. If I recall correctly the only thing I needed to do was to edit /etc/default/sl-modem-daemon to set the variable that enables automatic loading.

If you built new modules or installed them some other way, you may not be able to use the package in the repository without some modifications, but installing it might be a good start.

Here's what apt-cache show prints for sl-modem-daemon...................

mvano@targ3:~$ apt-cache show sl-modem-daemon
Package: sl-modem-daemon
Priority: optional
Section: multiverse/misc
Installed-Size: 1004
Maintainer: Eduard Bloch <blade@debian.org>
Architecture: i386
Source: sl-modem
Version: 2.9.10+2.9.9d-6ubuntu1
Provides: slmodem
Depends: libasound2 (>> 1.0.9), libc6 (>= 2.3.4-1), debconf
Conflicts: sl-modem-modules
Filename: pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386 .deb
Size: 416104
MD5sum: 8f67b8b3ce6fdef952b9ebcfada7c7c6
Description: SmartLink software modem daemon
 The SmartLink modem daemon is the application part of the
 driver for recent modems produced by Smart Link Ltd.
 .
 This package replaces (along with hardware access drivers) the old
 driver generation (2.7.x) which consisted of kernel modules only.
 .
 It needs a kernel driver to access the hardware. This can be either
 recent ALSA (shipped with a newer kernel (>=2.6.4) with Alsa support
 and intel8x0m module) which is sufficient for basic operation and
 data/Internet connection, or the SmartLink kernel driver which is
 provided by separate packages which you can build using the source from
 the sl-modem-source package.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by melquiades on 2006-03-11
thanks for the advice. i already installed sl-modem-daemon via synaptic and voila,
i have /dev/ttySL0 every bootup. My problem now is that wvdial can't dial as it used to; I checked sl-modem-daemon and to my consternation i learned it was invoked with USA as country setting. I need to replace it with the correct setting, which for me is PHILIPPINES, for it to have any use to me. How's this done, i have no clue. please help

---

