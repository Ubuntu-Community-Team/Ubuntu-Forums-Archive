---
title: "fix for google earth ATI radeon users with driver 8.40"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by sdowney717 on 2007-08-23
[http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/689714/page/vc/vc/1](http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/689714/page/vc/vc/1)

download that file, rename it and put it into google-earth folder. It runs a little slow but it will run.

It is I suppose an ATI driver issue.

---

### Post by dougfractal on 2007-08-23
> **sdowney717 said:**
> [http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/689714/page/vc/vc/1](http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/689714/page/vc/vc/1)

download that file, rename it and put it into google-earth folder. It runs a little slow but it will run.

It is I suppose an ATI driver issue.

NO.


[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)
You already have the file, you just need to add the symlink.
> sudo mkdir -p /usr/X11R6/lib/modules/dri 
sudo ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri/fglrx_dri.so

---

### Post by sdowney717 on 2007-08-24
NO!, if you follow his directions, this is what you will get when running googleearth.


scott@scott-desktop:~$ googleearth
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[etc.............................

sudo unlink  /usr/lib/dri/fglrx_dri.so

must unlink it to make google earth run again. just rm (delete) the symbolic link is not going to work.!

---

### Post by dougfractal on 2007-08-28
does using have LD_PRELOAD any effect?
LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 googleearth

---

