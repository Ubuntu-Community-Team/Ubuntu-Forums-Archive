---
title: "Is there a program to format Dvd-rw?"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by jbayone on 2007-01-27
Can you format a Dvd with k3b or anything else?  I'm not at home right now, just wondering how I would go about this.

---

### Post by will0957 on 2007-01-27
search :)
[http://ubuntuforums.org/showthread.php?t=298954&highlight=format+dvd+rw](http://ubuntuforums.org/showthread.php?t=298954&highlight=format+dvd+rw)

---

### Post by jbayone on 2007-01-27
Thanks, I forgot about GnomeBaker

---

### Post by umayado on 2008-06-17
using gnomebaker i get an extremely irritating sound followed by this :

Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p User -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-user/gnomebaker-W0H5CU | builtin_dd of=/dev/sr0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
:-[ PERFORM OPC failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error

Help please!

thanks in advance

---

### Post by umayado on 2008-06-17
after the second try, (after formatting via tools) i get the same annoying sound when trying to burn and this message :

Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p user -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-user/gnomebaker-803RCU | builtin_dd of=/dev/sr0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
:-[ PERFORM OPC failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error


by the way my formatting is done in 44 secs....

---

### Post by umayado on 2008-06-17
Could not open location 'burn:///'
The default action does not support this protocol.


when trying to open the empty disk via nautilus...

---

