---
title: "intalling gimp plugin, gimp-lensfun"
date: 2015-11-17
forum: Multimedia Software
---

### Post by andrewsc0 on 2015-11-17
Hello I'm trying to install the new 2.4 version of the gimp-lensfun plugin, because it should add a lens I use and the 2.3.1 version in the software center does not have it. 

I'm following the instructions located here:
[http://seebk.github.io/GIMP-Lensfun/](http://seebk.github.io/GIMP-Lensfun/)

Specifically
> [COLOR=#000000][FONT=Verdana]On (K)Ubuntu you can easily install the required libs by[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]>$ sudo apt-get install build-essential libgimp2.0-dev libexiv2-dev liblensfun-dev[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]On Fedora 15 (and probably other versions, too) you need to install these packages[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]gcc, gcc-c++, gimp-devel-tools, lensfun-devel, exiv2-devel[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Afterwards get the sources from github:[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]>$ git clone git://github.com/seebk/GIMP-Lensfun.git[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Enter the directory and compile with "make":[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]>$ cd GIMP-Lensfun
>$ make[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]If all went fine copy the newly created binary file "gimplensfun" to your GIMP plugins folder. Normally you find this at "/home/USER/.gimp-2.8/plug-ins/".[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]You need to restart GIMP to detect the new plugin.[/FONT][/COLOR]




However after running  $ make I get the following output with the final error and I have zero idea what it is or how to fix it.

```
g++ -DDEBUG=0 -O3 -Wall -fopenmp -pthread -I/usr/include/gtk-2.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/harfbuzz -I/usr/include/gimp-2.0   -I/usr/local/include -I/usr/local/include/lensfun -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -c -o src/gimplensfun.o src/gimplensfun.cppIn file included from /usr/include/exiv2/metadatum.hpp:39:0,
                 from /usr/include/exiv2/exif.hpp:34,
                 from /usr/include/exiv2/image.hpp:41,
                 from src/gimplensfun.cpp:34:
/usr/include/exiv2/value.hpp:984:25: note: attribute for ‘struct Exiv2::DateValue::Date’ must follow the ‘struct’ keyword
         EXIV2API struct Date
                         ^
src/gimplensfun.cpp: In function ‘void query()’:
src/gimplensfun.cpp:205:5: warning: deprecated conversion from string constant to ‘gchar* {aka char*}’ [-Wwrite-strings]
     };
     ^
src/gimplensfun.cpp:205:5: warning: deprecated conversion from string constant to ‘gchar* {aka char*}’ [-Wwrite-strings]
src/gimplensfun.cpp:205:5: warning: deprecated conversion from string constant to ‘gchar* {aka char*}’ [-Wwrite-strings]
src/gimplensfun.cpp:205:5: warning: deprecated conversion from string constant to ‘gchar* {aka char*}’ [-Wwrite-strings]
src/gimplensfun.cpp:205:5: warning: deprecated conversion from string constant to ‘gchar* {aka char*}’ [-Wwrite-strings]
src/gimplensfun.cpp:205:5: warning: deprecated conversion from string constant to ‘gchar* {aka char*}’ [-Wwrite-strings]
In file included from src/gimplensfun.cpp:30:0:
/usr/local/include/lensfun/lensfun.h: In function ‘void run(const gchar*, gint, const GimpParam*, gint*, GimpParam**)’:
/usr/local/include/lensfun/lensfun.h:1603:5: error: ‘lfDatabase::lfDatabase()’ is protected
     lfDatabase () {}
     ^
src/gimplensfun.cpp:1232:27: error: within this context
     ldb = new lfDatabase ();
                           ^
make: *** [src/gimplensfun.o] Error 1
```


Anyhelp would be appreciated?

---

### Post by andrewsc0 on 2015-11-17
Anyone?  Is it a permissions issue, when if says > [COLOR=#000000][FONT=Ubuntu Mono]&#8216;lfDatabase::lfDatabase()&#8217; is protected[/FONT][/COLOR]

If so, where is that to change permissions?

---

### Post by steeldriver on 2015-11-18
No it's not a permissions issue, it's a programming issue

If you look in the lensfun.h file mentioned, you will likely see that the lfDatabase is a *protected* class/struct member

```

protected:
    /* Prevent user from creating and destroying such objects */
    lfDatabase () {}
    ~lfDatabase () {}

```

As noted in the comments, this means

```

 * You cannot create and destroy objects of this type directly; instead
 * use the lf_db_new() / lf_db_destroy() functions or the
 * lfDatabase::Create() / lfDatabase::Destroy() methods.

```

The plugin code seems to be trying to do something that's not allowed by the lensfun API - perhaps it was written for an older (or newer) version of lensfun that doesn't have this restriction?

---

### Post by andrewsc0 on 2015-11-18
Interesting, I'm guessing that this isn't a very easy fix for someone like myself who knows nothing about programming... Any ideas how I could get this issue resolved?

Thanks for the clarification steeldriver.

---

### Post by steeldriver on 2015-11-18
What version of lensfun do you have installed in /usr/local? I'm assuming it's not the same as that provided by the liblensfun-dev package from the repository?

---

### Post by andrewsc0 on 2015-11-18
I don't see a version per se in /usr/local what I do have is lots of stuff related to lensfun throughout the directory. In
usr/loca/bin there are three files g-lensfun-update-data, lensfun-add-adapter, lensfun-update-data in 
usr/local/inlude/lensfun there is lensfun.h in 
usr/local/lib is liblensfun.so, liblensfun.so.0 and liblensfun.so.0.3.1 also inin usr/local/lib/pkgconfig is lensfun.pc
there is also a folder of xml files located at usr/local/share/lensfun

I uninstalled the older version of lensfun before attempting to install the new version using [COLOR=#333333][FONT=Menlo]sudo apt-get remove gimp-lensfun[/FONT][/COLOR]

---

