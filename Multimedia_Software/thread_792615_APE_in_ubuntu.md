---
title: "APE in ubuntu"
date: 2008-05-13
forum: Multimedia Software
---

### Post by presston on 2008-05-13
That's way that work for audacious and beep player in my ubuntu 7.10

in terminal

> sudo aptitude install build-essential

> sudo aptitude install nasm

download this:  
[http://supermmx.org/download/linux/mac/mac-3.99-u4-b5.tar.gz](http://supermmx.org/download/linux/mac/mac-3.99-u4-b5.tar.gz)

> tar -zxvf mac-3.99-u4-b5.tar.gz
cd mac-3.99-u4-b5.tar.gz

> ./configure
make
sudo make install

download this:
[http://ubuntuforums.org/attachment.php?attachmentid=47050&d=1192925100](http://ubuntuforums.org/attachment.php?attachmentid=47050&d=1192925100)

make the same for this package.


then we go to audaciuos and make all audio modules (in preference) checked up.

any questions? :popcorn:

---

### Post by Major_Kong on 2008-05-13
If your using a i386 version of ubuntu you could use this - [http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/) - repo.

PS: The newer versions of Audacious already come with a ape plugin.

---

