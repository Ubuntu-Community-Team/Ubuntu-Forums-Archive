---
title: "nvidia-settings and nvidia-xconfig issues"
date: 2009-02-23
forum: Multimedia Software
---

### Post by Snypercell on 2009-02-23
8.04 64bit nvidia 7 series

-in order to install nvidia settings, i followed these instructions after a fresh install: [http://my.opera.com/sjosul/blog/index.dml/tag/Ubuntu%208.04](http://my.opera.com/sjosul/blog/index.dml/tag/Ubuntu%208.04)

-once installed, attempted to open the menu via: sudo nvidia-xconfig

-got an error: You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

tried to run nvidia-xconfig, but got this message: Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'



can anyone assist me?

---

### Post by Snypercell on 2009-02-23
just rebooted system, and poof!!! back to norml.
not sure what happened

---

### Post by cariboo on 2009-02-23
When installing a new video driver or if you edit /etc/X11/xorg.conf, you have to restart X for the changes to take place. To restart X press Ctrl-Alt-Backspace or reboot.

Jim

---

### Post by ejaz.sayyed@gmail.com on 2009-03-07
Hi,

I also got the same error message twice but, after doing the 

after doing  $ sudo nvidia-xconfig

VALIDATION ERROR: 

control+alt+backspace I donno what happened and I was put in high resolution mode.

Thanks to Control+Alt+Backspace

---

