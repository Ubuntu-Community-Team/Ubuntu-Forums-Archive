---
title: "Creating ISO headache"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by Son of Silas on 2008-01-19
I have a PC running Gutsy that I plan to stack to the rafters with ISO images of DVDs then leave ACIDRIP to churn its way through them all creating XVID Files.

The problem I have is some of my DVDs will not let me create ISO images of them. The method I am using is thus:

* Pop the DVD in the drive.
* An Icon appears on the desktop for it
* I right click the Icon and select 'Copy Disc...'
* A dialogue box opens and I select 'File Image' fro the 'Copy Disc to' box
* Click 'write'

This seems to work for about half my DVDs, but the rest appear to copy normally, but the resulting .ISO file is tiny (400 - 900kb)

Any ideas what's happening or how I can easily create straight .ISO copies of DVDs without shrinking them, re-encoding them etc..?

---

### Post by disturbed1 on 2008-01-19
Install libdvdcss2 ( [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/) )
Install vobcopy (via apt-get)

do 
vobcopy -m

libdvdcss2 to decrypt the DVD, vobcopy, as the name says ;) -m means to mirror, copy entire contents. This will create a directory for the name of the DVD, and decrypt and copy the contents of the VIDEO_TS folder.

You can then point acidrip to that directory.

Be forewarned, libdvdcss2 can only break older css copy protection, not the newer ARCOS, RIPGUARD, or others. For these, you'll need to run either RipItForMe to create a PLS with DVDDecrypter then clean it with fixvts, or run DVDFab through wine.

---

