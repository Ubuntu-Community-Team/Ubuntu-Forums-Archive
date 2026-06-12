---
title: "Compiz, gnome-Mplayer and MPlayer PATCHED"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by r4idei on 2007-06-24
Hello everybody, I run ubuntu feisty on a laptop with intel 915 grahpic card.
Compiz has always run quite well on this pc, the only problem was the baaad video playback with Xv driver, with all that blue flashing and missing resizing when scaling or switching (I really didn't want to use the unaccelerated Xshm).
I dont know if it is a common problem (it's present with mi ati equipped pc too), but after months i finally find a patch for this issue written by Dave R. :D [http://lists.freedesktop.org/archives/xorg/2007-March/022343.html](http://lists.freedesktop.org/archives/xorg/2007-March/022343.html)

After applying this patch to mplayer's source everything run smooth, without any artifact and with the full speed and low cpu consumption of Xv driver :)

The only problem now is that im forced to use mplayer (i've always used xine) and i would like to find something that intereacts well with gnome.
I found gnome-mplayer BUT with the patched mplayer it just shows a blue screen (playback works cause i hear audio) while with normal mplayer works normally
Thinking of a bug tried smplayer and even kmplayer, and they all do the same.
With classic gmplayer or with pythonbased frontends (like pymp or pygme) i got a correct playback..

Where is the problem?

Thanks in advance

---

