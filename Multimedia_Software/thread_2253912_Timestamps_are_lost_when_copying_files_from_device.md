---
title: "Timestamps are lost when copying files from devices (pcmanfm, gphoto2)"
date: 2014-11-23
forum: Multimedia Software
---

### Post by vesa33 on 2014-11-23
Hi everyone,

When I connect a Canon IXUS digital camera via USB to the computer running Lubuntu 14.10, the system first asks if I want to open the device in file manager. If I do, a file manager window opens with the address line showing something beginning with "gphoto2://". If I use it to copy image or video files to my computer, timestamps of the files are lost.

However, when I use the command line interface of gphoto2 to copy files, timestamps are preserved. So, the problem seems to be in how the file manager (pcmanfm, I suppose) or some other component of the system uses the (lib)gphoto2 interface.

The same problem of losing timestamps with the default file manager access also happens when connecting to a Samsung Android phone that uses the MTP protocol.

Is this problem really in pcmanfm or in how it is configured to use external connections such as (lib)gphoto2 ?

Thanks for any help.

---

### Post by bapoumba on 2014-11-23
Maybe some info here : [http://ubuntuforums.org/showthread.php?t=2187432](http://ubuntuforums.org/showthread.php?t=2187432)
Bug report here : [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1175947](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1175947)

Not related to lubuntu or the file browser it seems.

---

