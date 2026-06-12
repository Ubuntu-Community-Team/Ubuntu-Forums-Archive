---
title: "Dropping back to the open source ATI drivers though the command line"
date: 2009-08-13
forum: Multimedia Software
---

### Post by second.exodous on 2009-08-13
Hey, I tried to update to the latest ATI graphics driver with their .run package that builds ubuntu/jaunty .deb packages but on reboot my computer borked.

With recovery mode I can get to a command line, what are the commands to get the opensouce driver back so I can boot into a gui again?

Also, is there a guide somewhere that explains how to install the latest 64 bit dirvers for ATI?  I couldn't find any and thought if I just installed the .deb packages that the .run file from ATI made I'd be fine, but apparently it's a little more than that.

Thanx,
Stan

---

### Post by markbuntu on 2009-08-13
The easiest way to recover from a bad graphics driver install is to boot into the recovery mode kernel and use the fix x option. 

Did you remove the old driver before updating?
You really need to do that.
To remove the driver installed from the ati site use the script
sudo usr/share/ati/fglrx-uninstall.sh

---

