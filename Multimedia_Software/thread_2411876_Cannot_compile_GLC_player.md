---
title: "Cannot compile GLC_player"
date: 2019-02-05
forum: Multimedia Software
---

### Post by davidnr on 2019-02-05
Hello,

I need this app to open some CAD files. Libraries GLC_lib were compiled well. I've got a problem with compilation of GLC_player. According to the web page (*[http://www.glc-player.net/download.php?PHPSESSID=f3d38b871eebb5be8dc5a7f8de122c67](http://www.glc-player.net/download.php?PHPSESSID=f3d38b871eebb5be8dc5a7f8de122c67)*), it should be enough if I run following commands inside the folder:

[B][FONT=courier new]qmake
make release[/FONT][/B]

But after the second command I get the message:

[B][FONT=courier new]~/Downloads/GLC_Player_src_2.3.0$ make release
make: *** Keine Regel, um „release“ zu erstellen.  Schluss.[/FONT][/B]

(the message is in German, but I think you know what does it mean)

The same problem I've got with command [FONT=courier new][B]sudo make release

[/B][FONT=arial]It is a Lubuntu 18.10[/FONT][/FONT]

---

### Post by Yellow Pasque on 2019-02-05
Can you give the output of the qmake command?

---

### Post by davidnr on 2019-02-05
There is no output. Just steps into the next line.

---

### Post by mc4man on 2019-02-05
Them just use plain
make

---

### Post by davidnr on 2019-02-06
Here it is:

[B][FONT=courier new]~/Downloads/GLC_Player_src_2.3.0$ make
g++ -c -m64 -pipe -g -Wall -W -D_REENTRANT -DQT_XML_LIB -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I/usr/local/include/GLC_lib -I/usr/X11R6/include -IBuild -IBuild -o Build/main.o main.cpp
In file included from glc_player.h:29,
                 from main.cpp:25:
opengl_view/OpenglView.h:28:10: fatal error: GLC_Viewport: Datei oder Verzeichnis nicht gefunden
 #include <GLC_Viewport>
          ^~~~~~~~~~~~~~
compilation terminated.
make: *** [Makefile:653: Build/main.o] Fehler 1[/FONT][/B]

---

