---
title: "AMDCCCLE and Dual Monitors"
date: 2012-09-03
forum: Multimedia Software
---

### Post by tweetubunt on 2012-09-03
I'm running Ubuntu 12.04 with an ATI Radeon HD 5450 card, two monitors: a Dell E196FP which I believe should be 1280x1024 and a Vizio HDTV (VO320E) which I think should be 1280x720 (its a 720 resolution). The Vizio is set to 1280x1024 in the Catalyst Control Center and if I change it, or if I try to enable dual monitors, the program crashes and I get this output in terminal:

(process:14738 ) : GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.3/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:14738 ) : GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:14738 ) : GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.3/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:14738 ) : GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:14738 ) : GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

My entire xorg.conf file:

Section "Screen"
Identifier	"Default Screen"
DefaultDepth	24
EndSection

Section "Module"
Load	"glx"
EndSection

I have to think that has something to do with it. I attached a screen shot of the CCC.

Bottom line: I'd like the multi-display desktop to work and set the Vizio to the proper settings. If I need to rewrite the xorg.conf file, specific help with that would be appreciated. Let me know if I've forgotten anything, thanks.

---

### Post by QIII on 2012-09-03
How did you install the driver and the control center?

---

### Post by tweetubunt on 2012-09-03
Its been a while but I found these commands in terminal history so pretty sure this is how I did it:

  280  sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
  281  sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot
  282  cd ~/; mkdir catalyst12.4; cd catalyst12.4/
  283  wget [http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run)
  284  chmod +x amd-driver-installer-12-4-x86.x86_64.run
  285  ./amd-driver-installer-12-4-x86.x86_64.run --extract driver
  286  cd driver/common/lib/modules/fglrx/build_mod/
  287  wget -O fglrx.patch [http://ubuntuone.com/5gNgEmVfzs3ytD5QZ2YGCi](http://ubuntuone.com/5gNgEmVfzs3ytD5QZ2YGCi)
  288  patch -p1 < fglrx.patch
  289  cd ~/catalyst12.4/driver/
  290  ./ati-installer.sh 8.961 --buildpkg Ubuntu/precise
  291  cd ../
  292  sudo dpkg -i fglrx*.deb
  293  sudo cp /usr/lib64/switchlib* /usr/lib64/fglrx/
  294  cd /usr/lib64/switchlib
  295  cd ..
  296  cd usr
  297  cd lib64
  298  cd..
  299  cd ..
  300  cd usr
  301  cd ..
  302  cd usr
  303  cd lib64
  304  cd ..
  305  sudo cp /usr/lib32/switchlib* /usr/lib32/fglrx/
  306  cd usr
  307  cd lib32
  308  ls
  309  cd lib
  310  ls
  311  exit
  312  gksu amdcccle
  313  exit
  314  pcsc_scan
  315  cd ~/catalyst12.4/driver/
  316  ls
  317  cd ../
  318  sudo dpkg -i fglrx*.deb
  319  fglrxinfo
  320  sudo amdcccle

---

