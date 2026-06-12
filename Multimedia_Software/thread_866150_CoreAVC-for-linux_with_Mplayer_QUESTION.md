---
title: "CoreAVC-for-linux with Mplayer QUESTION"
date: 2008-07-21
forum: Multimedia Software
---

### Post by Duranxl on 2008-07-21
Hi all
I've successfully compiled the SVN build of mplayer with CoreAVC.
But I can only start the mplayer via terminal:
mplayer -vc coreserve <filename>

But this way i do no have the mplayer-control thingy and i rightclick on the video.
Is there anyway to get the control thingy back?

Thanks

---

### Post by Jean__ on 2008-07-22
gmplayer

---

### Post by Duranxl on 2008-07-22
> **Jean__ said:**
> gmplayer

That boots the normal mplayer i have installed...and i cannot load the CoreAVC build.
> Forced video codec: coreserve
Requested video codec family [coreserve] (vfm=dshowserver) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x31637661.
I can only use the compiled SVN build with mplayer

---

### Post by shirilover on 2008-07-22
Did you use the -enable-gui flag when you compiled mplayer?

---

### Post by Duranxl on 2008-07-23
> **shirilover said:**
> Did you use the -enable-gui flag when you compiled mplayer?

No i didn't.
The guide I followed ([http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)) never stated anything about this..

edit: do you need to -enable-gui with all SVN builds?

---

### Post by shirilover on 2008-07-24
Only if you want a graphical frontend.
Another option is to use SMplayer as the frontend to mplayer.

---

