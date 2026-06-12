---
title: "gstreamer coming with ubuntu-desktop repository?"
date: 2016-03-24
forum: Multimedia Software
---

### Post by jiapei100 on 2016-03-24
Hi, all:

I'm using Ubuntu 14.04.4 LTS, and it seems the default gstreamer coming with Ubuntu-desktop repository is a bit confusing?

The structure of gstreamer source code is quite clear here    ```
 https://gstreamer.freedesktop.org/src/ 
```
But in the Ubuntu repository, ** gstreamer-1.0  libstreamer-0.10 ** are all there, which make things messy (In my point of view).

Also, I'm building the newest VLC-git, and it builds with gstreamer. I got the following **ERROR** messages:
```
jiapei@jiapei-GT72-6QE:~/Downloads/videoprocessing/vlc/vlc$ make >> 1.txt
In file included from /usr/include/gstreamer-1.0/gst/gstallocator.h:26:0,
                 from codec/gstreamer/gstvlcpictureplaneallocator.c:27:
/usr/include/gstreamer-1.0/gst/gstmemory.h:55:35: error: ‘GST_MINI_OBJECT_FLAG_LOCK_READONLY’ undeclared here (not in a function)
   GST_MEMORY_FLAG_READONLY      = GST_MINI_OBJECT_FLAG_LOCK_READONLY,
                                   ^
/usr/include/gstreamer-1.0/gst/gstmemory.h:56:36: error: ‘GST_MINI_OBJECT_FLAG_LAST’ undeclared here (not in a function)
   GST_MEMORY_FLAG_NO_SHARE      = (GST_MINI_OBJECT_FLAG_LAST << 0),
                                    ^
/usr/include/gstreamer-1.0/gst/gstmemory.h:152:3: error: unknown type name ‘GstMiniObject’
   GstMiniObject   mini_object;
   ^
/usr/include/gstreamer-1.0/gst/gstmemory.h:172:23: error: ‘GST_LOCK_FLAG_READ’ undeclared here (not in a function)
   GST_MAP_READ      = GST_LOCK_FLAG_READ,
                       ^
/usr/include/gstreamer-1.0/gst/gstmemory.h:173:23: error: ‘GST_LOCK_FLAG_WRITE’ undeclared here (not in a function)
   GST_MAP_WRITE     = GST_LOCK_FLAG_WRITE,
                       ^
/usr/include/gstreamer-1.0/gst/gstmemory.h: In function ‘gst_memory_ref’:
/usr/include/gstreamer-1.0/gst/gstmemory.h:309:3: error: implicit declaration of function ‘gst_mini_object_ref’ [-Werror=implicit-function-declaration]
   return (GstMemory *) gst_mini_object_ref (GST_MINI_OBJECT_CAST (memory));
   ^
/usr/include/gstreamer-1.0/gst/gstmemory.h:309:3: error: implicit declaration of function ‘GST_MINI_OBJECT_CAST’ [-Werror=implicit-function-declaration]
/usr/include/gstreamer-1.0/gst/gstmemory.h:309:10: warning: cast from function call of type ‘int’ to non-matching type ‘struct GstMemory *’ [-Wbad-function-cast]
   return (GstMemory *) gst_mini_object_ref (GST_MINI_OBJECT_CAST (memory));
          ^
/usr/include/gstreamer-1.0/gst/gstmemory.h:309:10: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/usr/include/gstreamer-1.0/gst/gstmemory.h: In function ‘gst_memory_unref’:
/usr/include/gstreamer-1.0/gst/gstmemory.h:325:3: error: implicit declaration of function ‘gst_mini_object_unref’ [-Werror=implicit-function-declaration]
   gst_mini_object_unref (GST_MINI_OBJECT_CAST (memory));
   ^
In file included from codec/gstreamer/gstvlcpictureplaneallocator.c:27:0:
/usr/include/gstreamer-1.0/gst/gstallocator.h: At top level:
/usr/include/gstreamer-1.0/gst/gstallocator.h:88:39: error: ‘GST_OBJECT_FLAG_LAST’ undeclared here (not in a function)
   GST_ALLOCATOR_FLAG_CUSTOM_ALLOC  = (GST_OBJECT_FLAG_LAST << 0),
                                       ^
/usr/include/gstreamer-1.0/gst/gstallocator.h:107:3: error: unknown type name ‘GstObject’
   GstObject  object;
   ^
/usr/include/gstreamer-1.0/gst/gstallocator.h:125:3: error: unknown type name ‘GstObjectClass’
   GstObjectClass object_class;
   ^
In file included from /usr/include/gstreamer-1.0/gst/gstbuffer.h:27:0,
                 from /usr/include/gstreamer-1.0/gst/gstpad.h:65,
                 from /usr/include/gstreamer-1.0/gst/gstelement.h:57,
                 from /usr/include/gstreamer-1.0/gst/gstbin.h:27,
                 from /usr/include/gstreamer-1.0/gst/gst.h:34,
                 from codec/gstreamer/gstvlcpictureplaneallocator.h:30,
                 from codec/gstreamer/gstvlcpictureplaneallocator.c:29:
/usr/include/gstreamer-1.0/gst/gstminiobject.h:229:17: error: conflicting types for ‘gst_mini_object_ref’
 GstMiniObject * gst_mini_object_ref  (GstMiniObject *mini_object);
                 ^
In file included from /usr/include/gstreamer-1.0/gst/gstallocator.h:26:0,
                 from codec/gstreamer/gstvlcpictureplaneallocator.c:27:
/usr/include/gstreamer-1.0/gst/gstmemory.h:309:24: note: previous implicit declaration of ‘gst_mini_object_ref’ was here
   return (GstMemory *) gst_mini_object_ref (GST_MINI_OBJECT_CAST (memory));
                        ^
In file included from /usr/include/gstreamer-1.0/gst/gstbuffer.h:27:0,
                 from /usr/include/gstreamer-1.0/gst/gstpad.h:65,
                 from /usr/include/gstreamer-1.0/gst/gstelement.h:57,
                 from /usr/include/gstreamer-1.0/gst/gstbin.h:27,
                 from /usr/include/gstreamer-1.0/gst/gst.h:34,
                 from codec/gstreamer/gstvlcpictureplaneallocator.h:30,
                 from codec/gstreamer/gstvlcpictureplaneallocator.c:29:
/usr/include/gstreamer-1.0/gst/gstminiobject.h:230:17: warning: conflicting types for ‘gst_mini_object_unref’ [enabled by default]
 void            gst_mini_object_unref  (GstMiniObject *mini_object);
                 ^
In file included from /usr/include/gstreamer-1.0/gst/gstallocator.h:26:0,
                 from codec/gstreamer/gstvlcpictureplaneallocator.c:27:
/usr/include/gstreamer-1.0/gst/gstmemory.h:325:3: note: previous implicit declaration of ‘gst_mini_object_unref’ was here
   gst_mini_object_unref (GST_MINI_OBJECT_CAST (memory));
   ^
cc1: some warnings being treated as errors
make[4]: *** [codec/gstreamer/libgstdecode_plugin_la-gstvlcpictureplaneallocator.lo] Error 1
make[3]: *** [all-recursive] Error 1
make[2]: *** [all] Error 2
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2

```


