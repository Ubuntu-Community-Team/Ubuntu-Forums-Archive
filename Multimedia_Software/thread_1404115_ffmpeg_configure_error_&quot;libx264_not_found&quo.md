---
title: "ffmpeg configure error &quot;libx264 not found&quot; ?"
date: 2010-02-11
forum: Multimedia Software
---

### Post by rahul23 on 2010-02-11
when I install libx264 through apt-get , the ffmpeg configuration goes smoothly but after uninstalling libx264 , i install it again but by compiling src , i got ffmpeg configuration error as  "libx264 not found" ?

My Operating system: Kubuntu 9.10 karmic kola  64bit

thanks in advance

---

### Post by FakeOutdoorsman on 2010-02-11
Did you follow this guide?
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

---

### Post by rahul23 on 2010-02-12
> **FakeOutdoorsman said:**
> Did you follow this guide?
[URL="http://ubuntuforums.org/showthread.php?t=786095"]
HOWTO: Install and use the latest FFmpeg and x264[/URL]


yes i did , the only difference is i downloaded  the src code directly from ffmpeg site , instead of using svn (for vhook to work).
The amazing thing is svn version compiled without any problem but it do not have vhook support.So still the problem remains

---

### Post by FakeOutdoorsman on 2010-02-12
FFmpeg 0.5 is too old to use a recent compiled x264, and I'm unsure which x264 revision will work for you.  Perhaps **libx264-dev** from the repository will work.  Never tried it myself.

Or, if you're patient, a patch is coming soon that will allow recent x264 to work in the FFmpeg 0.5 branch.  I'll make a post when it is released.

---

### Post by VertexPusher on 2010-02-12
Alternatively you can use ffmpeg as a decoding filter in front of the CLI version of x264. This will give you access to all x264 options, including those which are not mapped to ffmpeg. Enter "x264 --longhelp" for a full list.
```
ffmpeg -i <input file> -r <fps> -s <width>x<height> \
-f rawvideo -vcodec rawvideo -pix_fmt yuv420p \
-y /dev/stdout | x264 <encoding options> -o <output file> \
--fps <fps> /dev/stdin <width>x<height>
```

---

### Post by rahul23 on 2010-02-12
> **VertexPusher said:**
> Alternatively you can use ffmpeg as a decoding filter in front of the CLI version of x264. This will give you access to all x264 options, including those which are not mapped to ffmpeg. Enter "x264 --longhelp" for a full list.
```
ffmpeg -i <input file> -r <fps> -s <width>x<height> \
-f rawvideo -vcodec rawvideo -pix_fmt yuv420p \
-y /dev/stdout | x264 <encoding options> -o <output file> \
--fps <fps> /dev/stdin <width>x<height>
```

Thats a nice workaround (and complex :;) ) , my primary aim to setupt ffmpeg is to use it with phpvideotoolkit ,

---

### Post by mc4man on 2010-02-12
libx264-67 and it's matching libx264-dev will work fine with the 0.5 release of ffmpeg.
[more here]("http://ubuntuforums.org/showthread.php?p=8644623#post8644623")

---

### Post by rahul23 on 2010-02-12
> **mc4man said:**
> libx264-67 and it's matching libx264-dev will work fine with the 0.5 release of ffmpeg.
[more here]("http://ubuntuforums.org/showthread.php?p=8644623#post8644623")

i installed both of them but the same problem.

---

### Post by mc4man on 2010-02-13
> i installed both of them but the same problem.

Not actuallly sure what you mean but ...
You could wait for the patch FO mentioned or follow what I posted. If you did so I'm 99.9% sure you'd have the 0.5 ffmpeg with vhook and x264 enabled.

You need to remove any prior x264 builds first and if you have any ppa that provides x264 then disable it.

You'd run this first, then install the karmic libx264-67 and karmic libx264-dev (1:0.svn20090621+git364d7d-0ubuntu2), then build the 0.5 ffmpeg source, ect.

```
sudo apt-get remove libx264-dev x264 ffmpeg
```

```
sudo apt-get install libx264-67 libx264-dev
```

---

