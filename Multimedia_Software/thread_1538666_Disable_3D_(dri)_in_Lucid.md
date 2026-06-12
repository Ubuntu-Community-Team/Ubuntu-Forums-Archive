---
title: "Disable 3D (dri) in Lucid?"
date: 2010-07-25
forum: Multimedia Software
---

### Post by kleeman on 2010-07-25
I want to switch off 3d i.e. dri on my laptop to save power. There is a bug in the intel video driver that makes it generate excess wakeups and thus increase power consumption. I don't use 3d so this is very annoying.

I have tried modifying /etc/X11/xorg.conf to insert an "NODRI" option in the  "Device" section and have commented out both of the "load dri" commands in the "Modules" section. No go. When I look in the xorg log, these changes are seen but not acted on. The system appears to have hardwired defaults set somewhere which are difficult to override. Any advice on how to get round this would be great. It appears to be a new issue because with Karmic one still had control with xorg.conf.

Just generally I don't like changes like this because it is not documented on the wiki where and how to change the defaults in Lucid. Linux was supposed to be easily configurable so IMHO this is a step backwards.

---

### Post by Yellow Pasque on 2010-07-25
> Option "DRI" "boolean"
Disable or enable DRI support.   Default:  DRI  is  enabled  for
configurations where it is supported.
[http://manpages.ubuntu.com/manpages/intrepid/man4/intel.4.html](http://manpages.ubuntu.com/manpages/intrepid/man4/intel.4.html)

---

