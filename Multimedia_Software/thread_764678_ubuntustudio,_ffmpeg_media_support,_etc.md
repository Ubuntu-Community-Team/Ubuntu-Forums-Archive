---
title: "ubuntustudio, ffmpeg media support, etc"
date: 2008-04-24
forum: Multimedia Software
---

### Post by barna on 2008-04-24
Hi,
I would like to have a clearer view concerning multimedia with ubuntu. I have recently heared about ubuntustudio, a "A multimedia creation flavor of Ubuntu". Lacking time, I only made a superficial search, what it really is, but found no detailed description. Is it just a collection of packages aiming multimedia production, on top of the standard ubuntu base? Like kubuntu, which also has a separate install CD, but which you can also install by installing the kubuntu-desktop package, which brings in then all kde-related packages? So can I install ubuntu studio on top of, say,kubuntu, and have everything I had before, + the predefined set of multimedia software? My main profile is software development and simulations, etc, so I wouldn't not like to lose the standard environment, but in my freetime I play sometimes with multimedia.

Another question is about ffmpeg: some time ago I had a video file, which I wanted to convert using ffmpeg, but the support of this format was not compiled into that version of ffmpeg, which was available in the ubuntu repository. So I had to download the source, reconfigure, recompile, and voila. However, this is cumbersome. SuSE has for example an extra repository, packman, where alternative versions of these multimedia software are available, with support for much more formats compiled in. Is something similar available in ubuntu? Or the only choice is to recompile everything from source, if I want more than the 'officially decided' features?

Thanks, Daniel

---

### Post by ShodanjoDM on 2008-04-24
> **barna said:**
> Is it just a collection of packages aiming multimedia production, on top of the standard ubuntu base? Like kubuntu, which also has a separate install CD, but which you can also install by installing the kubuntu-desktop package, which brings in then all kde-related packages? So can I install ubuntu studio on top of, say,kubuntu, and have everything I had before, + the predefined set of multimedia software? 

Yes, you can install ubuntustudio directly from DVD (it doesnt fit inside a CD) or just install additional packages from your current ubuntu installation.

For example, for the ubuntustudio "basic" desktop:

```
sudo aptitude install ubuntustudio-desktop
```

or just search in the synaptic for a complete list

> Another question is about ffmpeg: some time ago I had a video file, which I wanted to convert using ffmpeg, but the support of this format was not compiled into that version of ffmpeg, which was available in the ubuntu repository. So I had to download the source, reconfigure, recompile, and voila. However, this is cumbersome. SuSE has for example an extra repository, packman, where alternative versions of these multimedia software are available, with support for much more formats compiled in. Is something similar available in ubuntu? Or the only choice is to recompile everything from source, if I want more than the 'officially decided' features?


Maybe this will help: [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by barna on 2008-04-24
Great, thanks for drawing my attention to this repository!

---

### Post by ShodanjoDM on 2008-04-24
You're welcome :)

I've been using ubuntu studio since 7.04. I like the option to install a "reduced" desktop compared to standard ubuntu install, and build my system up from there.

---

