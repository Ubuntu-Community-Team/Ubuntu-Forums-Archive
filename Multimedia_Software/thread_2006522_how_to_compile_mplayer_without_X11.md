---
title: "how to compile mplayer without X11"
date: 2012-06-19
forum: Multimedia Software
---

### Post by newbie15 on 2012-06-19
Hi all,

I am trying to do a first time install of mplayer without X11 options. So can anyone suggest me the procedure to make it work in a smoother way, so that i wont jump out of it:confused:

---

### Post by andrew.46 on 2012-06-19
I guess you could use the following option:

```

--disable-x11

```

Have a look here for some general compilation details as well:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

---

### Post by newbie15 on 2012-06-20
When I am trying to compile the mplayer with "--disable-x11" option i'm getting the below error, not able to find what needs to be fixed... 

any ideas regarding this will be of great help...

```
cc -MD -MP -Wundef -W -Wall -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99  -O2 -march=native -mtune=native -pipe -g  -fno-tree-vectorize -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I. -Iffmpeg  -D_REENTRANT -I/usr/include/directfb -I/usr/include/   -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT   -I/usr/include/freetype2 -c -o edl.o edl.c
cc -MD -MP -Wundef -W -Wall -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99  -O2 -march=native -mtune=native -pipe -g  -fno-tree-vectorize -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I. -Iffmpeg  -D_REENTRANT -I/usr/include/directfb -I/usr/include/   -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT   -I/usr/include/freetype2 -c -o fmt-conversion.o fmt-conversion.c
fmt-conversion.c:34: error: 'PIX_FMT_RGB565BE' undeclared here (not in a function)
fmt-conversion.c:34: warning: missing initializer
fmt-conversion.c:34: warning: (near initialization for 'conversion_map[3].pix_fmt')
fmt-conversion.c:35: error: 'PIX_FMT_RGB565LE' undeclared here (not in a function)
fmt-conversion.c:35: warning: missing initializer
fmt-conversion.c:35: warning: (near initialization for 'conversion_map[4].pix_fmt')
fmt-conversion.c:36: error: 'PIX_FMT_RGB555BE' undeclared here (not in a function)
fmt-conversion.c:36: warning: missing initializer
fmt-conversion.c:36: warning: (near initialization for 'conversion_map[5].pix_fmt')
fmt-conversion.c:37: error: 'PIX_FMT_RGB555LE' undeclared here (not in a function)
fmt-conversion.c:37: warning: missing initializer
fmt-conversion.c:37: warning: (near initialization for 'conversion_map[6].pix_fmt')
fmt-conversion.c:38: error: 'PIX_FMT_RGB444BE' undeclared here (not in a function)
fmt-conversion.c:38: warning: missing initializer
fmt-conversion.c:38: warning: (near initialization for 'conversion_map[7].pix_fmt')
fmt-conversion.c:39: error: 'PIX_FMT_RGB444LE' undeclared here (not in a function)
fmt-conversion.c:39: warning: missing initializer
fmt-conversion.c:39: warning: (near initialization for 'conversion_map[8].pix_fmt')
fmt-conversion.c:51: error: 'PIX_FMT_BGR565BE' undeclared here (not in a function)
fmt-conversion.c:51: warning: missing initializer
fmt-conversion.c:51: warning: (near initialization for 'conversion_map[20].pix_fmt')
fmt-conversion.c:52: error: 'PIX_FMT_BGR565LE' undeclared here (not in a function)
fmt-conversion.c:52: warning: missing initializer
fmt-conversion.c:52: warning: (near initialization for 'conversion_map[21].pix_fmt')
fmt-conversion.c:53: error: 'PIX_FMT_BGR555BE' undeclared here (not in a function)
fmt-conversion.c:53: warning: missing initializer
fmt-conversion.c:53: warning: (near initialization for 'conversion_map[22].pix_fmt')
fmt-conversion.c:54: error: 'PIX_FMT_BGR555LE' undeclared here (not in a function)
fmt-conversion.c:54: warning: missing initializer
fmt-conversion.c:54: warning: (near initialization for 'conversion_map[23].pix_fmt')
fmt-conversion.c:55: error: 'PIX_FMT_BGR444BE' undeclared here (not in a function)
fmt-conversion.c:55: warning: missing initializer
fmt-conversion.c:55: warning: (near initialization for 'conversion_map[24].pix_fmt')
fmt-conversion.c:56: error: 'PIX_FMT_BGR444LE' undeclared here (not in a function)
fmt-conversion.c:56: warning: missing initializer
fmt-conversion.c:56: warning: (near initialization for 'conversion_map[25].pix_fmt')
fmt-conversion.c:92: error: 'PIX_FMT_YUV420P16LE' undeclared here (not in a function)
fmt-conversion.c:92: warning: missing initializer
fmt-conversion.c:92: warning: (near initialization for 'conversion_map[45].pix_fmt')
fmt-conversion.c:93: error: 'PIX_FMT_YUV420P16BE' undeclared here (not in a function)
fmt-conversion.c:93: warning: missing initializer
fmt-conversion.c:93: warning: (near initialization for 'conversion_map[46].pix_fmt')
fmt-conversion.c:94: error: 'PIX_FMT_YUV420P10LE' undeclared here (not in a function)
fmt-conversion.c:94: warning: missing initializer
fmt-conversion.c:94: warning: (near initialization for 'conversion_map[47].pix_fmt')
fmt-conversion.c:95: error: 'PIX_FMT_YUV420P10BE' undeclared here (not in a function)
fmt-conversion.c:95: warning: missing initializer
fmt-conversion.c:95: warning: (near initialization for 'conversion_map[48].pix_fmt')
fmt-conversion.c:96: error: 'PIX_FMT_YUV420P9LE' undeclared here (not in a function)
fmt-conversion.c:96: warning: missing initializer
fmt-conversion.c:96: warning: (near initialization for 'conversion_map[49].pix_fmt')
fmt-conversion.c:97: error: 'PIX_FMT_YUV420P9BE' undeclared here (not in a function)
fmt-conversion.c:97: warning: missing initializer
fmt-conversion.c:97: warning: (near initialization for 'conversion_map[50].pix_fmt')
fmt-conversion.c:98: error: 'PIX_FMT_YUV422P16LE' undeclared here (not in a function)
fmt-conversion.c:98: warning: missing initializer
fmt-conversion.c:98: warning: (near initialization for 'conversion_map[51].pix_fmt')
fmt-conversion.c:99: error: 'PIX_FMT_YUV422P16BE' undeclared here (not in a function)
fmt-conversion.c:99: warning: missing initializer
fmt-conversion.c:99: warning: (near initialization for 'conversion_map[52].pix_fmt')
fmt-conversion.c:100: error: 'PIX_FMT_YUV422P10LE' undeclared here (not in a function)
fmt-conversion.c:100: warning: missing initializer
fmt-conversion.c:100: warning: (near initialization for 'conversion_map[53].pix_fmt')
fmt-conversion.c:101: error: 'PIX_FMT_YUV422P10BE' undeclared here (not in a function)
fmt-conversion.c:101: warning: missing initializer
fmt-conversion.c:101: warning: (near initialization for 'conversion_map[54].pix_fmt')
fmt-conversion.c:102: error: 'PIX_FMT_YUV422P9LE' undeclared here (not in a function)
fmt-conversion.c:102: warning: missing initializer
fmt-conversion.c:102: warning: (near initialization for 'conversion_map[55].pix_fmt')
fmt-conversion.c:103: error: 'PIX_FMT_YUV422P9BE' undeclared here (not in a function)
fmt-conversion.c:103: warning: missing initializer
fmt-conversion.c:103: warning: (near initialization for 'conversion_map[56].pix_fmt')
fmt-conversion.c:104: error: 'PIX_FMT_YUV444P16LE' undeclared here (not in a function)
fmt-conversion.c:104: warning: missing initializer
fmt-conversion.c:104: warning: (near initialization for 'conversion_map[57].pix_fmt')
fmt-conversion.c:105: error: 'PIX_FMT_YUV444P16BE' undeclared here (not in a function)
fmt-conversion.c:105: warning: missing initializer
fmt-conversion.c:105: warning: (near initialization for 'conversion_map[58].pix_fmt')
fmt-conversion.c:106: error: 'PIX_FMT_YUV444P10LE' undeclared here (not in a function)
fmt-conversion.c:106: warning: missing initializer
fmt-conversion.c:106: warning: (near initialization for 'conversion_map[59].pix_fmt')
fmt-conversion.c:107: error: 'PIX_FMT_YUV444P10BE' undeclared here (not in a function)
fmt-conversion.c:107: warning: missing initializer
fmt-conversion.c:107: warning: (near initialization for 'conversion_map[60].pix_fmt')
fmt-conversion.c:108: error: 'PIX_FMT_YUV444P9LE' undeclared here (not in a function)
fmt-conversion.c:108: warning: missing initializer
fmt-conversion.c:108: warning: (near initialization for 'conversion_map[61].pix_fmt')
fmt-conversion.c:109: error: 'PIX_FMT_YUV444P9BE' undeclared here (not in a function)
fmt-conversion.c:109: warning: missing initializer
fmt-conversion.c:109: warning: (near initialization for 'conversion_map[62].pix_fmt')
fmt-conversion.c:126: error: 'PIX_FMT_VDPAU_MPEG4' undeclared here (not in a function)
fmt-conversion.c:126: warning: missing initializer
fmt-conversion.c:126: warning: (near initialization for 'conversion_map[74].pix_fmt')
make: *** [fmt-conversion.o] Error 1
```

---