### Post by spjackson on 2019-02-06
> **davidnr said:**
> 
[B][FONT=courier new]~/Downloads/GLC_Player_src_2.3.0$ make
g++ -c -m64 -pipe -g -Wall -W -D_REENTRANT -DQT_XML_LIB -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I[COLOR=#ff0000]/usr/local/include/GLC_lib[/COLOR] -I/usr/X11R6/include -IBuild -IBuild -o Build/main.o main.cpp
In file included from glc_player.h:29,
                 from main.cpp:25:
opengl_view/OpenglView.h:28:10: fatal error: GLC_Viewport: Datei oder Verzeichnis nicht gefunden
 #include <GLC_Viewport>
          ^~~~~~~~~~~~~~
compilation terminated.
make: *** [Makefile:653: Build/main.o] Fehler 1[/FONT][/B]

Do you have the folder I have highlighted?

This page [http://www.glc-player.net/](http://www.glc-player.net/) says that you need GLC_Lib. I'm guessing that's what is supposed to provide /usr/local/include/GLC_lib, although I note that you said "Libraries GLC_lib were compiled well." If you have GLC_Viewport installed somewhere else, you will need to change the INCLUDEPATH in glc_player.pro and re-run qmake.

I note that the source for GLC Player is 7 years old. The source for GLC_lib is 5 years old. I suspect that you might need quite a bit of help to get it built on 18.10.

---

### Post by davidnr on 2019-02-06
You had a right. The path to the GLC_lib was wrong. I had 

[B][FONT=courier new]/usr/local/include/GLC_lib-2.5

[/FONT][/B]and I just removed "-2.5". After that "**[FONT=courier new]make[/FONT]**" command was running well.
After some minutes I've tried once more time "**[FONT=courier new]make release[/FONT]**" - and get the same error: **[FONT=&quot]make: *** Keine Regel, um &#8222;release&#8220; zu erstellen. Schluss.[/FONT]**

---

### Post by davidnr on 2019-02-07
Maybe anyone has an idea which other application can open 3Dxml files?

---

### Post by spjackson on 2019-02-07
> **davidnr said:**
> [B][FONT=courier new]
[/FONT][/B]and I just removed "-2.5". After that "**[FONT=courier new]make[/FONT]**" command was running well.

And did the make complete successfully?
> 
After some minutes I've tried once more time "**[FONT=courier new]make release[/FONT]**" - and get the same error: **[FONT=&amp]make: *** Keine Regel, um „release“ zu erstellen. Schluss.[/FONT]**
qmake creates a Makefile which has no target called release, i.e. it contains no line beginning with
```

release:

```
The instruction to do "make release" is either out of date or has always been wrong on Linux platforms.

If "make" has built the program successfully, there is nothing more to do unless you want to copy the resulting program (and any .so files) to a particular location.

---

### Post by spjackson on 2019-02-07
> **davidnr said:**
> Maybe anyone has an idea which other application can open 3Dxml files?
For Linux, probably not unless Dassault's player works under wine. [https://en.wikipedia.org/wiki/3DXML](https://en.wikipedia.org/wiki/3DXML)

---

### Post by davidnr on 2019-02-08
> **spjackson said:**
> And did the make complete successfully?

qmake creates a Makefile which has no target called release, i.e. it contains no line beginning with
```

release:

```
The instruction to do "make release" is either out of date or has always been wrong on Linux platforms.

If "make" has built the program successfully, there is nothing more to do unless you want to copy the resulting program (and any .so files) to a particular location.

There is a result:

```
~/Downloads/GLC_Player_src_2.3.0$ make
g++ -c -m64 -pipe -g -Wall -W -D_REENTRANT -DQT_XML_LIB -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I/usr/local/include/GLC_lib -I/usr/X11R6/include -IBuild -IBuild -o Build/OpenglView.o opengl_view/OpenglView.cpp
opengl_view/OpenglView.cpp: In constructor ‘OpenglView::OpenglView(QWidget*)’:
opengl_view/OpenglView.cpp:79:25: error: no matching function for call to ‘GLC_Viewport::GLC_Viewport(OpenglView*)’
 , m_CurrentLightIndex(-1)
                         ^
In file included from /usr/local/include/GLC_lib/GLC_Viewport:1,
                 from opengl_view/OpenglView.h:28,
                 from opengl_view/OpenglView.cpp:24:
/usr/local/include/GLC_lib/viewport/glc_viewport.h:72:2: note: candidate: ‘GLC_Viewport::GLC_Viewport()’
  GLC_Viewport();
  ^~~~~~~~~~~~
/usr/local/include/GLC_lib/viewport/glc_viewport.h:72:2: note:   candidate expects 0 arguments, 1 provided
opengl_view/OpenglView.cpp: In member function ‘virtual void OpenglView::paintGL()’:
opengl_view/OpenglView.cpp:516:11: error: ‘class GLC_Light’ has no member named ‘enable’; did you mean ‘disable’?
   m_Light.enable();
           ^~~~~~
           disable
opengl_view/OpenglView.cpp:525:22: error: ‘class GLC_Light’ has no member named ‘enable’; did you mean ‘disable’?
     m_UserLights[i]->enable();
                      ^~~~~~
                      disable
opengl_view/OpenglView.cpp: In member function ‘virtual void OpenglView::mousePressEvent(QMouseEvent*)’:
opengl_view/OpenglView.cpp:705:10: warning: enumeration value ‘VE_NORMAL’ not handled in switch [-Wswitch]
   switch (m_ViewEnterState)
          ^
In file included from /usr/include/qt4/QtGui/qbrush.h:47,
                 from /usr/include/qt4/QtGui/qpalette.h:47,
                 from /usr/include/qt4/QtGui/qwidget.h:50,
                 from /usr/include/qt4/QtOpenGL/qgl.h:45,
                 from /usr/include/qt4/QtOpenGL/QGLWidget:1,
                 from /usr/local/include/GLC_lib/viewport/glc_viewport.h:27,
                 from /usr/local/include/GLC_lib/GLC_Viewport:1,
                 from opengl_view/OpenglView.h:28,
                 from opengl_view/OpenglView.cpp:24:
/usr/include/qt4/QtCore/qvector.h: In instantiation of ‘void QVector<T>::realloc(int, int) [with T = GLC_Matrix4x4]’:
/usr/include/qt4/QtCore/qvector.h:337:3:   required from ‘void QVector<T>::detach_helper() [with T = GLC_Matrix4x4]’
/usr/include/qt4/QtCore/qvector.h:147:45:   required from ‘void QVector<T>::detach() [with T = GLC_Matrix4x4]’
/usr/include/qt4/QtCore/qstack.h:73:31:   required from ‘T& QStack<T>::top() [with T = GLC_Matrix4x4]’
/usr/local/include/GLC_lib/viewport/../sceneGraph/../glc_context.h:81:105:   required from here
/usr/include/qt4/QtCore/qvector.h:503:25: warning: ‘void* memcpy(void*, const void*, size_t)’ writing to an object of type ‘QVector<GLC_Matrix4x4>::Data’ {aka ‘struct QVectorTypedData<GLC_Matrix4x4>’} with no trivial copy-assignment; use copy-assignment or copy-initialization instead [-Wclass-memaccess]
                 ::memcpy(x.p, p, sizeOfTypedData() + (qMin(aalloc, d->alloc) - 1) * sizeof(T));
                 ~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from /usr/include/qt4/QtGui/qbrush.h:47,
                 from /usr/include/qt4/QtGui/qpalette.h:47,
                 from /usr/include/qt4/QtGui/qwidget.h:50,
                 from /usr/include/qt4/QtOpenGL/qgl.h:45,
                 from /usr/include/qt4/QtOpenGL/QGLWidget:1,
                 from /usr/local/include/GLC_lib/viewport/glc_viewport.h:27,
                 from /usr/local/include/GLC_lib/GLC_Viewport:1,
                 from opengl_view/OpenglView.h:28,
                 from opengl_view/OpenglView.cpp:24:
/usr/include/qt4/QtCore/qvector.h:94:8: note: ‘QVector<GLC_Matrix4x4>::Data’ {aka ‘struct QVectorTypedData<GLC_Matrix4x4>’} declared here
 struct QVectorTypedData : private QVectorData
        ^~~~~~~~~~~~~~~~
make: *** [Makefile:875: Build/OpenglView.o] Fehler 1
```

There were some error. But are they important? Or maybe they are only warnings?

Where can I find a result binary (and *.so files) and to which location should I put them?

---

### Post by davidnr on 2019-02-08
> **spjackson said:**
> For Linux, probably not unless Dassault's player works under wine. [https://en.wikipedia.org/wiki/3DXML](https://en.wikipedia.org/wiki/3DXML)

I have also tried to install 3DXML Player under the Wine but with no success. The installation runs, but after 1 sec stops and rolls back. Folders are created:

```
~/.wine/drive_c/Program Files/Dassault Systemes/3D XML Player$ 

```

but content is empty.

---

### Post by spjackson on 2019-02-08
> **davidnr said:**
> 
```
~/Downloads/GLC_Player_src_2.3.0$ make
g++ -c -m64 -pipe -g -Wall -W -D_REENTRANT -DQT_XML_LIB -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I/usr/local/include/GLC_lib -I/usr/X11R6/include -IBuild -IBuild -o Build/OpenglView.o opengl_view/OpenglView.cpp
opengl_view/OpenglView.cpp: In constructor ‘OpenglView::OpenglView(QWidget*)’:
[COLOR=#ff0000]opengl_view/OpenglView.cpp:79:25: error: no matching function for call to ‘GLC_Viewport::GLC_Viewport(OpenglView*)’[/COLOR]
 , m_CurrentLightIndex(-1)
                         ^
In file included from /usr/local/include/GLC_lib/GLC_Viewport:1,
                 from opengl_view/OpenglView.h:28,
                 from opengl_view/OpenglView.cpp:24:
/usr/local/include/GLC_lib/viewport/glc_viewport.h:72:2: note: candidate: ‘GLC_Viewport::GLC_Viewport()’
  GLC_Viewport();
  ^~~~~~~~~~~~
/usr/local/include/GLC_lib/viewport/glc_viewport.h:72:2: note:   candidate expects 0 arguments, 1 provided
opengl_view/OpenglView.cpp: In member function ‘virtual void OpenglView::paintGL()’:
[COLOR=#ff0000]opengl_view/OpenglView.cpp:516:11: error: ‘class GLC_Light’ has no member named ‘enable’; did you mean ‘disable’?[/COLOR]
   m_Light.enable();
           ^~~~~~
           disable
[COLOR=#ff0000]opengl_view/OpenglView.cpp:525:22: error: ‘class GLC_Light’ has no member named ‘enable’; did you mean ‘disable’?[/COLOR]
     m_UserLights[i]->enable();
                      ^~~~~~
                      disable
opengl_view/OpenglView.cpp: In member function ‘virtual void OpenglView::mousePressEvent(QMouseEvent*)’:
opengl_view/OpenglView.cpp:705:10: warning: enumeration value ‘VE_NORMAL’ not handled in switch [-Wswitch]
   switch (m_ViewEnterState)
          ^
In file included from /usr/include/qt4/QtGui/qbrush.h:47,
                 from /usr/include/qt4/QtGui/qpalette.h:47,
                 from /usr/include/qt4/QtGui/qwidget.h:50,
                 from /usr/include/qt4/QtOpenGL/qgl.h:45,
                 from /usr/include/qt4/QtOpenGL/QGLWidget:1,
                 from /usr/local/include/GLC_lib/viewport/glc_viewport.h:27,
                 from /usr/local/include/GLC_lib/GLC_Viewport:1,
                 from opengl_view/OpenglView.h:28,
                 from opengl_view/OpenglView.cpp:24:
/usr/include/qt4/QtCore/qvector.h: In instantiation of ‘void QVector<T>::realloc(int, int) [with T = GLC_Matrix4x4]’:
/usr/include/qt4/QtCore/qvector.h:337:3:   required from ‘void QVector<T>::detach_helper() [with T = GLC_Matrix4x4]’
/usr/include/qt4/QtCore/qvector.h:147:45:   required from ‘void QVector<T>::detach() [with T = GLC_Matrix4x4]’
/usr/include/qt4/QtCore/qstack.h:73:31:   required from ‘T& QStack<T>::top() [with T = GLC_Matrix4x4]’
/usr/local/include/GLC_lib/viewport/../sceneGraph/../glc_context.h:81:105:   required from here
/usr/include/qt4/QtCore/qvector.h:503:25: warning: ‘void* memcpy(void*, const void*, size_t)’ writing to an object of type ‘QVector<GLC_Matrix4x4>::Data’ {aka ‘struct QVectorTypedData<GLC_Matrix4x4>’} with no trivial copy-assignment; use copy-assignment or copy-initialization instead [-Wclass-memaccess]
                 ::memcpy(x.p, p, sizeOfTypedData() + (qMin(aalloc, d->alloc) - 1) * sizeof(T));
                 ~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from /usr/include/qt4/QtGui/qbrush.h:47,
                 from /usr/include/qt4/QtGui/qpalette.h:47,
                 from /usr/include/qt4/QtGui/qwidget.h:50,
                 from /usr/include/qt4/QtOpenGL/qgl.h:45,
                 from /usr/include/qt4/QtOpenGL/QGLWidget:1,
                 from /usr/local/include/GLC_lib/viewport/glc_viewport.h:27,
                 from /usr/local/include/GLC_lib/GLC_Viewport:1,
                 from opengl_view/OpenglView.h:28,
                 from opengl_view/OpenglView.cpp:24:
/usr/include/qt4/QtCore/qvector.h:94:8: note: ‘QVector<GLC_Matrix4x4>::Data’ {aka ‘struct QVectorTypedData<GLC_Matrix4x4>’} declared here
 struct QVectorTypedData : private QVectorData
        ^~~~~~~~~~~~~~~~
make: *** [Makefile:875: Build/OpenglView.o] Fehler 1
```

There were some error. But are they important? Or maybe they are only warnings?

There are 3 fatal errors which I have marked in red. Because of these, make stops and does not produce an executable. The implication is that the GLC Player source that you are using is incompatible with the GLC_lib source that you are using. GLC Player is using aspects of the interface to GLC_lib which the latter does not provide.

I would personally be concerned about the warnings but the warnings do not prevent the build - they may potentially give rise to problems at runtime, or they may be OK.

---

### Post by mc4man on 2019-02-10
The whole project is stagnant, was & is a mess in many ways.
You'd need to match your qt verion with GLC_lib version & that with the GLC_player version. Plus in all cases there are some errors in the .pro or code. 

So the 3.0.1 lib  will build with the next branch of the player (git) & produce a binary in 16.04. However the binary segfaults  so useless.

The 2.5 lib will build with the 2.3.0 version of player and can work, though only in 14.04 it seems. (screens 1 & 2
(- in the lib build example 11 needs an edit as in gedit screen
After installing lib one must run
sudo ldconfig

Doesn't appear any combo will build or run in 18.04.

To see what a mess ck. the github issues on both sources.
[https://github.com/laumaya/GLC_lib/issues](https://github.com/laumaya/GLC_lib/issues)
[https://github.com/laumaya/GLC_Player/issues](https://github.com/laumaya/GLC_Player/issues)

---

### Post by davidnr on 2019-02-11
OK, So I understand, that I can forget about GLC_Player on 18.10.
But what about installing 3DXML Player under the Wine?

---

