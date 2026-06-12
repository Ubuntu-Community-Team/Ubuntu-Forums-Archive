---
title: "Linux Embedding Album Art"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by mikesena on 2007-07-31
Hi,

Apart from EasyTAG, are there any programs that allow the editing / adding of album art to MP3s in Linux?
If EasyTAG is the only way, using a program like [this one](http://directory.fsf.org/albumart.html), is there an easy way to, for instance, download all album art, save as a similar filename as the MP3 file and then add them all?

Thanks,
Michael

---

### Post by smbm on 2007-08-13
I would also very much like a batch album art downloader. Anyone got any ideas?

---

### Post by kp-salsa on 2007-08-13
I'd also love to be able to do this - and also embed large-scale album art (i.e. 500x500px rather than scratty old 200x200 or smaller).

WMP allows you to do this easily, and embed the images into the ID3 tags, but I've yet to find a player on Ubuntu that sees this info (Amarok, for example, doesn't even seem to read the ID3 tags at all).

---

### Post by joshzam on 2007-09-04
My favorite app for embedding images in mp3 tags (or adding folder.jpg files), *Album Cover Art Downloader*, is available for Linux!

So, for those interested, you can either [download the tarball]("http://ftp.roedu.net/mirrors/gentoo.org/distfiles/") (search for *albumart-1.6.0.tar.gz*) and and compile it yourself, or you can alternately [pick up the DEB]("http://www.unrealvoodoo.org/hiteck/projects/albumart/") - but If you use Ubuntu 7.04, make sure to add the following magic comment:
[COLOR="Blue"]#coding:utf-8[/COLOR]
in the first line of this file:
[COLOR="Blue"]/usr/lib/albumart/albumart_images.py[/COLOR]
in order for Python to interprete the encoding of the file properly, otherwise the file is wrongly interpreted as an ASCII file and a syntax error is thrown when the application launches.

---

### Post by chrome307 on 2007-09-04
Hi there

I was interested in the application and followed the steps outlined but have encountered a problem with being able to save the new file - can you tell what I should do in this instance?

Thanks :)

[IMG]http://i8.tinypic.com/4xlg4lw.jpg[/IMG]

[IMG]http://i7.tinypic.com/4mjy1sh.jpg[/IMG]

---

### Post by chrome307 on 2007-09-05
Open up TERMINAL and then type

```


gksudo gedit /usr/lib/albumart/albumart_images.py


```

Once the file is open then -** Add the comments in the 1st line**

```


#coding:utf-8


```

Then SAVE

---

### Post by joshzam on 2007-09-05
I'm glad to see you found the answer to your problem. Correct me if I'm wrong someone, but I'm pretty sure "sudo" is what you're looking for if editing via the terminal. "gksudo" is when you are in the GUI and need root access.

Knowing how to edit files via the terminal with super user permissions is a valuable skill. Use it wisely :cool:

---

### Post by xjgnsdof on 2008-01-31
I installed Album Art through the deb package, but I can't seem to get the album covers to embed in gtkpod. I even inserted that comment line in the file as root. What's wrong?

---