Now, I would like to remove the default gstreamer, and rebuild everything related to gstreamer from scratch, all by myself.
However, whenever I tried to remove some gstreamer packages, **Ubuntu-desktop** needs to be removed at the same time, which is **NOT** what I expected.
[IMG]http://www.longervision.com/questions/ubuntugstreamer.png[/IMG]
For me, gstreamer is NOT for desktop display at all, it's mostly for video/audio signal transmission protocols. Isn't it???

Cheers
Pei

---

### Post by bernard-godard on 2016-03-28
Gstreamer is used by some "core" applications and so you should not remove it. But you can still build and install your own gstreamer in /usr/local or /opt or some other places like your user account and tell the vlc build system the location of your gstreamer include files and shared objects.

---

### Post by Yellow Pasque on 2016-03-29
ubuntu-desktop is a "metapackage" (a package that depnds on other packages) and is safe to remove if you want to do a custom gstreamer install. It will not remove your desktop or anything like that.
Depending on your use of VLC, it may be a lot easier/safer to simply disable gstreamer decoding support by using '--disable-gst-decode' option with configure.

---

### Post by mcduck on 2016-03-31
> **jiapei100 said:**
> Hi, all:
For me, gstreamer is NOT for desktop display at all, it's mostly for video/audio signal transmission protocols. Isn't it???

Cheers
Pei
That is correct, gstreamer doesn't need the desktop.

However that doesn't mean that the desktop stuff wouldn't need gstreamer. ;) Dependencies are one-directional, for example a desktop music player can depend on gstreamer to play back audio, while gstreamer doesn't need the music player for anything.

---

### Post by bernard-godard on 2016-03-31
> **mcduck said:**
> That is correct, gstreamer doesn't need the desktop.

However that doesn't mean that the desktop stuff wouldn't need gstreamer. ;) Dependencies are one-directional, for example a desktop music player can depend on gstreamer to play back audio, while gstreamer doesn't need the music player for anything.

Yes if you remove gstreamer, you will probably lose:
* the default music player Rhythmbox
* the default video player totem
* default Nautilus video thumb-nailer

---

