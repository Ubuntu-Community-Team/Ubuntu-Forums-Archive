---
title: "Can't play audio cd's"
date: 2010-01-01
forum: Multimedia Software
---

### Post by ahayzen on 2010-01-01
Hi

I am having trouble running audio cd's in my second ubuntu 9.10 machine. However normal cd's run in the drive and I have tested the cd's on my first machine.

Under computer the cd drive icon disappears.

can anyone help?

Andy

---

### Post by ahayzen on 2010-01-01
I tried running the drive through terminal and got this:

```

andy@ubuntu-desktop:~$ totem cdda://

(totem:1971): GStreamer-WARNING **: Name queue is not unique in bin uridecodebin0, not adding

(totem:1971): GStreamer-CRITICAL **: gst_caps_get_structure: assertion `index < caps->structs->len' failed

(totem:1971): GStreamer-CRITICAL **: gst_structure_get_name: assertion `structure != NULL' failed

(totem:1971): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(totem:1971): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(totem:1971): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(totem:1971): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(totem:1971): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(totem:1971): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(totem:1971): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed
** Message: no file info
** Message: Error: Could not open CD device for reading.
gstcdparanoiasrc.c(286): gst_cd_paranoia_src_open (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstCdParanoiaSrc:source:
cdda_identify failed

** Message: Error: Could not open CD device for reading.
gstcdparanoiasrc.c(286): gst_cd_paranoia_src_open (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstCdParanoiaSrc:source:
cdda_identify failed

```

---

### Post by ahayzen on 2010-01-01
Also this is my fstab

```

andy@ubuntu-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=cfd77428-453a-4917-9a2a-fa311bab587b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5f4d848-0057-4459-bb81-689002616300 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Sorry for putting over 3 posts.

---

