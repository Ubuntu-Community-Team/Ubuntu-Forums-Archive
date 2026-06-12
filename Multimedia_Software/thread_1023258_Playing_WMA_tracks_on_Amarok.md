---
title: "Playing WMA tracks on Amarok"
date: 2008-12-27
forum: Multimedia Software
---

### Post by Roger Allott on 2008-12-27
I like Amarok. However, it has only gotten hold of the mp3 tracks in my music library, and ignored the many more wma files.

I see from the [Ubuntu Help/Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") page that the problem is probably to do with not have the appropriate codecs installed.

It says that I need to have ubuntu-restricted-extras installed to play wma files. But I've got that installed already!

However, I've just noticed that Amarok is a KDE application. So does that mean that I need to install kubuntu-restricted-extras as well as the ubuntu variant? Won't they clash/conflict?

---

### Post by mc4man on 2008-12-27
Install libxine1-ffmpeg, that will take care of wma in amarok except if they're wma lossless. For that you also need w32codecs, available from link below

```
sudo apt-get install libxine1-ffmpeg
```

For hardy (8.04
[http://packages.medibuntu.org/hardy/w32codecs.html](http://packages.medibuntu.org/hardy/w32codecs.html)

For intrepid (8.10
[http://packages.medibuntu.org/intrepid/w32codecs.html](http://packages.medibuntu.org/intrepid/w32codecs.html)

---

### Post by Roger Allott on 2008-12-27
> **mc4man said:**
> Install libxine1-ffmpeg, that will take care of wma in amarok except if they're wma lossless. For that you also need w32codecs, available from link below

```
sudo apt-get install libxine1-ffmpeg
```

For intrepid (8.10
[http://packages.medibuntu.org/intrepid/w32codecs.html](http://packages.medibuntu.org/intrepid/w32codecs.html)

Thanks, but both of those packages were already installed and Amarok isn't finding wma files.

---

### Post by SuperSonic4 on 2008-12-27
I'm not sure, I don't have a wma file to test it on >.<

Edit: seems I can play wma without a problem, or a wma rip of an flv anyway. I installed kubuntu-restricted-extras

---

### Post by Roger Allott on 2008-12-29
I'm struggling to think that my problem can be codec related because wma files play perfectly well in Banshee.

So, if I install the package (metapackage?) kubuntu-restricted-extras, there won't be some horrid conflict somewhere down the line?

---

### Post by josepato on 2011-03-15
thanxs works great.. I use it on ubuntu 10.04

---

