---
title: "Photoshop CS2 converts jpg to xmp"
date: 2019-03-23
forum: Multimedia Software
---

### Post by claus on 2019-03-23
Hello,

after installing Photoshop CS2 on Ubuntu 18.04 (via wine), almost all of the jpg files in my 'Pictures' folder were replaced with a file with the extension .JPG.xmp. The original jpg files are gone. The xmp files are XML text files only. My question: Is there a way to get back the original jpg's, or are they gone?

TIA,

Claus

---

### Post by #&amp;thj^% on 2019-03-23
I had this happen also about 8 years ago, "exiftool" does the job for me, it's written in perl so should work for you on any o/s

[http://www.sno.phy.queensu.ca/~phil/exiftool](http://www.sno.phy.queensu.ca/~phil/exiftool)

usage :
```

exiftool -all= image.jpg
```
For more options see: [https://libre-software.net/edit-image-metadata-on-linux/](https://libre-software.net/edit-image-metadata-on-linux/)

---

### Post by claus on 2019-03-23
Hi,

I downloaded  & installed "exiftool", but as I understand it, it only extracts exif information included in the .xmp file. The .JPG.xmp files I have are only 1.6k large, so all of the bitmap information is lost. :(
Apparently, there's no way to get back the original jpg's. Nonetheless, [here's]("https://sno.phy.queensu.ca/~phil/exiftool/install.html#Unix") a howto to install "exiftool" on Unix/Linux. This works pretty well.

Claus

---

