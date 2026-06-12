---
title: "Opening files on &quot;windoze&quot; box from GIMP"
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by Tomlin on 2006-01-06
I'm having problems opening .jpg files (on a windoze 2000 machine) across a network with GIMP.

I have Samba set up and I can connect to the win box by:

clicking on "Places"
"browse the network" (shared win machines come up)
dbl click on the win box and fill in Username, domain and PW (shares come up)
right click on share and choose "connect to this server" (share shows up on desktop)

I'm assuming it's now mounted, because right clicking shows the option to unmount it.

When I dbl click on a .jpg file, it opens "Eye of GNOME 2.10.0" and I can edit it, etc. But if I right click and choose open with "GIMP Image Editor", I get 2 errors:

JPEG image message
Could not open 'root/smb://windozemachine/sharename/pic.jpg' for reading:
no such file or directory

AND

GIMP message
opening 'root/smb://windozemachine/sharename/pic.jpg' failed:
Plug-In could not open image.

From within GIMP, if I click on File, Open - there isn't any way to specify a filename such as smb://whatever. My options (in the left pane) are:

Home
Desktop
Filesystem
Floppy Drive
CD-RW/DVD+RW Drive
CD-RW Drive

I also can't open .pdf files from a different share on the same win box using Acrobat Reader 7.0. I get:

Couldn't display "smb://windozemachine/sharename/blah.pdf".

If I copy the files to the Ubuntu 5.04 machine, I can open both files fine.

Any ideas?

TIA,

Tomlin

---

### Post by MetalMusicAddict on 2006-01-06
Ive seen this also. I wonder If it happens on a Linux only network also?

---

