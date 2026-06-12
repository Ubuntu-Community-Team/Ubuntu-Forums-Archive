---
title: "Screen tearing when playing xvids"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by thedon_1 on 2008-01-20
When i play avi's, primarily xvids, i experience tearing of the picture.

I have tried installing totem xine, but it didn't help.

I have tried using MPlayer and VLC and i get the same results.

I have an Nvidia card.

Any ideas?

---

### Post by nibbo on 2008-02-06
I have the same problem and also using a nvidia card... Any suggestions?

---

### Post by OisinT on 2008-02-06
I also have the same problem... I have tried all different deinterlacing modes on VLC and asked the question here also.  No answer yet.
Also have an nvidia card and looks like I'm using vesa also.. just dont know how to turn it off if it is causing the problem.

```

oisint@OisinT1:~$ cat /etc/X11/xorg.conf | grep vesa
# values from the debconf database and some overrides to use vesa mode.
    BoardName      "vesa"
    BoardName      "vesa"

```

---

