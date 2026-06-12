---
title: "FFMPEG issue ..."
date: 2008-05-26
forum: Multimedia Software
---

### Post by dbee on 2008-05-26
I've uninstalled FFMpeg and added the ubuntu media repos. Then I've installed FFMeg from there. Problem is though, i still can't convert mp4 to avi ...

```

ffmpeg -i vid.mp4 -f avi file.avi
....
[mpeg4 @ 0xb7cfc3f0]removing common factors from framerate
Unsupported codec (id=86018) for input stream #0.0

```

Does anyone know what's wrong ?

THanks

---

### Post by kostkon on 2008-06-02
You have to install the version of *FFmpeg* that is offered by the [*Medibuntu* repository]("http://medibuntu.org/"). This version has the support for restricted formats enabled.

---

