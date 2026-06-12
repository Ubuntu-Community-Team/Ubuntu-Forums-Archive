---
title: "Having problems compiling Inkscape"
date: 2009-02-21
forum: Multimedia Software
---

### Post by YaronSh on 2009-02-21
Hello guys!
I don't know if this is the right forum to post this but I'm having problems compiling the newest Inkscape sources from SVN

I tried running autogen.sh but I got the following error:
```
Running intltoolize --copy --force --automake ...
  intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite
Please fix the error conditions and try again.
```

I ignored the following and tried running ./configure
And got the following:
```
checking for new_aspell_config in -laspell... no
configure: error: aspell is needed to compile inkscape

```

I checked whether aspell is installed (sudo apt-get install aspell) and it shows that my aspell is installed and updated

I don't know what should I do next...
My Ubuntu version is 8.04 (I installed all the required packages listed at the Inkscape website)

Can anyone tell me what have I done wrong?

---

