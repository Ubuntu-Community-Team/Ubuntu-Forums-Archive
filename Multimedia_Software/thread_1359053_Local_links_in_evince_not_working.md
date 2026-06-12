---
title: "Local links in evince not working"
date: 2009-12-19
forum: Multimedia Software
---

### Post by flostre on 2009-12-19
Hi,

I'm using pdflatex in the version coming with Ubuntu 9.10 (version string see bottom of my post). I'm creating a pdf which contains links to other pdf files and webpages using the package hyperref. Link to webpages and to pdf files on the internet works great (i.e. when the address is sth like "http://www.example.edu/pubs/SmitheeEtAl99.pdf"). However, linking to local files does not work in evince. I tried both "/path/to/file.pdf" and "file:///path/to/file.pdf". Both variants work in okular though!

Does anybody have an idea?

Bye, flostre


Edit: It works both in Evince and in Okular if you use relative paths. Less than optimal if you ask me, though.


pdflatex version:

pdfTeX using libpoppler 3.141592-1.40.3-2.2 (Web2C 7.5.6)
kpathsea version 3.5.6
Copyright 2007 Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).
Kpathsea is copyright 2007 Karl Berry and Olaf Weber.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the pdfTeX using libpoppler copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the pdfTeX using libpoppler source.
Primary author of pdfTeX using libpoppler: Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).
Kpathsea written by Karl Berry, Olaf Weber, and others.

Compiled with libpng 1.2.37; using libpng 1.2.37
Compiled with zlib 1.2.3.3; using zlib 1.2.3.3
Compiled with libpoppler version 0.12.0

---

