---
title: "kdenlive (or perhaps more general?) help needed"
date: 2008-03-05
forum: Multimedia Production
---

### Post by anewguy on 2008-03-05
As noted in a post I had out a few weeks ago, I am trying to join together some videos from a camcorder, but had problems with most everything I tried.  Last night I was doing some more searching, and came across this link which sounds like it may solve my problem (audio is "ahead" of the video stream).  The only problem is, I'm stupid!  Can someone help me through what the post is saying and how to this in Ubuntu Gutsy?

Thanks in advance!  :)

[http://www.kdenlive.org/bbforum/viewtopic.php?f=16&t=92]("http://www.kdenlive.org/bbforum/viewtopic.php?f=16&t=92")

---

### Post by anewguy on 2008-03-06
bump

---

### Post by tubasoldier on 2008-03-06
Kdenlive is pretty decent. But as far as open source video editing it is still a crapshoot. (Unless you have around 6K USD for Autodesk Smoke). IMO Kdenlive has the most potential. If you use it to put together two or more videos then by the time you get to the second video the sound is terribly off kilter with the video. After all it is still BETA software in heavy development. Your best bet is to use *ffmpeg* or something similiar to join them together in the command line. Perhaps someone else knows the command line tools better than me?

If you would like to try it this should install it:
```
sudo apt-get install kdenlive
```

I'm pretty sure you will have to have the Medibuntu repositories as well as the Multiverse/Universe repositories enabled.

---

### Post by anewguy on 2008-03-06
yea, I already have kdenlive installed, and hence the audio problems.  The link I provided is what is supposed to fix the problem.  However I am at a complete loss on how to get this to work in Gutsy.

I followed the website and downloaded 2 tars from sourceforge:  1 for mlt, the other for mlt++.  Then I saw the kdenlive builder script, so I downloaded it.  It did the getsources and the updatesources fine, the "clean" step kicked out but I assume it was because I had never built these before so there was nothing to clean up.  The build step aborts as follows:

dave@dave-desktop:~$ ./kdenlive_builder.sh build
Unknown option "--enable-libogg".
See ./configure --help for available options.


I then tried adding the configuration options mentioned earlier in the post to the build line and got the following:

dave@dave-desktop:~$ ./kdenlive_builder.sh build  --prefix=/usr --enable-gpl --disable-mmx --avformat-swscale --enable-motion-est
Unknown option "--enable-libogg".
See ./configure --help for available options.


I don't know enough to know what to try next.  

:)

---

### Post by anewguy on 2008-03-06
Okay, since I haven't gotten an answer on any of this yet, I went ahead and did a configure/make/make install of ffmpeg.  I then tried the same on mlt and got the following error in the make:

