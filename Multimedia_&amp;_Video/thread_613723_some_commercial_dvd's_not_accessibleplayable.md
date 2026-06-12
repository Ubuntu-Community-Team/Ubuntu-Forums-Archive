---
title: "some commercial dvd's not accessible/playable"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by Ba66e77 on 2007-11-15
I'm baffled.  Since upgrading to Gutsy, _some_ commercial DVD's are not recognized at all.  I put them in, the drive spins up briefly, then nothing: no icon on the desktop and all the programs read like nothing is there.  

CD's work fine, data DVD's work fine, homemade video DVD's work fine, and some commercial video DVD's work.  

The disks that don't work are read fine on my Windows box.  

It's consistent as to which videos do and don't work.  The ones that work always work, the ones that don't never work.

Output messages are below.  Can anyone give me some pointers on where to look for a fix?

_output of regionset: _
$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
[U]
Kaffein output:[/U]
xine Message 
The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (/dev/dvd)

xine Error
No plugin found to handle this resource (dvd://)
Details
xine: cannot find input plugin for MRL [dvd://]
xine: input plugin cannot open MRL [dvd://]
xine: found input plugin: DVD Navigator

_VLC output:_
dvdread error: DVDRead cannot open source: /dev/scd0
vcd error: could not read TOCHDR
vcd error: no movie tracks found
access_file error: file /dev/scd0 is empty, aborting
cdda error: could not read TOCHDR
cdda error: no audio tracks found
main error: no suitable access module for `dvd:///dev/scd0'

---

### Post by tears.of.angels on 2007-11-15
have you tried installing the libdvdcss2 package? i know that's fixed some dvd issues i've had before.

they're not in ubuntu's official repo's, i got it from medibuntu

```
deb http://packages.medibuntu.org/ gutsy free non-free #Medibuntu
```

the gpg key is at:

packages.medibuntu.org/medibuntu-key.gpg

---

### Post by Ba66e77 on 2007-11-15
Thanks, tears, but I do have libdvdcss2 installed

---

