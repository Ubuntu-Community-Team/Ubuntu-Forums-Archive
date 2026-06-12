---
title: "KdenLive - Compile Error"
date: 2008-02-22
forum: Multimedia Production
---

### Post by alphan on 2008-02-22
Hi everybody and salute to all of my masters,

I have a c++ compile problem on Ubuntu 7.10 with "KdenLive Video Editing" Application. I'm a newbie programmer on Linux c++, so I can't solve the problem myself. I googled for all related topics but can't found any solution.

This application will be very useful for my video editing school project. I must to make some small changes on this application and compile it. So firstly, I decided to compile the original code, after it works, I will start to change some codes and recompile it. But I can't compile the original yet.

Ok, here is the what I did and what is my problem:

I read all dependencies on [www.kdenlive.org](www.kdenlive.org) Wiki Pages and install all of them, including KDE environment and lots of extra dev packages. So, I found a builder script: [http://code.google.com/p/kdenlive-dev-helpers/](http://code.google.com/p/kdenlive-dev-helpers/)

This builder script is downloading some other dependencies (ffmpeg, mlt, mlt++) and KdenLive from SVN, and compiling all of them. Everything looking almost right until it come the last part of the script: compiling the KdenLive.


I'm getting some warnings like below before compiling KdenLive:
flvenc.c:131: warning: ‘videocodecid’ may be used uninitialized in this function

And some warnings like this:
```
nutdec.c:823: warning: passing argument 3 of ‘av_tree_find’ from incompatible pointer type
```

Like this:
```
rgb2rgb_template.c:274: warning: cast discards qualifiers from pointer target type
```

And like this:
```
yuv2rgb.c:397: warning: unused variable ‘Y’
```



But I think the warnings are not very important, aren't they?

And finally, this is the final error that stops the compile process:
```

make[2]: Entering directory `/home/alphan/mlt/src/modules/avformat'
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I/home/alphan/build/kdenlive.2008-02-22_15_23/include/ffmpeg  -I../.. -DSWSCALE   -c -o factory.o factory.c
factory.c: In function ‘avformat_destroy’:
factory.c:63: warning: ‘av_free_static’ is deprecated (declared at /home/alphan/build/kdenlive.2008-02-22_15_23/include/ffmpeg/avcodec.h:2894)
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I/home/alphan/build/kdenlive.2008-02-22_15_23/include/ffmpeg  -I../.. -DSWSCALE   -c -o producer_avformat.o producer_avformat.c
producer_avformat.c: In function ‘producer_open’:
producer_avformat.c:206: error: ‘AVFormatParameters’ has no member named ‘device’
producer_avformat.c: In function ‘producer_get_image’:
producer_avformat.c:491: warning: unused variable ‘current_position’
producer_avformat.c:470: warning: unused variable ‘real_timecode’
producer_avformat.c: In function ‘producer_get_audio’:
producer_avformat.c:906: warning: ‘avcodec_decode_audio’ is deprecated (declared at /home/alphan/build/kdenlive.2008-02-22_15_23/include/ffmpeg/avcodec.h:2615)
make[2]: *** [producer_avformat.o] Error 1
make[2]: Leaving directory `/home/alphan/mlt/src/modules/avformat'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/alphan/mlt/src/modules'
make: *** [all] Error 1
```


I said "OK"! I will try another way. And I read the INSTALL file that comes with KdenLive SVN package.

So I run the command:
```
sudo cmake .
```

Ok, no warning and no error. Next step:
```
sudo make
```

I saw some warnings again, like these:
```
[  0%] Generating avfile.moc.cpp
/home/alphan/kdenlive/kdenlive/avfile.h:0: Warning: No relevant classes found. No output generated.
[ 10%] Generating kdenlivesplash.moc.cpp
/home/alphan/kdenlive/kdenlive/kdenlivesplash.h:0: Warning: No relevant classes found. No output generated.  
```                                              


And finally it is start to scan and gave an error:
```
Scanning dependencies of target kdenlive
[ 40%] Building CXX object kdenlive/CMakeFiles/kdenlive.dir/avfilelist.o
[ 40%] Building CXX object kdenlive/CMakeFiles/kdenlive.dir/aviconviewitem.o
[ 40%] Building CXX object kdenlive/CMakeFiles/kdenlive.dir/avlistviewitem.o
/home/alphan/kdenlive/kdenlive/avlistviewitem.cpp: In member function ‘void AVListViewItem::doCommonCtor()’:
/home/alphan/kdenlive/kdenlive/avlistviewitem.cpp:56: warning: unused variable ‘node’
[ 40%] Building CXX object kdenlive/CMakeFiles/kdenlive.dir/baselistviewitem.o
[ 40%] Building CXX object kdenlive/CMakeFiles/kdenlive.dir/westleylistviewitem.o
/home/alphan/kdenlive/kdenlive/westleylistviewitem.cpp:50: warning: unused parameter ‘itemName’
/home/alphan/kdenlive/kdenlive/westleylistviewitem.cpp: In member function ‘void WestleyListViewItem::parseItem(int, int)’:
/home/alphan/kdenlive/kdenlive/westleylistviewitem.cpp:105: warning: ‘exists’ is deprecated (declared at /usr/include/kde/kio/netaccess.h:282)
[ 40%] Building CXX object kdenlive/CMakeFiles/kdenlive.dir/clipdrag.o
[ 41%] Building CXX object kdenlive/CMakeFiles/kdenlive.dir/clipmanager.o
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:800:2: warning: #warning "This might blow up spectacularly - this implementation does not check"
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:801:2: warning: #warning "and clean up any references to said clips."
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:866:2: warning: #warning - to be written
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:885:2: warning: #warning - to be written
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:892:2: warning: #warning - to be written.
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:942:2: warning: no newline at end of file
/home/alphan/kdenlive/kdenlive/./initeffects.h:40: error: ISO C++ forbids declaration of ‘Repository’ with no type
/home/alphan/kdenlive/kdenlive/./initeffects.h:40: error: invalid use of ‘::’
/home/alphan/kdenlive/kdenlive/./initeffects.h:40: error: expected ‘;’ before ‘*’ token
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:42: warning: unused parameter ‘parent’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:42: warning: unused parameter ‘name’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:319: warning: unused parameter ‘pix’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:411: warning: unused parameter ‘thumbnailFrame’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:535: warning: unused parameter ‘extension’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp: In member function ‘QValueList<QPoint> ClipManager::virtualZones()’:
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:741: warning: passing ‘double’ for argument 1 to ‘QPoint::QPoint(int, int)’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:741: warning: passing ‘double’ for argument 2 to ‘QPoint::QPoint(int, int)’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp: In member function ‘DocClipBase* ClipManager::findClip(const KURL&)’:
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:752: warning: unused variable ‘avClip’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp: At global scope:
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:864: warning: unused parameter ‘file’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:883: warning: unused parameter ‘clip’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp: In member function ‘DocClipBase* ClipManager::addTemporaryClip(const KURL&)’:
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:909: warning: passing ‘double’ for argument 1 to ‘void Timecode::setFormat(int, bool, Timecode::Formats)’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp: At global scope:
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:925: warning: unused parameter ‘frame’
/home/alphan/kdenlive/kdenlive/clipmanager.cpp: In member function ‘void ClipManager::refreshThumbNails()’:
/home/alphan/kdenlive/kdenlive/clipmanager.cpp:935: warning: unused variable ‘result’
make[2]: *** [kdenlive/CMakeFiles/kdenlive.dir/clipmanager.o] Error 1
make[1]: *** [kdenlive/CMakeFiles/kdenlive.dir/all] Error 2
make: *** [all] Error 2

```
So, I'm here now. Is it possible that I'm using a wrong compiler? Or what can it be?
Any suggestion would be acceptable. I will wait front of the monitor for your reply.

Thank you.

---

### Post by mridkash on 2008-03-12
Compile a new mlt++

Here is the link to [kdenlive forum]("http://www.kdenlive.org/bbforum/viewtopic.php?f=8&t=477&sid=bcd83a5e5270c34633d7c23aac97b647#p1651") for this problem



---

