---
title: "compilation error of libkexiv2 in Digikam SVN"
date: 2007-03-28
forum: Multimedia &amp; Video
---

### Post by ToohTaah on 2007-03-28
Hi,

I have tried to compile digikam SVN from this [link]("http://www.digikam.org/?q=download/svn"). I had no problem compiling it before on my system. However, a few weeks ago, I got error messages when trying to compile libkexiv2. The error message is;

```

if /bin/bash ../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../libkipi/libkipi -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -fexceptions  -MT kexiv2.lo -MD -MP -MF ".deps/kexiv2.Tpo" -c -o kexiv2.lo kexiv2.cpp; \
        then mv -f ".deps/kexiv2.Tpo" ".deps/kexiv2.Plo"; else rm -f ".deps/kexiv2.Tpo"; exit 1; fi
/bin/bash ../libtool --silent --tag=CXX --mode=link g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -fexceptions    -o libkexiv2.la -rpath /usr/lib -L/usr/share/qt3/lib     -R /usr/lib -R /usr/lib -R /usr/share/qt3/lib -version-info 1:0:1 -no-undefined -Wl,--no-undefined -Wl,--allow-shlib-undefined kexiv2.lo -lexiv2   -lkdecore -lqt-mt  -lz -lpng -lz -lm -lXext -lX11  -lSM -lICE -lpthread
.libs/kexiv2.o: In function `KExiv2Iface::KExiv2::getIptc(bool) const':
kexiv2.cpp:(.text+0x2341): undefined reference to `Exiv2::versionNumber()'
.libs/kexiv2.o: In function `KExiv2Iface::KExiv2::setImageProgramId(QString const&, QString const&)':
kexiv2.cpp:(.text+0xbf5b): undefined reference to `Exiv2::versionNumber()'
.libs/kexiv2.o: In function `KExiv2Iface::KExiv2::convertCommentValue(Exiv2::Exifdatum const&)':
kexiv2.cpp:(.text+0xc963): undefined reference to `Exiv2::versionNumber()'
collect2: ld returned 1 exit status
make[2]: *** [libkexiv2.la] Error 1

```

any idea how to fix this error?

---

### Post by ToohTaah on 2007-03-28
Sorry, I put it to a wrong section.

---

