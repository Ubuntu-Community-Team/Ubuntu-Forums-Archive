---
title: "k9copy not works on 10.04"
date: 2010-07-31
forum: Multimedia Software
---

### Post by Formicula on 2010-07-31
Hello,

on 8.04 everything was allright with k9copy. I lost it with my last hard drive.

on 10.04 k9copy crashes using c9copy assistant chosing DVD drive and next.
even in k9copy without assistant the treeview (display) is empty and it crashes with 'open'.
_________________________________________________________________
Report:
p, li { white-space: pre-wrap; }

Application: k9copy (k9copy), signal: Segmentation fault

[KCrash Handler]

#6 0x081405bc in ?? ()

#7 0x08130001 in ?? ()

#8 0x080da77f in _start ()
_________________________________________________________________
I tried from another source:

1)Install libdvdread4:

sudo apt-get install libdvdread4

2)Install lipdvdcss2:

sudo /usr/share/doc/libdvdread4/install-css.sh

BUT THIS DOES NOT WORK FOR K9COPY.

libdvdread4 was already installed.

libdvdcss2 was not installed.

Installed lipdvdcss2 makes VLC working to play these DVDs and
MoviePlayer shows no more error messages but the display is black.
Instead MoviePlayer is looking now for a suitalble codec: without success.

Thank you for a working proposal.

PS: I own .kde in my home folder, even the rights are 777. 
Its the 32 bit version of 10.04  on a Fujitsu-Siemens ESPRIMO E 5615.

---

