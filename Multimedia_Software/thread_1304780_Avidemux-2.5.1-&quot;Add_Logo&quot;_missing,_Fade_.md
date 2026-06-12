---
title: "Avidemux-2.5.1-&quot;Add Logo&quot; missing, Fade out broken."
date: 2009-10-29
forum: Multimedia Software
---

### Post by emarkay on 2009-10-29
It was here:[http://avidemux.org/admWiki/index.ph...eo_filter_Logo]("http://avidemux.org/admWiki/index.php?title=Video_filter_Logo")

And under "Video >  Filters" where  "Add Logo" feature was, now shows an entry "Partial" which crashes  program with:

Segfault
 at line 0, file ??/usr/lib/libADM_core.so(ADM_backTrack+0x6d) [0x1f292d]
/usr/lib/libADM_core.so(_Z20sig_segfault_handleri+0x46) [0x1f2db6]
[0x22a400]
/usr/lib/libADM_coreImage.so(_ZN10CONFcouple10lookupNameEPK  c+0x1a) [0x213d9a]
/usr/lib/libADM_coreImage.so(_ZN10CONFcouple9getCoupleEPKcP  j+0x2c) [0x2142bc]
avidemux2_gtk(_ZN15ADMVideoPartialC1EP22AVDMGeneri  cVideoStreamP10CONFcouple+0x5:cool: [0x80c8708]
avidemux2_gtk(_Z14partial_createP22AVDMGenericVide  oStreamP10CONFcouple+0x2b) [0x80c881b]
avidemux2_gtk [0x81add5b]
/usr/lib/libgtk-x11-2.0.so.0 [0x11ec72f]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x646d072]
/usr/lib/libgobject-2.0.so.0 [0x64827a8]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0x6483b2d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x6483fb6]
/usr/lib/libgtk-x11-2.0.so.0(gtk_tree_view_row_activated+0x9:cool: [0x12e6fc8]
/usr/lib/libgtk-x11-2.0.so.0 [0x12f991a]
/usr/lib/libgtk-x11-2.0.so.0 [0x11ee474]
/usr/lib/libgobject-2.0.so.0 [0x646b6f9]
/usr/lib/libgobject-2.

This all worked fine in Jaunty!

Bug filed:
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/461350]("https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/461350")

Fix apparently in SVN, I am unsure as to my abilities in ensuring uncorrupted compilation, asked for assistance here:
[http://avidemux.org/admForum/viewtopic.php?id=6807]("http://avidemux.org/admForum/profile.php?id=3449")

Reposting original (Closed) Karmic thread in case any additional activity:
[http://ubuntuforums.org/showthread.php?t=1297256](http://ubuntuforums.org/showthread.php?t=1297256)

---

### Post by emarkay on 2009-11-08
No one else uses Avidemux?

---

### Post by emarkay on 2009-11-23
I find this hard to believe that us Open Source folks are not editing videos...

---

### Post by splogad on 2009-12-14
Hi! I have the same problem, 2.5.1 does not contain logo filter and some other filters chrash...
I tried to install the svn version but the problem remains.
2.5.1 it's not yet stable.

Maybe installing the previous version it should work.

---

### Post by skwhirl on 2009-12-15
I'm glad that I am not the only one who has met with frustration over this.

I've recently switched a second PC from Windows to Ubuntu, and was expecting AVIDemux to be a fitting replacement to VirtualDub. VirtualDub's DirectShow reliance makes it about as worthless as a milk bucket under a bull in WinE. One of the main filters that I use is the Logo filter. 

Supposedly the logo filter as well as a couple of others been commented out of the more recent builds of AVIDemux, and they just aren't compiled. 

Two options: Find V 2.4.4, or grab the source and see if you can uncomment it and get it to compile with them (my next step)

The stable version (with Logo filter) can be found at: [http://voxel.dl.sourceforge.net/project/avidemux/avidemux/2.4.4/avidemux_2.4.4.tar.gz](http://voxel.dl.sourceforge.net/project/avidemux/avidemux/2.4.4/avidemux_2.4.4.tar.gz)

We really should encourage the project maintainers to fix this ASAP.

The repositories should contain both the stable (2.4.4) as well as the Dev versions. Unfortunately the broken version is the only one available (!)

---

### Post by abadr on 2010-01-03
I found the 64bit 2.4.4 version here [http://old.getdeb.net/search.php?search_distro_id=12&keywords=avidemux](http://old.getdeb.net/search.php?search_distro_id=12&keywords=avidemux) 
I removed the repo version and tried to install this but I got a dependency error "Error: Dependency is not satisfiable: libx264-59 (>=1:0.svn20080408)" even though I have libx264-67 installed... This sucks......

---

### Post by emarkay on 2010-05-19
Also not working in in 2.5.2

---

### Post by emarkay on 2010-08-28
Testing version 2.6 provides the feature again, but that version is not working well otherwise.

---

