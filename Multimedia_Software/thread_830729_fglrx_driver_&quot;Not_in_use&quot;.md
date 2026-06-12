---
title: "fglrx driver &quot;Not in use&quot;"
date: 2008-06-16
forum: Multimedia Software
---

### Post by xst on 2008-06-16
I use Kubuntu/Hardy and have tried to intsall the ATI drivers using K > System > Hardware Drivers Manager. However, the driver is "Not in use" even though I *have* rebooted.

I have, without success, tried a lot of stuff in order to make it work, including:

1)
$ grep DISAB /etc/default/linux-restricted-modules-common
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
DISABLED_MODULES=""


2)
$ dpkg -l | grep xserver-xgl
$


3) Running "depmod -a" and reboot


4)
$  DISPLAY=:0 glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


5)
$  modprobe -l | grep fglrx
/lib/modules/2.6.24-19-generic/volatile/fglrx.ko


6)
$ lsmod | grep fglrx
$
(Hmm, strange! Shouldn't it show something here?)

Any ideas?

---

