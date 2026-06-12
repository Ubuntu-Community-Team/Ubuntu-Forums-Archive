---
title: "Playing DVDs using VLC"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by tsairox on 2007-11-05
Hi all,

I have a fresh install of Ubuntu 7.10 amd64I am trying to  play some dvds using VLC. I get this: 



si@si-desktop:~/Desktop$ vlc TheDevilStomps
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: DEVIL_Stomps_PS
libdvdnav: DVD Serial Number: 351D69C4
libdvdnav: DVD Title (Alternative): DEVIL_Stomps_PS
libdvdnav: Unable to find map file '/home/si/.dvdnav/DEVIL_Stomps_PS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed - CRASHING!!!
vlc: vm.c:198: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)
si@si-desktop:~/Desktop$

How do I get beyond this encryption issue?

Thanks anyone,

tsairox

---

### Post by undadecor on 2007-11-05
Try using Synaptic and installing "libdvdcss".  That should allow you to get past the encryption that is put on DVDs.

---

