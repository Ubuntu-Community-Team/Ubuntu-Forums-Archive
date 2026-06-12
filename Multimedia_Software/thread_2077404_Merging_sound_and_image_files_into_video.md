---
title: "Merging sound and image files into video"
date: 2012-10-28
forum: Multimedia Software
---

### Post by redaxe90 on 2012-10-28
Yeah, it's me again with a different kind of problem :D

I have the need to create a video file by putting together a music file I recorded and put image files on top of it as a kind of a slide show. I've already tried using WinFF and OpenShot and neither will work, as the file types I have to work with are wav and jpg.

OpenShot only wants to work with PNG files, so I'm a bit stumped. Any ideas??

I know I could make this with Windows Movie Maker, but I completely  abhor using Windows, which is why I come to you great people here.

---

### Post by ajgreeny on 2012-10-28
Try **imagination** from the repos.  It looks as if it works on all image file types, though I admit I've so far only used it for jpg files from my camera.

---

### Post by redaxe90 on 2012-10-28
Thanks, I'll give that a go

---

### Post by VanillaMozilla on 2012-10-29
No, it's exceedingly difficult to get a video editor that works for you so keep the one that works and that you are familiar with.

Just convert the .jpg files to .pngs.  There are lots of ways to do it.  The way I would do it is to use ImageJ.  That's not necessarily the simplest or most efficient way, but it's what I happen to have on *my* computer, and it works.  Just open the .jpg and save as .png.

---

### Post by FakeOutdoorsman on 2012-10-29
> **VanillaMozilla said:**
> Just convert the .jpg files to .pngs.  There are lots of ways to do it.  The way I would do it is to use ImageJ.  That's not necessarily the simplest or most efficient way, but it's what I happen to have on *my* computer, and it works.  Just open the .jpg and save as .png.
One at a time? Sounds like too much work for me. Remember, laziness can be a virtue (or easily confused for a desire for efficiency):

Using graphicsmagick:
```
sudo apt-get install graphicsmagick
cd my-jpg-images
gm mogrify -format png *.jpg
```

Using imagemagick:
```
sudo apt-get install imagemagick
cd my-jpg-images
mogrify -format png *.jpg
```

Graphicsmagick is usually faster then imagemagick in my experience, but they're both good.

I'm surprised nobody mentioned **Kdenlive** as an editor.

---

### Post by shantiq on 2012-10-29
and one more vote for **kdenlive** :KS   drag pictures [any format] in  and stretch to the duration you seek and add your music and export in pristine mkv.   haaaa

---

### Post by Pinoy Tux on 2012-10-30
> **redaxe90 said:**
> I've already tried using ... OpenShot and neither will work, as the file types I have to work with are wav and jpg.

OpenShot only wants to work with PNG files...
Wait, what? OpenShot only work with PNG files and won't allow you to import JPGs?  Sorry but that's just pure nonsense.  OpenShot imports JPG files just fine.  I don't think it's an OpenShot issue at all.

---

### Post by VanillaMozilla on 2012-10-30
Indeed it is nonsense.  I just tried it.  There's no problem whatsoever.

Maybe there's a library missing.  Missing non-free codecs?

---

