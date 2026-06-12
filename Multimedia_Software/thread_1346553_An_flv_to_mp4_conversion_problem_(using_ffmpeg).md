---
title: "An flv to mp4 conversion problem (using ffmpeg)"
date: 2009-12-05
forum: Multimedia Software
---

### Post by AussieGuy on 2009-12-05
I'm using ffmpeg to convert a downloaded flv video to mp4.  After some hunting around, I found that

ffmpeg -i file.flv -acodec copy -f mp4 -ar 22050 file.mp4

did the trick, and didn't give those annoying "Unsupported codec for output stream #0.1" (which is the audio stream) errors.

But when I went to play the mp4 file, after transferring to my iPod, I found the sound was missing, yet it played fine on my linux box.

Does anybody know what other tweaking is required to produce an mp4 file recognisable by an iPod?

Thanks,
-A.

---

### Post by Bachstelze on 2009-12-05
You didn't define an -acodec, that's probably why.

---

### Post by andrew.46 on 2009-12-05
Hi AussieGuy,

> **AussieGuy said:**
> 
```
ffmpeg -i file.flv -acodec copy -f mp4 -ar 22050 file.mp4
```


Can you give the full terminal output that accompanies that command along with the command itself?

Andrew

---

### Post by AussieGuy on 2009-12-05
Thanks - what I did in the end was to compile ffmpeg from source, having been informed that aac support is not included by default, following the instructions at:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

It's now working fine!

-A.

---

### Post by andrew.46 on 2009-12-05
Hi AussieGuy,

> **AussieGuy said:**
> Thanks - what I did in the end was to compile ffmpeg from source, having been informed that aac support is not included by default

Good to hear :). It was not a fine moment for Ubuntu when faac was not only removed from FFmpeg under Karmic Koala (for which there are some very real licensing issues) but no real effort was made to enable aac encoding for the average user who would perhaps be disinclined to compile their own. Fortunately FFmpeg is developing a native aac encoder and hopefully this will be reasonably mature by the time Lucid Lynx arrives...

All the best,

Andrew

---

### Post by FakeOutdoorsman on 2009-12-05
> **andrew.46 said:**
> ...but no real effort was made to enable aac encoding for the average user who would perhaps be disinclined to compile their own.

Medibuntu may be filling that niche by offering **libav*-extra-52** thanks to paul.gevers submitting this as a Medibuntu "whishlist":
[url=https://bugs.launchpad.net/medibuntu/+bug/490227]
Bug #490227 in Medibuntu: Wishlist: create ffmpeg with aac/libfaac support for Karmic[/url]

It's been uploaded to the Medibuntu *karmic-staging* repository.  I'm not sure of the process after that though or if/when it will migrate to the regular Medibuntu *karmic* repository.

---

### Post by AussieGuy on 2009-12-05
I have no problems compiling from source, being an old linux user (although new to Ubuntu), but I guess in the spirit of ease of use, it would be nice not to necessarily go along this path.  And I know that not everyody is as gung-ho about compilation as I am.  

Thanks again,
A.

---

### Post by andrew.46 on 2009-12-06
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> Medibuntu may be filling that niche by offering **libav*-extra-52** thanks to paul.gevers submitting this as a Medibuntu "whishlist":
[url=https://bugs.launchpad.net/medibuntu/+bug/490227]
Bug #490227 in Medibuntu: Wishlist: create ffmpeg with aac/libfaac support for Karmic[/url]

Now I feel a little guilty for just whinging about it instead of taking some action :(.

Andrew

---

