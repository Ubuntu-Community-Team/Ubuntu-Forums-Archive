---
title: "mediatomb on karmic PPC error on install"
date: 2009-11-25
forum: Multimedia Software
---

### Post by johntoups on 2009-11-25
after a 

```
sudo apt-get install mediatomb
```

I have the following output, and have tried many things to understand, but am stumped:

```
$ sudo /etc/init.d/mediatomb start
 * Starting upnp media server mediatomb
/usr/bin/mediatomb: symbol lookup error: /usr/local/lib/libffmpegthumbnailer.so.3: undefined symbol: av_fifo_alloc
   ...fail!
```

If it helps, the libffmpeg* packages installed are:

```
$ sudo dpkg -l |grep libffmpeg
ii  libffmpegthumbnailer-dev              1.5.4-1build1                      development files for ffmpegthumbnailer
rc  libffmpegthumbnailer2                 1.3.0-1                            the ffmpegthumbnailer library
ii  libffmpegthumbnailer3                 1.5.4-1build1                      the ffmpegthumbnailer library
```


Thanks in advance for any pointers.

---

