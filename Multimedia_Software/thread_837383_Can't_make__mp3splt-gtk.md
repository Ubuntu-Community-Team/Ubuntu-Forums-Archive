---
title: "Can't make  mp3splt-gtk"
date: 2008-06-22
forum: Multimedia Software
---

### Post by devehf on 2008-06-22
Starting a new thread because another one was stale.

Trying to install mp3splt-gtk so I can easily split huge MP3 archives of concerts I have streamed into individual band's sets.

A couple pf people have reported that the deb package doesn't work  due to a [BMP dependency error]("http://ubuntuforums.org/showpost.php?p=5121684&postcount=5"). I tried to make the binary with make and got the following error.

```
In file included from /usr/include/libmp3splt/mp3splt.h:34,
                 from tree_tab.c:41:
/usr/include/libmp3splt/mp3splt_types.h:34:17: error: mad.h: No such file or directory
In file included from /usr/include/libmp3splt/mp3splt.h:34,
                 from tree_tab.c:41:
/usr/include/libmp3splt/mp3splt_types.h:296: error: field &#8216;stream&#8217; has incomplete type
/usr/include/libmp3splt/mp3splt_types.h:297: error: field &#8216;frame&#8217; has incomplete type
/usr/include/libmp3splt/mp3splt_types.h:298: error: field &#8216;synth&#8217; has incomplete type
/usr/include/libmp3splt/mp3splt_types.h:300: error: expected specifier-qualifier-list before &#8216;mad_fixed_t&#8217;
make[2]: *** [tree_tab.o] Error 1
make[2]: Leaving directory `/home/davef/mp3splt-gtk/mp3splt-gtk-0.3.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/davef/mp3splt-gtk/mp3splt-gtk-0.3.1'
make: *** [all] Error 2
```

I don't understand the error msg because the directory "/usr/include/libmp3splt" certainly exists as does the mp3splt_types.h file. is there an error in this file? Is the error saying that 'mad.h' does not exist? This is true. How would I troubleshoot this?

---

### Post by Jose Catre-Vandis on 2008-08-02
Did you run make as root, e.g.

```
sudo make
sudo make install
```

Also check you have libmp3splt package properly installed from mp3splt site

---

### Post by optimix on 2008-09-05
You can try installing the new mp3splt-gtk version 0.5 which supports Audacious instead of Beep Media Player. The compilation error is due to the missing 'mad.h' header file which is found in the libmad development package. libmp3splt will have to be modified to check also for the headers of the libraries.

---

