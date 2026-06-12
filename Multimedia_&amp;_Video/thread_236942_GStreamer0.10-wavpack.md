---
title: "GStreamer0.10-wavpack?"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by joris1977 on 2006-08-15
GStreamer0.10-wavpack

Does anyone know if this package is available for dapper? And if so where do i get it, because it is not in my packages-list. It seems this is necessary to play wma files in quod libet and that would make this player almost perfect!

thanks in advance

Joris

---

### Post by Jagot on 2006-08-16
The package is not available in the Ubuntu repositories.  Doesn't w32codecs do the job?

---

### Post by Jagot on 2006-08-16
Oops - double post.

---

### Post by joris1977 on 2006-08-16
Thanks for replying. But no I already have w32codecs installed and wavpack as well, but that doesn't seem to help. These links suggests that it should be possible to make quod libet play wma, but it seems to need a gstreamer plugin  see [http://www.wavpack.com/links.html](http://www.wavpack.com/links.html)
 and
[http://www.sacredchao.net/quodlibet/wiki/Guide/Requirements](http://www.sacredchao.net/quodlibet/wiki/Guide/Requirements)  

and on this side i found out there exists a Gstreamer-wavpack from some linux distributions, but i don't know if i can install this one.

[http://rpm.pbone.net/index.php3/stat/21/year/2006/month/06/day/17](http://rpm.pbone.net/index.php3/stat/21/year/2006/month/06/day/17)

---

### Post by hugmenot on 2006-08-16
Hold your horses!

```
dpkg -L gstreamer0.10-plugins-bad
[snip]
/usr/lib/gstreamer-0.10/libgstwavpack.so
[etc.]
```

that&#8217;s what you want.

---

### Post by tv0571 on 2007-07-17
Sorry for the noob question but could you elaborate?  I understand I am to apt-get the gstreamer0.10-plugins-bad, but what then?  I see after dpkg that i have libgstwavpack.so, but I don't know what to do with it.  I'd like to get WMA's running with quod libet.

The sacredecho website lists this obscure reference.  [http://www.sacredchao.net/quodlibet/browser/trunk/quodlibet/formats/wma.py?rev=4001](http://www.sacredchao.net/quodlibet/browser/trunk/quodlibet/formats/wma.py?rev=4001)
I tried building that .py in the directory they indicate, but I couldn't tell that it did anything.

Thanks in advance for help!

---

### Post by hugmenot on 2007-07-18
WMA is Windows Media Audio and not WavPack! WavPack is .wv not .wma.
You&#8217;re after the wrong format. I remember that there is now WMA support in QL. Look for the thread about getting the latest QL and download my packages at the very end of the thread. They are for Feisty I think.

---

