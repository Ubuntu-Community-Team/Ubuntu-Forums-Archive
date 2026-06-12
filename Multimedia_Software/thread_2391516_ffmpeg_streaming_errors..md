---
title: "ffmpeg streaming errors."
date: 2018-05-10
forum: Multimedia Software
---

### Post by Furycd001 on 2018-05-10
HI guys.

I regularly use [mpv]("https://mpv.io/") with [ffmpeg]("https://ffmpeg.org/") to watch livestreams & other online videos. Everything works fine but the relating terminal window endlessly scrolls with the following two error messages below. Is there any way I can stop these two errors from constantly showing ??


[B][ffmpeg] tls: The TLS connection was non-properly terminated.

[ffmpeg] https: No trailing CRLF found in HTTP header.[/B]

---

### Post by tinylagarto on 2018-05-10
You can create an mpv config file where you can specify:

*--quiet*; less output or
*--really quiet*; even less output and messages on the console

etc, read the mpv man page.

You can start mpv with those options from the command line and try it. If you like it create a config file in your home folder: 

```
~/.config/mpv/
```

---

### Post by Yellow Pasque on 2018-05-10
[https://github.com/mpv-player/mpv/issues/4425](https://github.com/mpv-player/mpv/issues/4425)

---

### Post by Furycd001 on 2018-05-11
> **tinylagarto said:**
> You can create an mpv config file where you can specify:

*--quiet*; less output or
*--really quiet*; even less output and messages on the console

etc, read the mpv man page.

You can start mpv with those options from the command line and try it. If you like it create a config file in your home folder: 

```
~/.config/mpv/
```

Thanks for the heads up ^^ May create my own config file because I didn't know you could do that....

---

### Post by Furycd001 on 2018-05-11
> **Temüjin said:**
> [https://github.com/mpv-player/mpv/issues/4425](https://github.com/mpv-player/mpv/issues/4425)

Thanks for the link. This appears to solve the problem so I'm going to give it a try....

---

