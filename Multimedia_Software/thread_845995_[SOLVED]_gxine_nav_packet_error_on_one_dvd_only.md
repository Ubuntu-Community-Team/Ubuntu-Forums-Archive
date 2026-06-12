---
title: "[SOLVED] gxine nav packet error on one dvd only"
date: 2008-07-01
forum: Multimedia Software
---

### Post by bryncoles on 2008-07-01
ok, i have a problem with one (and so far, only one) of my DVD's. 

i prefer to use gxine to view dvds, as i just like the interface. it plays all my collection fine, except my (shop bought) dvd of Rammsteins Volkerball. with that dvd alone, gxine spits out two errors: 

'error reading from nav packet'

and when i try and load the dvd anyway

'segmentation fault'.

ive also tried vlc player and lindvd (im using a dell inspiron 1525, with ubuntu pre-installed). they dont like this one rammstein dvd either. 

im running hardy heron - is ubuntu just critical of my musical taste? its annoying that just this one dvd will not play when everything else seems fine! and im sure it used to play on my old laptop under gutsy (not sure i ever tried it under hardy on that one). 

can anyone help me watch my German industrial metal...?

*edit*

also: i get the error message 'encrypted or faulty dvd'. i suspect encrypted, as the dvd plays fine on an actual dvd player...
 
is there something i should install to work round the encryption? i have libdvdnav4 and libdvdread3 installed already...

*edit*

duh!

i just found (and followed) 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and got that repo, and then libdvdcss2 installed. now my one dvd plays again! yay! 

so a big thank-you to the ubuntu documentation teams!

red face me!

---

