---
title: "FLV files only play when totem is run as root"
date: 2009-12-29
forum: Multimedia Software
---

### Post by chrisamiller on 2009-12-29
When I try to play a .flv file with totem, the program informs me that it can't find the flash demuxer plugin, and a search for the plugin is unsuccessful.

However, if I run totem as root (sudo totem asdf.flv), the file plays perfectly.  

I assume that this is a permissions problem somewhere. Can someone point me in the right direction?

---

### Post by VertexPusher on 2009-12-29
Make sure that all the files in your user home directory are owned by that user, not root.

And stop running applications as root. Don't use sudo as a magic bullet to make stuff work. This is how permissions get messed up in the first place. Once you run an application as root, its configuration files will be owned by root and inaccessible to your normal user account.

WINE should never be run as root either. Unfortunately many people mix up root privileges with Windows administrator privileges and run WINE as root when installing Windows applications. This is wrong.

---

### Post by chrisamiller on 2009-12-29
Trust me, I'm aware of the implications of running things as root.  I stumbled across another forum thread where someone reported a similar problem and gave it a last-ditch try.

find . -user root 

doesn't return anything unexpected - just some CPAN stuff

---

### Post by chrisamiller on 2009-12-29
I also did searches for totem and gstreamer files system-wide and don't see anything obviously wrong with their permissions either.

I've already reinstalled most of the gstreamer plugins, in the hopes that the problem could be resolved that way, but have had no luck.  

Any other suggestions?

---

