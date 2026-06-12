---
title: "PPStream with totem-pps + chrome"
date: 2010-09-01
forum: Multimedia Software
---

### Post by yookoala on 2010-09-01
Hello,

I'm using Ubuntu 10.04 with Chromium (5.0.375) as my main browser. I've installed totem-pps as described in [the instruction I found](http://blog.diyersitzone.net/2010/05/18/ppstream-on-ubuntu-10-04/). There are number of problems:

[list=1]
[*]I cannot see the category list of video (on the sidebar)

[*]When using Chrome to open pps:// based uri in [PPS movie index site](http://kan.pps.tv/movie_index.html), it failed without an error message.

For example, if I open a link like this:

[pps://ouu2wygqea.pps/%E5%8D%81%E4%BA%8C%E7%BD%97%E6%B1%89.rmvb?maingen=%E7%83%AD%E9%97%A8%E7%94%B5%E5%BD%B1&subgen=](pps://ouu2wygqea.pps/%E5%8D%81%E4%BA%8C%E7%BD%97%E6%B1%89.rmvb?maingen=%E7%83%AD%E9%97%A8%E7%94%B5%E5%BD%B1&subgen=)

Chrome uses xdg-open to open that uri, which try to run command like this:

```
xdg-open pps://ouu2wygqea.pps/%E5%8D%81%E4%BA%8C%E7%BD%97%E6%B1%89.rmvb?maingen=%E7%83%AD%E9%97%A8%E7%94%B5%E5%BD%B1
```


I tried to run that command directly. And it reports:
```
Error showing url: The specified location is not supported
```

[/list]


What is my problem? Any suggestion?

---

### Post by Dempf on 2010-09-27
I have the same problem. Check this thread:

[http://ubuntuforums.org/showthread.php?t=1332919&page=2#20](http://ubuntuforums.org/showthread.php?t=1332919&page=2#20)

Looks like PPStream may be blocking 3rd party applications. Maybe it'd be a good idea to ask them about it...

---

### Post by s0563764 on 2010-10-20
There's now an error too, with totem-pps missing when i try to install it

---

### Post by Spetsnaz84 on 2011-10-12
Anyone have any ideas ?

---

