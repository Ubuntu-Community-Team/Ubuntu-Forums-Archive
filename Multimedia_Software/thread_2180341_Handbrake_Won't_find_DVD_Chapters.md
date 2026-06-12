---
title: "Handbrake Won't find DVD Chapters"
date: 2013-10-12
forum: Multimedia Software
---

### Post by AlexHudghton on 2013-10-12
Ubuntu 12.04 up to date as from today 12 Oct 2013

Installed Handbrake and after faffing around for an hour got it up an running

Recognises the name of the DVD and does the scan through the chapters fine

At the end of the scan it can't do anything, because there is no Chapter selected to transfer.

Same with 3 DVD's I've tried, which all play fine and can be copied with Windows DVD Decrypter

Any Ideas please?

---

### Post by hannaman on 2013-10-14
Do the DVDs play in Ubuntu or just Windows?  Have you installed libdvdcss?
Instructions for installing libdvdcss: [https://help.ubuntu.com/community/RestrictedFormats#Addlibdvdccs](https://help.ubuntu.com/community/RestrictedFormats#Addlibdvdccs)
Or if you would prefer a repository: [http://gauvain.pocentek.net/node/61](http://gauvain.pocentek.net/node/61)

Other than that, when I have had DVDs that Handbrake couldn't get the main title for, I would use MakeMKV to rip the main title and then use Handbrake to transcode it to mp4.
MakeMKV for Linux: [http://www.makemkv.com/forum2/viewforum.php?f=3&sid=bea74a2d0e09c714144d00436e6097f7](http://www.makemkv.com/forum2/viewforum.php?f=3&sid=bea74a2d0e09c714144d00436e6097f7)

---

### Post by AlexHudghton on 2013-10-14
Hi, thanks for replying

DVDs will only play in windows

I get an error about a missing decryption library

Your link also,says to do this;
sudo /usr/share/doc/libdvdread4/install-css.sh

but that errors as well

alex@desktop:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2013-10-14 20:09:02--  [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'
Dynamic fetch failed; Falling back to static fetch
--2013-10-14 20:09:12--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'

---

### Post by hannaman on 2013-10-14
Sounds like you have an outdated libdvdread4.  Medibuntu has been shut down, so the updated script uses VideoLan now instead for css.
This post [http://ubuntuforums.org/showthread.php?t=2178960&page=3&p=12815012&viewfull=1#post12815012](http://ubuntuforums.org/showthread.php?t=2178960&page=3&p=12815012&viewfull=1#post12815012) describes how to update to the new libdvdread4.
That should get DVDs working for you.

---

### Post by AlexHudghton on 2013-10-15
> **hannaman said:**
> Sounds like you have an outdated libdvdread4.  Medibuntu has been shut down, so the updated script uses VideoLan now instead for css.
This post [http://ubuntuforums.org/showthread.php?t=2178960&page=3&p=12815012&viewfull=1#post12815012](http://ubuntuforums.org/showthread.php?t=2178960&page=3&p=12815012&viewfull=1#post12815012) describes how to update to the new libdvdread4.
That should get DVDs working for you.

You were spot on :cool:

I now have working DVD and handbrake :D

Thanks again

---

