---
title: "Latest ffmpeg version question / problem"
date: 2011-05-08
forum: Multimedia Software
---

### Post by Twizzle on 2011-05-08
I am trying to install forked-daapd on my Ubuntu x64 10.10 server box.

Everything runs to plan except for when I run:

 ```
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --enable-flac --enable-musepack
```

and I get an:

```
configure: error: ffmpeg >= 0.5.1 required
```

My ffmpeg version is:

```
ffmpeg version git-N-29513-g97dc86b, Copyright (c) 2000-2011 the FFmpeg developers
  built on Apr 30 2011 07:32:13 with gcc 4.4.5

```

which I thought was a recent version.

Am i right in thinking that as I have not installed a 'normal' version of ffmpeg, my system thinks that it is not 0.5.1 or greater?

If so, what can I do to fix it?

(I used [this]("https://github.com/jasonmc/forked-daapd/blob/master/INSTALL") for the forked-daapd install guide and [this]("http://ubuntuforums.org/showthread.php?t=786095") for the latest ffmpeg install guide)


SOLVED - I managed to remove and reinstall ffmpeg which fixed it and retained the functionality I wanted. Does not really answer the question about why my version did not show as a recent one but it works never the less.

---

