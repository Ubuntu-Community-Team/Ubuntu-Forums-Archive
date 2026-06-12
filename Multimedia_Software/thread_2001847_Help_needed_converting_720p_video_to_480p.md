---
title: "Help needed converting 720p video to 480p"
date: 2012-06-11
forum: Multimedia Software
---

### Post by tomdkat on 2012-06-11
So, I used Imagination to create a HD 720p slide show.  I saved the slideshow as a VOB file so I could retain the 720p resolution.

So, now I've got this 720p VOB file with MPEG-2 encoded video that I can't seem to downconvert to 480p.  Neither Avidemux nor Handbrake will allow me to do the conversion.

Any ideas on how I could do this?

Thanks!

Peace...

---

### Post by Georgescu1 on 2012-06-11
you could try kdenlive

---

### Post by evilsoup on 2012-06-11
The ffmpeg/avconv '-s' flag allows you to scale the frame size. From the terminal:

avconv -i input.vob -s hd480 output.vob

should do it. This will scale the video to 852x480. If you want other sizes, you can use the format wxh (e.g. 852x480); or you can find additional abbreviations in the avconv man page. Make sure you use the same aspect ratio, or you will end up with distorted images.

If you want a GUI, you can try out WINFF, though I've never used it so I don't know if it has these options

---

### Post by SeijiSensei on 2012-06-11
[Mencoder]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-rescale.html") with the "-vf scale" option will do this.

MPEG2 is quite inefficient by modern standards.  MPEG4 is a much better choice in terms of the tradeoff between quality and filesize.

---

### Post by tomdkat on 2012-06-12
> **evilsoup said:**
> The ffmpeg/avconv '-s' flag allows you to scale the frame size. From the terminal:

avconv -i input.vob -s hd480 output.vob

should do it. This will scale the video to 852x480. If you want other sizes, you can use the format wxh (e.g. 852x480); or you can find additional abbreviations in the avconv man page. Make sure you use the same aspect ratio, or you will end up with distorted images.

If you want a GUI, you can try out WINFF, though I've never used it so I don't know if it has these optionsThanks for the info. I installed WINFF today, before I read your post, but I haven't used it yet.  I was looking for a graphical option but your command line above is simple enough that I could use that as well.

Thanks!

Peace...

---

### Post by tomdkat on 2012-06-12
> **SeijiSensei said:**
> [Mencoder]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-rescale.html") with the "-vf scale" option will do this.

MPEG2 is quite inefficient by modern standards.  MPEG4 is a much better choice in terms of the tradeoff between quality and filesize.Thanks for the info.  Fortunately, MPEG-2 vs MPEG-4 issues don't matter in this case. I actually use MPEG-4 for most of my video work these days.  :)

Thanks!

Peace...

---

### Post by FakeOutdoorsman on 2012-06-13
> **SeijiSensei said:**
> [Mencoder]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-rescale.html") with the "-vf scale" option will do this.

I also recommend "-vf scale" and ffmpeg also uses it:
```
ffmpeg -i input -vf scale=-1:480 -vcodec mpeg4 -qscale 3 output.mp4
```
The -1 tells ffmpeg to use an appropriate width that preserves the aspect ratio, which in your case would probably be 853.

---

### Post by tomdkat on 2012-06-13
> **FakeOutdoorsman said:**
> I also recommend "-vf scale" and ffmpeg also uses it:
```
ffmpeg -i input -vf scale=-1:480 -vcodec mpeg4 -qscale 3 output.mp4
```
The -1 tells ffmpeg to use an appropriate width that preserves the aspect ratio, which in your case would probably be 853.
Excellent!  Thanks!  :guitar:

Peace...

---

