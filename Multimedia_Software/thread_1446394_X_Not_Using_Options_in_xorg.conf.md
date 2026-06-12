---
title: "X Not Using Options in xorg.conf"
date: 2010-04-04
forum: Multimedia Software
---

### Post by X-Malleus on 2010-04-04
Hey guys,

I'm using an Intel 965 GM graphics chip with the "intel" driver.  I'm curious as to why it doesn't seem to be using any of the options that I'm placing under the Device section of xorg.conf.  Here's an example:

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
    Option        "AccelMethod"    "XAA"
EndSection

In my Xorg.0.log file, I get the following message:

(WW) intel(0): Option "AccelMethod" is not used

Why would it not be allowing me to use options such as this?  I know that my driver and video card are compatible with this option, as is indicated in this manual:

[http://manpages.ubuntu.com/manpages/intrepid/man4/intel.4.html](http://manpages.ubuntu.com/manpages/intrepid/man4/intel.4.html)

---

### Post by pebo on 2010-04-04
That manual page is out of date. If you run ```
man intel
```in a terminal you will see that there is no longer the "XAA" option. There have been many changes to the intel driver recently and options such as XAA and EXA are no longer available. Any reason for needing XAA?
Edit: I just noticed that the man page you linked is for ubuntu 8.10 - and the driver is version 2.4.1. Ubuntu 9.10 is using version 2.9.0. Which one are you using?

---

