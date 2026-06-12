---
title: "Anyone know of reliable DVD Backup Software"
date: 2009-07-12
forum: Multimedia Software
---

### Post by Geekkit on 2009-07-12
I'm in Ubuntu 8.10 and I'm trying to burn DVD data disks. I've tried the following:

1) K3B but it gives me the following cryptic message:
"No such file or directory. Invalid node"

The file **does** exist and so not sure why it doesn't like the file.

2) Brasero but I can't drag and drop files from within itself. It reports:

"(brasero:14637): Gtk-CRITICAL **: gtk_drag_begin: assertion `targets != NULL' failed"

However if I drag drop files from Nautilus this works ... about 2 - 3 times ... and then Brasero just crashes - disappears with this cryptic message:

"(brasero:14637): Gtk-CRITICAL **: gtk_drag_set_icon_default: assertion `GDK_IS_DRAG_CONTEXT (context)' failed
Segmentation fault"

3) I tried GnomeBaker but got this when I tried to burn:
Executing 'genisoimage -gui -V bckup200907v1 -A GnomeBaker -p user123 -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-user123/gnomebaker-8EJYWU | builtin_dd of=/dev/sr0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Directories too deep for 'devel/Java/JEE/Seam/templates/Seam-Template/thirdparty/libs' (7) max is 6.
:-( write failed: Input/output error

4) I tried with CD/DVD Creator via Nautilus but it fails and pops up a dialog box stating:

"Error Writing to Disc. There was an error writing to the disc: Unhanded error, aborting."

I'm having to set up network shares in XP and Vista just so that I can perform backups of my Linux computer (Nero in XP and Vista just work).

Anyone have any suggestions for a CD/DVD writing software application in Linux that actually works? I need to back up my Linux directories in Linux.

Any help most appreciated.

---

