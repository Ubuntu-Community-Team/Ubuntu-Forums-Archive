---
title: "Strange Error While Installing Banshee"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by DWRZ on 2007-03-18
I am trying to follow this guide [http://doc.gwos.org/index.php/Banshee_and_plugins](http://doc.gwos.org/index.php/Banshee_and_plugins) to install Banshee and eventually most plugins.

At step #4,* sudo apt-get build-dep banshee* I get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/xgl.compiz.info_dists_dapper_main_source_Sources - open (2 No such file or directory)

I have no idea what this is... how do I fix this?

---

### Post by DWRZ on 2007-03-18
Ok, I removed the entries for xgl.compiz.info from my sources.list, then ran "apt-get update". Now, when I try to "apt-get build-dep banshee", I get this following error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for banshee

Any ideas?

---

### Post by pippy on 2007-04-13
I get the same error, i heard from some forum somewhere it had something to do with ntfs driver or something...

i would really like to install the latest version, for some reason i get a clicking sound in one of my headphones when listing to music (i listen to a lot of music)

its not my head phones or drivers, other music players play perfectly

I'll try and find a stable .deb package

---

