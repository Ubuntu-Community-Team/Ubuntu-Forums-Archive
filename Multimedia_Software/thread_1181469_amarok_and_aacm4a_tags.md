---
title: "amarok and aac/m4a tags"
date: 2009-06-07
forum: Multimedia Software
---

### Post by logos34 on 2009-06-07
Wish I'd known that adding read+write support for Apple .m4a to Amarok was as easy as installing Medibuntu "amarok-engines" pkg:

> $ apt-cache show amarok-engines
Package: amarok-engines
Source: amarok
Version: 2:1.4.9.1-0ubuntu3.2+medibuntu1
Architecture: amd64
Maintainer: **Medibuntu** Packaging Team <admin@lists.medibuntu.org>
Installed-Size: 20
Depends: amarok-xine
Homepage: [http://amarok.kde.org](http://amarok.kde.org)
Priority: optional
Section: free/kde
Filename: pool/free/a/amarok/amarok-engines_1.4.9.1-0ubuntu3.2+medibuntu1_amd64.deb
Size: 1070
SHA256: a435154cf349209f6d20b41d0c303c09417ea687048421b3113093cd63d72d9f
SHA1: edd491284adc3131ac32f95ad5c08b6fcdc53494
MD5sum: 4c174fa578ae9ab57cc4d0d5f43d310a
Description: output engines for the Amarok audio player - Medibuntu package
 This package depends on all the available Amarok engines, and it's
 installed by default [COLOR="Blue"]unless you specify a particular engine[/COLOR]. You can
 safely remove it, as you can remove the amarok-$engine packages that
 you don't use.
 .
[COLOR="Blue"] This package is built with Itunes AAC-LC (.m4a) support enabled.
 Therefore, it is in Medibuntu as it might violate patents.[/COLOR]
 .
 This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU!
 .
 Please report any bug to our bug tracker instead:
  [https://bugs.launchpad.net/medibuntu/+bugs](https://bugs.launchpad.net/medibuntu/+bugs)
Original-Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>

Which is different from the regular ubuntu repo version (which lacks aac support):

> Package: amarok-engines
Priority: optional
Section: universe/kde
Installed-Size: 20
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Adeodato Simó <dato@net.com.org.es>
Architecture: amd64
Source: amarok
Version: 2:1.4.9.1-0ubuntu3
Depends: amarok-xine
Filename: pool/universe/a/amarok/amarok-engines_1.4.9.1-0ubuntu3_amd64.deb
Size: 892
MD5sum: 1d23c2a214f19f901508cec62009191c
SHA1: 498141ef1c57eef51adb898bcf5064d7fbae509c
SHA256: 257069744acecdc80b20cfeca7a3b95e39686c8ef691f02563be6d3084cd7ced
Description: output engines for the Amarok audio player
 This package depends on all the available Amarok engines, and it's
 installed by default unless you specify a particular engine. You can
 safely remove it, as you can remove the amarok-$engine packages that
 you don't use.
Homepage: [http://amarok.kde.org](http://amarok.kde.org)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

And here I was thinking I had to compile from source **--with-mp4v2** option...

Not only does the Medibuntu amarok-engine support AAC-LC (low-complexity) format, it can read .m4a tags 100% correctly (right down to bitrate--a problem before), AND allow you to EDIT the tags (which I also lacked).  Half my music is archived in apple .m4a lossless (.alac), which amarok couldn't display properly or edit

My mistake was in specifying **amarok-xine** engine ONLY...

DUH!  learn sth new every day it seems

how did I miss that?

---

