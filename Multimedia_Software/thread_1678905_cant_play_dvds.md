---
title: "cant play dvds"
date: 2011-01-31
forum: Multimedia Software
---

### Post by Makoto_99 on 2011-01-31
Hi,
     I'm pretty new to ubuntu.  I have been trying to play dvds with no luck.  I've tried totem and vlc and still cant play dvds.  Any help would be appreciated.  

-Mike

---

### Post by cascade9 on 2011-01-31
You'll need to install libdvdcss- 

> **Installing libdvdcss**

 Legal Warning: Check with your local laws to make sure usage of libdvdcss2 would be legal in your area. 
 
**Ubuntu 9.04, 9.10, 10.04 (i386, amd64) and 10.10**

 
[LIST]
[*]Install the **libdvdread4** package (**no need to add third party repositories**) via Synaptic or command line: 
[/LIST]

 sudo apt-get install libdvdread4
[LIST]
[*]Then open a terminal window and execute: 
[/LIST]

 sudo /usr/share/doc/libdvdread4/install-css.shRebooting may be necessary. 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

