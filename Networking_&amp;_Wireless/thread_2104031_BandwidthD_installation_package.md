---
title: "BandwidthD installation package?"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-01-11
I'm trying to download bandwidth D with no success.  I simply downloaded the .deb file and the Ubu Software Center tells me to run it through my normal installation channels.  I tried to run: apt-get install bandwidthd and it says: 
"Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
(Reading database ... 290152 files and directories currently installed.)
Removing bandwidthd:i386 ...
/etc/init.d/bandwidthd: 19: /etc/init.d/bandwidthd: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing bandwidthd:i386 (--remove):
 subprocess installed pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: /etc/init.d/bandwidthd: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bandwidthd:i386"

I tried just running dpkg on the .deb file and got no where.  Is the package just broken?  Or is my package manager broken? Or is it something weird with bandwidthd?  Thanks for the help.

---

### Post by SlugSlug on 2013-01-14
bandwidthd is in the repos you don't need the deb.

Try purging and reinstalling using the repos...

```
sudo apt-get remove --purge bandwidthd; sudo apt-get update; sudo apt-get autoremove; sudo apt-get install bandwidthd
```

---

### Post by psyllex on 2013-01-14
Thanks for that.  I used your commands and then I reinstalled.  I needed to make some small changes to bandwitdth.conf and apache2.conf and it runs like a champ now.  Thanks alot!:lolflag:

---