cc -shared -o ../libmltsox.so factory.o filter_sox.o  -lst -lmad -lvorbisenc -lvorbisfile -logg -lasound -lm -lgsm -lsndfile -lsamplerate -L../../framework -lmlt
/usr/bin/ld: cannot find -lsndfile
collect2: ld returned 1 exit status
make[2]: *** [../libmltsox.so] Error 1
make[2]: Leaving directory `/home/dave/mlt/src/modules/sox'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/dave/mlt/src/modules'
make: *** [all] Error 1

Any help would be greatly appreciated!!  If I can get the above to complete successfully, I think all I have to do then is configure/make/make install of kdenlive in order for the changes to be in place so I can try it out to see if it really fixes the problem.:(

---

### Post by anewguy on 2008-03-06
bump

---

### Post by anewguy on 2008-03-06
bump.   Perhaps a moderator could move this to the multimedia forum?

---

### Post by anewguy on 2008-03-07
bump.

---

### Post by PmDematagoda on 2008-03-07
This thread has been moved to the Multimedia Production section on the request of the OP.

---

### Post by anewguy on 2008-03-08
bump.

I have gotten ffmpeg and mlt and mlt++ compiled, but I need help with kdenlive itself.  Here is the output from the make:

dave@dave-desktop:~/kdenlive-0.5$ ls
acinclude.m4         CMakeLists.txt   COPYING       kdenlive.spec  po
aclocal.m4           config.h         debian        libtool        profiles
admin                config.h.in      doc           Makefile       README
AUTHORS              config.log       Doxyfile      Makefile.am    renderer
bootstrap            config.status    graphics      Makefile.cvs   stamp-h1
ChangeLog            configure        icons         Makefile.dist  stamp-h.in
CMakeCache.txt       configure.files  INSTALL       Makefile.in    subdirs
CMakeFiles           configure.in     kdenlive      NEWS           templates
cmake_install.cmake  configure.in.in  kdenlive.lsm  pgm            TODO
dave@dave-desktop:~/kdenlive-0.5$ cmake .
-- Found KDE3 include dir: /usr/include/kde
-- Found KDE3 library dir: /usr/lib
-- Found KDE3 dcopidl preprocessor: /usr/bin/dcopidl
-- Found KDE3 dcopidl2cpp preprocessor: /usr/bin/dcopidl2cpp
-- Found KDE3 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- 
-- Configuring done
-- Generating done
-- Build files have been written to: /home/dave/kdenlive-0.5
dave@dave-desktop:~/kdenlive-0.5$ make
[  0%] Building CXX object kdenlive/CMakeFiles/kdenlive.dir/kdenlive.o
In file included from /home/dave/kdenlive-0.5/kdenlive/kdenlive.cpp:113:
/home/dave/kdenlive-0.5/kdenlive/trackpanelclipmovefunction.h:166:2: warning: #warning - The following method is a bad example for programming design.
/usr/include/kde/keditlistbox.h:60: warning: ‘class KEditListBox::CustomEditor’ has virtual functions but non-virtual destructor
/home/dave/kdenlive-0.5/kdenlive/./dynamicToolTip.h:28: warning: ‘class Gui::DynamicToolTip’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:224: warning: ‘class QXmlReader’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:407: warning: ‘class QXmlContentHandler’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:424: warning: ‘class QXmlErrorHandler’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:433: warning: ‘class QXmlDTDHandler’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:441: warning: ‘class QXmlEntityResolver’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:448: warning: ‘class QXmlLexicalHandler’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:461: warning: ‘class QXmlDeclHandler’ has virtual functions but non-virtual destructor
/home/dave/kdenlive-0.5/kdenlive/projectlistview.h:77: warning: ‘class ListViewToolTip’ has virtual functions but non-virtual destructor
/home/dave/kdenlive-0.5/kdenlive/projecticonview.h:74: warning: ‘class IconViewToolTip’ has virtual functions but non-virtual destructor
/home/dave/kdenlive-0.5/kdenlive/kdenlive.cpp: In member function ‘void Gui::KdenliveApp::parseProfiles()’:
/home/dave/kdenlive-0.5/kdenlive/kdenlive.cpp:271: error: ‘MLT_PREFIX’ was not declared in this scope
/home/dave/kdenlive-0.5/kdenlive/kdenlive.cpp: In member function ‘void Gui::KdenliveApp::setProjectFormat(QString)’:
/home/dave/kdenlive-0.5/kdenlive/kdenlive.cpp:2126: warning: passing ‘double’ for argument 1 to ‘static void KdenliveSettings::setDisplaywidth(int)’
/home/dave/kdenlive-0.5/kdenlive/kdenlive.cpp:2127: warning: passing ‘double’ for argument 1 to ‘static void KdenliveSettings::setDisplaywidth(int)’
/home/dave/kdenlive-0.5/kdenlive/kdenlive.cpp: In member function ‘void Gui::KdenliveApp::slotSetClipDuration()’:
/home/dave/kdenlive-0.5/kdenlive/kdenlive.cpp:3265: warning: unused variable ‘ok’
/home/dave/kdenlive-0.5/kdenlive/kdenlive.cpp: In member function ‘void Gui::KdenliveApp::slotProjectDeleteClips(QStringList)’:
/home/dave/kdenlive-0.5/kdenlive/kdenlive.cpp:3439: warning: unused variable ‘refClip’
make[2]: *** [kdenlive/CMakeFiles/kdenlive.dir/kdenlive.o] Error 1
make[1]: *** [kdenlive/CMakeFiles/kdenlive.dir/all] Error 2
make: *** [all] Error 2
dave@dave-desktop:~/kdenlive-0.5$ 



Any help on this would be GREATLY appreciated!!  :)

---

### Post by anewguy on 2008-03-08
bump.

Any ideas on how to get MLT_PREFIX set as needed based on what it says in the make output above?

:)

---

### Post by forrestcupp on 2008-03-09
It may be a bit overkill, but if you're having trouble with kdenlive, you might give [Cinelerra](http://cv.cinelerra.org/about.php) a try.  It is a pretty robust video editor, but I've never had trouble with it not working right.

[Here](http://cv.cinelerra.org/getting_cinelerra.php#ubuntu) is the link to install it in Ubuntu.

---

### Post by maku-d on 2008-03-10
Having the same problem as below using the build script from the kdenlive forums. Ideas?

> **anewguy said:**
> Okay, since I haven't gotten an answer on any of this yet, I went ahead and did a configure/make/make install of ffmpeg.  I then tried the same on mlt and got the following error in the make:

cc -shared -o ../libmltsox.so factory.o filter_sox.o  -lst -lmad -lvorbisenc -lvorbisfile -logg -lasound -lm -lgsm -lsndfile -lsamplerate -L../../framework -lmlt
/usr/bin/ld: cannot find -lsndfile
collect2: ld returned 1 exit status
make[2]: *** [../libmltsox.so] Error 1
make[2]: Leaving directory `/home/dave/mlt/src/modules/sox'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/dave/mlt/src/modules'
make: *** [all] Error 1

Any help would be greatly appreciated!!  If I can get the above to complete successfully, I think all I have to do then is configure/make/make install of kdenlive in order for the changes to be in place so I can try it out to see if it really fixes the problem.:(

---

### Post by maku-d on 2008-03-10
...and here's a link for anyone who wants to test the script:

[http://www.kdenlive.org/bbforum/viewtopic.php?f=8&t=339&p=1672#p1672]("http://www.kdenlive.org/bbforum/viewtopic.php?f=8&t=339&p=1672#p1672")

---

