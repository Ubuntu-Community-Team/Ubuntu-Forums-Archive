---
title: "Blueray 3D support?"
date: 2012-06-02
forum: Multimedia Software
---

### Post by Garyu on 2012-06-02
I have been trying to search for how well Ubuntu supports Blueray 3D movies, but I can't seem to find anything. I hope this means I'm bad at searching, or that it works so well that no one needs to post anything about fixes or whatever... 

I have the nVidia 3D Vision enabled screen, with spectacular spectacles. Currently have Windoze installed, but every now and then I tend to switch to Ubuntu on my computers until I get annoyed about the lack of features supported and then switch back. So... this time I figured I would ask before I switch, can I still watch my movies?

If it isn't supported, how about running Windoze in a virtual box? Would the VM be able to access hardware so I could still use 3D movies?

EDIT: I continued googling and found that playing 3D Vision is no problem, but apparently playing Blu-ray in linux is a problem? Weird. Some people say you have to rip the BD first, then play the .mkv-file. What's up with that, really?

---

### Post by andrew.46 on 2012-06-02
> **Garyu said:**
> EDIT: I continued googling and found that playing 3D Vision is no problem, but apparently playing Blu-ray in linux is a problem? Weird. Some people say you have to rip the BD first, then play the .mkv-file. What's up with that, really?

Sorry to answer only part of your question :). Playback of bluray under Linux is still in early stages but at the moment it can be done a few different ways. *makemkv* can rip the bluray to your drive as an mkv file for later playback but will also allow the live streaming of the movie which can then be played with either vlc or MPlayer. Also if the copy of vlc or MPlayer has been compiled against libbluray and libaacs, and has access to a suitable keydb.cfg, many blurays can be played directly. All the details here:

BluRay
[https://wiki.archlinux.org/index.php/BluRay](https://wiki.archlinux.org/index.php/BluRay)

Early days yet but it can be done. For the complication you can thank the ill-conceived encryption methods used on these discs which block the legitimate right of Linux bluray owners to play their own bluray discs.

---

