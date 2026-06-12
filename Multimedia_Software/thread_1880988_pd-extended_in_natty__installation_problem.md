---
title: "pd-extended in natty : installation problem"
date: 2011-11-14
forum: Multimedia Software
---

### Post by dairysound on 2011-11-14
Hi

I've been trying to install pd-extended on 11.04. I downloaded from [http://autobuild.puredata.info/auto-build/2011-09-01/](http://autobuild.puredata.info/auto-build/2011-09-01/) and installed via the software centre. When I run it in terminal I get this in the terminal:


dan@dan-laptop:~$ pd-extended
priority 6 scheduling enabled.
priority 8 scheduling enabled.
open: /etc/pd/gem.conf: No such file or directory
open: /home/dan/.pd/gem.conf: No such file or directory
open: ./gem.conf: No such file or directory

pd shows this:

WARNING: Font family 'DejaVu Sans Mono' not found, using default (courier)

/usr/lib/pd-extended/startup/vanilla: can't load startup library'!

/usr/lib/pd-extended/startup/extra: can't load startup library'!

GEM: Graphics Environment for Multimedia
GEM: ver: 0.93.SVN rev4516
GEM: compiled: Nov 12 2011
GEM: maintained by IOhannes m zmoelnig
GEM: Authors :	Mark Danks (original version)
GEM:		Chris Clepper
GEM:		Cyrille Henry
GEM:		IOhannes m zmoelnig
GEM: with help by Guenter Geiger, Daniel Heckenberg, James Tittle, Hans-Christoph Steiner, et al.
GEM: found a bug? miss a feature? please report it:
GEM: 	homepage [http://gem.iem.at/](http://gem.iem.at/)
GEM: 	bug-tracker [http://sourceforge.net/projects/pd-gem/](http://sourceforge.net/projects/pd-gem/)
GEM: 	mailing-list [http://lists.puredata.info/listinfo/gem-dev/](http://lists.puredata.info/listinfo/gem-dev/)
GEM: compiled for SIMD architecture: MMX 
GEM: using MMX optimization

-------------

/usr/lib/pd-extended/startup/vanilla and /usr/lib/pd-extended/startup/extra are both present in those locations so I'm assuming that the problem is gem.conf but I'm not sure and I don't know where to go next.

Any help gratefully received!

Thanks

Dan

---

