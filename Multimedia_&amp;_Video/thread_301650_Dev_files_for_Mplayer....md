---
title: "Dev files for Mplayer..."
date: 2006-11-17
forum: Multimedia &amp; Video
---

### Post by ardvark71 on 2006-11-17
Hi all...

I'm trying to install the latest release of Mplayer and to set it up with the GUI option enabled, it's telling me I need the GTK2 development files. I didn't find these in Synaptic. Are they under another name or is there a specific place to get them?

Thanks! :KS

---

### Post by ardvark71 on 2006-11-17
Anyone? :confused:

---

### Post by codejunkie on 2006-11-17
enable the universe and multiverse repos first if you don't know how you can find instructions [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories"), then run ```
sudo apt-get update
``` then ```
sudo apt-get build-dep mplayer
``` in a terminal should do it unless the latest version of mplayer requires an unknown package in that case it will list it during the compiling and you'll have to download that and install it first.

---

### Post by ardvark71 on 2006-11-18
Thanks, codejunkie...

I'll give that a shot. :cool:

---

### Post by ardvark71 on 2006-11-18
Hi again..

I found it through Synaptic....for some reason it wouldn't obtain it through apt-get even though the repositories were updated. Thanks!

:KS

---

