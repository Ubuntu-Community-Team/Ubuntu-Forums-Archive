---
title: "Libdvdcss does not install"
date: 2009-02-05
forum: Multimedia Software
---

### Post by faith1215 on 2009-02-05
The general issue is that DVDs will not play on my computer. MoviePlayer[xine] came up with an error reading
```
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?
```

So, I downloaded libdvdcss-1.2.9
Ran ./configure, make, make install

During the make I get the following messages:
```
make  all-recursive
make[1]: Entering directory `/home/faythe/Downloads/libdvdcss-1.2.9'
Making all in src
make[2]: Entering directory `/home/faythe/Downloads/libdvdcss-1.2.9/src'
Making all in dvdcss
make[3]: Entering directory `/home/faythe/Downloads/libdvdcss-1.2.9/src/dvdcss'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/faythe/Downloads/libdvdcss-1.2.9/src/dvdcss'
make[3]: Entering directory `/home/faythe/Downloads/libdvdcss-1.2.9/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/faythe/Downloads/libdvdcss-1.2.9/src'
make[2]: Leaving directory `/home/faythe/Downloads/libdvdcss-1.2.9/src'
Making all in test
make[2]: Entering directory `/home/faythe/Downloads/libdvdcss-1.2.9/test'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/faythe/Downloads/libdvdcss-1.2.9/test'
Making all in doc
make[2]: Entering directory `/home/faythe/Downloads/libdvdcss-1.2.9/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/faythe/Downloads/libdvdcss-1.2.9/doc'
make[2]: Entering directory `/home/faythe/Downloads/libdvdcss-1.2.9'
make[2]: Leaving directory `/home/faythe/Downloads/libdvdcss-1.2.9'
make[1]: Leaving directory `/home/faythe/Downloads/libdvdcss-1.2.9'

```

And during make install I get:
```

Making install in src
make[1]: Entering directory `/home/faythe/Downloads/libdvdcss-1.2.9/src'
Making install in dvdcss
make[2]: Entering directory `/home/faythe/Downloads/libdvdcss-1.2.9/src/dvdcss'
make[3]: Entering directory `/home/faythe/Downloads/libdvdcss-1.2.9/src/dvdcss'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dvdcss" || mkdir -p -- "/usr/local/include/dvdcss"
 /usr/bin/install -c -m 644 'dvdcss.h' '/usr/local/include/dvdcss/dvdcss.h'
/usr/bin/install: cannot remove `/usr/local/include/dvdcss/dvdcss.h': Permission denied
make[3]: *** [install-pkgincludeHEADERS] Error 1
make[3]: Leaving directory `/home/faythe/Downloads/libdvdcss-1.2.9/src/dvdcss'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/faythe/Downloads/libdvdcss-1.2.9/src/dvdcss'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/faythe/Downloads/libdvdcss-1.2.9/src'
make: *** [install-recursive] Error 1
```


I've tried searching various sites for help, but I am stuck.

I'd appreciate any help!

---

### Post by jolx on 2009-02-05
last time i checked you need to add the medibuntu repository and install it from there [LINK]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by binbash on 2009-02-05
you can install it from medibuntu repository.Anyways you are getting that error because you gave make install NOT sudo make install ;)

---

