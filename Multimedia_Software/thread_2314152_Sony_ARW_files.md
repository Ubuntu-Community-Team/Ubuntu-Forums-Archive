---
title: "Sony ARW files"
date: 2016-02-18
forum: Multimedia Software
---

### Post by darkweasel on 2016-02-18
Hi!

I've now been looking on Google for answers to this for quite a bit of time and couldn't find an answer. I'm on Xubuntu 15.10 and I'm looking for a way to make any decent image viewer – whether Geeqie, EOM, EOG, Ristretto, gThumb, anything – be able to display Sony's raw image format (extension ARW). It has to support zooming, and going to the previous/next file, and shouldn't be slow as hell. The ones I mentioned can all read the other filetypes I need – JPEG and Canon CR2.

I don't need an editor or converter, I have darktable  for that (RawTherapee also works but I'm used to darktable), but I'd like to just look at the images as they are without having to use darktable.

The only ones that do work are:
- digiKam, but I don't want or need a completely overkill photo management software
- Shotwell Viewer, which fails the "slow as hell" requirement from above, and doesn't have an "open with" option or anything for me to easily open darktable with when I need it
- showFoto, which can't go to the previous/next file
- the "ImageMagick (Q16)" option, which is impractical for obvious reasons

The weird thing is this: both the ufraw and the dcraw command work just fine, they seem to be able to read the files! And also, on Fedora I had none of these problems – both Geeqie and Gwenview (the latter of which doesn't seem to work properly at all on Xfce) did everything I needed (even though they didn't recognize the full resolution of ARW files, they seem to have read only the embedded JPEG, but that was good enough for me). I have the feeling I don't have some library installed, but I cannot figure out what to do.

Can anyone help me?

---

### Post by Linuxisfast on 2016-02-20
Try XnView from Dhor PPA @ [https://launchpad.net/~dhor/+archive/ubuntu/myway](https://launchpad.net/~dhor/+archive/ubuntu/myway)

---

### Post by darkweasel on 2016-02-21
Thanks. XnView does kind of work, but I would very strongly prefer a FOSS solution.

---

