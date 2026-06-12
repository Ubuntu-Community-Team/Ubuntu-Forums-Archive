---
title: "Don't quite understand video driver error message"
date: 2009-03-16
forum: Multimedia Software
---

### Post by jacatone on 2009-03-16
I used Synaptic to install the nvidia-glx-96 driver but when I try to configure it I get the error message attached below. The terminal result gives me:

jacatone@eMax ~ $ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.

Anyone know what I do here? Thanks.

---

### Post by norwoods on 2009-03-16
you have to run with sudo to have the authority to write to directory '/etc/X11'.
jacatone@eMax ~ $sudo nvidia-xconfig

---

