---
title: "qkismet compile fails / ubuntu 9.04"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by freeballer on 2009-09-01
I downloaded qkismet src. the package info is fairly simplistic.. no real info for dependancies but I assume I needed qt4, gcc gcc+ but not sure rest as no info is given.. Documentation says:

```
Instructions for building and installing qKismet from source

- Make sure you have Qt >= 4.3

- Run qmake && make release (in src dir) - qKismet's binary will be placed in the build/release directory

- Optionally, run "make install" to install qKismet in /usr/bin directory

```

but when I do it says:

```

qkismet.pro:24: Unknown test function: CONFIG
make: *** No rule to make target `release'.  Stop.

```

not sure what else is needed. there is little else for me to check, and no posts with a safe solution. please help

Thanks
Geo

---

### Post by Bachstelze on 2009-09-01
> **freeballer said:**
> 
but when I do it says:

```

qkismet.pro:24: Unknown test function: CONFIG
make: *** No rule to make target `release'.  Stop.

```

When you do what?

---

### Post by freeballer on 2009-09-01
qmake as per documentation, error is:

```

root@MacBook:/home/freeballer/qkismet-0.1.1/src# qmake -d
DEBUG 1: Resetting dir to: /home/freeballer/qkismet-0.1.1/src/
DEBUG 1: Changing dir to: /home/freeballer/qkismet-0.1.1/src
DEBUG 1: QMAKESPEC conf: reading /usr/share/qt3/mkspecs/default/qmake.conf
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:6 :MAKEFILE_GENERATOR: :=: (UNIX)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:7 :TEMPLATE: :=: (app)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:8 :CONFIG: :+=: (qt :: warn_on :: release :: incremental :: link_prl :: thread)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:9 :QMAKE_INCREMENTAL_STYLE: :=: (sublib)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:11 :QMAKE_CC: :=: (gcc)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:12 :QMAKE_LEX: :=: (flex)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:13 :QMAKE_LEXFLAGS: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:14 :QMAKE_YACC: :=: (yacc)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:15 :QMAKE_YACCFLAGS: :=: (-d)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:16 :QMAKE_YACCFLAGS_MANGLE: :=: (-p :: $base :: -b :: $base)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:17 :QMAKE_YACC_HEADER: :=: ($base.tab.h)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:18 :QMAKE_YACC_SOURCE: :=: ($base.tab.c)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:19 :QMAKE_CFLAGS: :=: (-pipe :: -g)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:20 :QMAKE_CFLAGS_DEPS: :=: (-M)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:21 :QMAKE_CFLAGS_WARN_ON: :=: (-Wall :: -W)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:22 :QMAKE_CFLAGS_WARN_OFF: :=: (-w)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:23 :QMAKE_CFLAGS_RELEASE: :=: (-O2)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:24 :QMAKE_CFLAGS_DEBUG: :=: (-O0)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:25 :QMAKE_CFLAGS_SHLIB: :=: (-fPIC)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:26 :QMAKE_CFLAGS_YACC: :=: (-Wno-unused :: -Wno-parentheses)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:27 :QMAKE_CFLAGS_THREAD: :=: (-D_REENTRANT)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:29 :QMAKE_CXX: :=: (g++)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:30 :QMAKE_CXXFLAGS: :=: (-pipe :: -g)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:31 :QMAKE_CXXFLAGS_DEPS: :=: (-M)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:32 :QMAKE_CXXFLAGS_WARN_ON: :=: (-Wall :: -W)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:33 :QMAKE_CXXFLAGS_WARN_OFF: :=: (-w)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:34 :QMAKE_CXXFLAGS_RELEASE: :=: (-O2)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:35 :QMAKE_CXXFLAGS_DEBUG: :=: (-O0)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:36 :QMAKE_CXXFLAGS_SHLIB: :=: (-fPIC)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:37 :QMAKE_CXXFLAGS_YACC: :=: (-Wno-unused :: -Wno-parentheses)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:38 :QMAKE_CXXFLAGS_THREAD: :=: (-D_REENTRANT)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:40 :QMAKE_INCDIR: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:41 :QMAKE_LIBDIR: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:42 :QMAKE_INCDIR_X11: :=: (/usr/X11R6/include)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:43 :QMAKE_LIBDIR_X11: :=: (/usr/X11R6/lib)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:44 :QMAKE_INCDIR_QT: :=: (/usr/share/qt3/include)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:45 :QMAKE_LIBDIR_QT: :=: (/usr/share/qt3/lib)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:46 :QMAKE_INCDIR_OPENGL: :=: (/usr/X11R6/include)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:47 :QMAKE_LIBDIR_OPENGL: :=: (/usr/X11R6/lib)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:49 :QMAKE_LINK: :=: (g++)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:50 :QMAKE_LINK_SHLIB: :=: (g++)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:51 :QMAKE_LFLAGS: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:52 :QMAKE_LFLAGS_RELEASE: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:53 :QMAKE_LFLAGS_DEBUG: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:54 :QMAKE_LFLAGS_SHLIB: :=: (-shared)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:55 :QMAKE_LFLAGS_PLUGIN: :=: (-shared)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:56 :QMAKE_LFLAGS_SONAME: :=: (-Wl,-soname,)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:57 :QMAKE_LFLAGS_THREAD: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:58 :QMAKE_RPATH: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:60 :QMAKE_LIBS: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:61 :QMAKE_LIBS_DYNLOAD: :=: (-ldl)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:62 :QMAKE_LIBS_X11: :=: (-lXext :: -lX11 :: -lm)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:63 :QMAKE_LIBS_X11SM: :=: (-lSM :: -lICE)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:64 :QMAKE_LIBS_NIS: :=: (-lnsl)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:65 :QMAKE_LIBS_QT: :=: (-lqt)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:66 :QMAKE_LIBS_QT_THREAD: :=: (-lqt-mt)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:67 :QMAKE_LIBS_OPENGL: :=: (-lGLU :: -lGL :: -lXmu)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:68 :QMAKE_LIBS_OPENGL_QT: :=: (-lGL :: -lXmu)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:69 :QMAKE_LIBS_THREAD: :=: (-lpthread)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:71 :QMAKE_MOC: :=: (/usr/share/qt3/bin/moc)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:72 :QMAKE_UIC: :=: (/usr/share/qt3/bin/uic)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:74 :QMAKE_AR: :=: (ar :: cqs)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:75 :QMAKE_RANLIB: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:77 :QMAKE_TAR: :=: (tar :: -cf)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:78 :QMAKE_GZIP: :=: (gzip :: -9f)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:80 :QMAKE_COPY: :=: (cp :: -f)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:81 :QMAKE_COPY_FILE: :=: ($(COPY))
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:82 :QMAKE_COPY_DIR: :=: ($(COPY) :: -r)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:83 :QMAKE_MOVE: :=: (mv :: -f)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:84 :QMAKE_DEL_FILE: :=: (rm :: -f)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:85 :QMAKE_DEL_DIR: :=: (rmdir)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:86 :QMAKE_STRIP: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:87 :QMAKE_STRIPFLAGS_LIB: :+=: (--strip-unneeded)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:88 :QMAKE_CHK_DIR_EXISTS: :=: (test :: -d)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:89 :QMAKE_MKDIR: :=: (mkdir :: -p)
DEBUG 1: Project file: reading qkismet.pro
DEBUG 1: Project Parser: qkismet.pro:5 :TEMPLATE: :=: (app)
DEBUG 1: Project Parser: qkismet.pro:7 :DEPENDPATH: :+=: (.)
DEBUG 1: Project Parser: qkismet.pro:8 :INCLUDEPATH: :+=: (.)
DEBUG 1: Project Parser: qkismet.pro:10 :RESOURCES: :=: (qkismet.qrc)
DEBUG 1: Project Parser: qkismet.pro:12 :target.path: :=: (/usr/bin/)
DEBUG 1: Project Parser: qkismet.pro:13 :INSTALLS: :+=: (target)
DEBUG 1: Project Parser: qkismet.pro:16 :HEADERS: :+=: (headmenu.h :: settings.h :: configdialog.h :: configpages.h :: infoview.h :: graph.h :: kisfilter.h :: netview.h :: kismodel.h :: alertmodel.h :: alertview.h :: kisview.h :: protprops.h :: kisock.h :: main.h :: mwnd.h :: mwtoolbar.h :: viewtoolbar.h :: filteredit.h :: about.h :: netmodel.h :: netitem.h :: statview.h :: statmodel.h :: manuf.h)
DEBUG 1: Project Parser: qkismet.pro:17 :SOURCES: :+=: (headmenu.cpp :: settings.cpp :: configdialog.cpp :: configpages.cpp :: infoview.cpp :: graph.cpp :: kisfilter.cpp :: netmodel.cpp :: netitem.cpp :: netview.cpp :: alertmodel.cpp :: alertview.cpp :: statmodel.cpp :: kisview.cpp :: protprops.cpp :: kisock.cpp :: main.cpp :: mwnd.cpp :: mwtoolbar.cpp :: viewtoolbar.cpp :: filteredit.cpp :: about.cpp :: statview.cpp :: manuf.cpp)
DEBUG 1: Project Parser: qkismet.pro:19 :QT: :+=: (network)
DEBUG 1: Project Parser: qkismet.pro:20 :QMAKE_CXXFLAGS_DEBUG: :+=: (-ggdb)
DEBUG 1: Project Parser: qkismet.pro:21 :CONFIG: :+=: (release)
DEBUG 1: Running project test: CONFIG( debug::debug|release )
qkismet.pro:24: Unknown test function: CONFIG
DEBUG 1: Project Parser: qkismet.pro:24 : Test (CONFIG(debug, debug|release)) failed.
DEBUG 1: Project Parser: qkismet.pro:24 : Entering block 1 (0).
DEBUG 1: Project Parser: qkismet.pro:25 : Ignored due to block being false.
DEBUG 1: Project Parser: qkismet.pro:26 : Ignored due to block being false.
DEBUG 1: Project Parser: qkismet.pro:27 : Ignored due to block being false.
DEBUG 1: Project Parser: qkismet.pro:28 : Ignored due to block being false.
DEBUG 1: Project Parser: qkismet.pro:29 : Leaving block 1
DEBUG 1: Project Parser: qkismet.pro:29 : Else considered.
DEBUG 1: Project Parser: qkismet.pro:29 : Entering block 1 (1).
DEBUG 1: Project Parser: qkismet.pro:30 :DESTDIR: :=: (../build/release)
DEBUG 1: Project Parser: qkismet.pro:31 :OBJECTS_DIR: :=: (../build/release)
DEBUG 1: Project Parser: qkismet.pro:32 :MOC_DIR: :=: (../build/release)
DEBUG 1: Project Parser: qkismet.pro:33 :RCC_DIR: :=: (../build/release)
DEBUG 1: Project Parser: qkismet.pro:34 : Leaving block 1
DEBUG 1: Dependency Directories: .
DEBUG 1: Processing PRL file: /usr/share/qt3/lib/libqt-mt
DEBUG 1: Project file: reading /usr/share/qt3/lib/libqt-mt.prl
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:1 :QMAKE_PRL_BUILD_DIR: :=: (/usr/share/qt3/src)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:2 :QMAKE_PRO_INPUT: :=: (qt.pro)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:3 :QMAKE_PRL_TARGET: :=: (libqt-mt.so.3.3.8)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:4 :QMAKE_PRL_DEFINES: :=: (QT_SHARED :: QT_TABLET_SUPPORT :: QT_NO_DEBUG :: QT_THREAD_SUPPORT)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:5 :QMAKE_PRL_CFLAGS: :=: (-D_REENTRANT)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:6 :QMAKE_PRL_CXXFLAGS: :=: (-D_REENTRANT)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:7 :QMAKE_PRL_CONFIG: :=: (qt :: warn_on :: release :: incremental :: link_prl :: thread :: nocrosscompiler :: dlopen_opengl :: minimal-config :: small-config :: medium-config :: large-config :: full-config :: styles :: tools :: kernel :: widgets :: dialogs :: iconview :: workspace :: inputmethod :: network :: canvas :: table :: xml :: opengl :: sql :: opengl :: release :: dll :: thread :: largefile :: stl :: ipv6 :: system-mng :: system-jpeg :: jpeg :: system-png :: png :: gif :: system-zlib :: nis :: cups :: nas :: bigcodecs :: x11sm :: xshape :: xinerama :: xcursor :: xrandr :: xrender :: xftfreetype :: tablet :: xkb :: inputmethod :: dylib :: create_prl :: link_prl :: qt :: warn_on :: depend_includepath :: qmake_cache :: x11 :: x11inc :: create_libtool :: create_pc :: moc :: x11lib)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:8 :QMAKE_PRL_VERSION: :=: (3.3.8)
DEBUG 1: CONFIG === qt :: warn_on :: release :: incremental :: link_prl :: thread :: release :: moc :: x11lib
DEBUG 1: DEFINES === QT_NO_DEBUG :: QT_THREAD_SUPPORT :: QT_SHARED :: QT_TABLET_SUPPORT
DEBUG 1: DEPENDPATH === .
DEBUG 1: DESTDIR === ../build/release/
DEBUG 1: DISTFILES === /home/freeballer/qkismet-0.1.1/src/qkismet.pro
DEBUG 1: HEADERS === headmenu.h :: settings.h :: configdialog.h :: configpages.h :: infoview.h :: graph.h :: kisfilter.h :: netview.h :: kismodel.h :: alertmodel.h :: alertview.h :: kisview.h :: protprops.h :: kisock.h :: main.h :: mwnd.h :: mwtoolbar.h :: viewtoolbar.h :: filteredit.h :: about.h :: netmodel.h :: netitem.h :: statview.h :: statmodel.h :: manuf.h
DEBUG 1: INCLUDEPATH === . :: /usr/include/qt3 :: ../build/release/
DEBUG 1: INSTALLS === target
DEBUG 1: MAKEFILE_GENERATOR === UNIX
DEBUG 1: MOC_DIR === ../build/release/
DEBUG 1: OBJECTS === ../build/release/headmenu.o :: ../build/release/settings.o :: ../build/release/configdialog.o :: ../build/release/configpages.o :: ../build/release/infoview.o :: ../build/release/graph.o :: ../build/release/kisfilter.o :: ../build/release/netmodel.o :: ../build/release/netitem.o :: ../build/release/netview.o :: ../build/release/alertmodel.o :: ../build/release/alertview.o :: ../build/release/statmodel.o :: ../build/release/kisview.o :: ../build/release/protprops.o :: ../build/release/kisock.o :: ../build/release/main.o :: ../build/release/mwnd.o :: ../build/release/mwtoolbar.o :: ../build/release/viewtoolbar.o :: ../build/release/filteredit.o :: ../build/release/about.o :: ../build/release/statview.o :: ../build/release/manuf.o
DEBUG 1: OBJECTS_DIR === ../build/release/
DEBUG 1: OBJMOC === ../build/release/moc_headmenu.o :: ../build/release/moc_configdialog.o :: ../build/release/moc_infoview.o :: ../build/release/moc_graph.o :: ../build/release/moc_kisfilter.o :: ../build/release/moc_netview.o :: ../build/release/moc_alertmodel.o :: ../build/release/moc_alertview.o :: ../build/release/moc_kisview.o :: ../build/release/moc_kisock.o :: ../build/release/moc_main.o :: ../build/release/moc_mwnd.o :: ../build/release/moc_mwtoolbar.o :: ../build/release/moc_viewtoolbar.o :: ../build/release/moc_filteredit.o :: ../build/release/moc_about.o :: ../build/release/moc_netmodel.o :: ../build/release/moc_statview.o :: ../build/release/moc_statmodel.o
DEBUG 1: PRL_EXPORT_CFLAGS === -D_REENTRANT
DEBUG 1: PRL_EXPORT_CXXFLAGS === -D_REENTRANT
DEBUG 1: QMAKE_APP_FLAG === 1
DEBUG 1: QMAKE_AR === ar :: cqs
DEBUG 1: QMAKE_CC === gcc
DEBUG 1: QMAKE_CFLAGS === -pipe :: -g :: -Wall :: -W :: -O2 :: -D_REENTRANT
DEBUG 1: QMAKE_CFLAGS_DEBUG === -O0
DEBUG 1: QMAKE_CFLAGS_DEPS === -M
DEBUG 1: QMAKE_CFLAGS_PRECOMPILE === -x c-header -c
DEBUG 1: QMAKE_CFLAGS_RELEASE === -O2
DEBUG 1: QMAKE_CFLAGS_SHLIB === -fPIC
DEBUG 1: QMAKE_CFLAGS_THREAD === -D_REENTRANT
DEBUG 1: QMAKE_CFLAGS_USE_PRECOMPILE === -include
DEBUG 1: QMAKE_CFLAGS_WARN_OFF === -w
DEBUG 1: QMAKE_CFLAGS_WARN_ON === -Wall :: -W
DEBUG 1: QMAKE_CFLAGS_YACC === -Wno-unused :: -Wno-parentheses
DEBUG 1: QMAKE_CHK_DIR_EXISTS === test :: -d
DEBUG 1: QMAKE_COPY === cp :: -f
DEBUG 1: QMAKE_COPY_DIR === $(COPY) :: -r
DEBUG 1: QMAKE_COPY_FILE === $(COPY)
DEBUG 1: QMAKE_CXX === g++
DEBUG 1: QMAKE_CXXFLAGS === -pipe :: -g :: -Wall :: -W :: -O2 :: -D_REENTRANT
DEBUG 1: QMAKE_CXXFLAGS_DEBUG === -O0 :: -ggdb
DEBUG 1: QMAKE_CXXFLAGS_DEPS === -M
DEBUG 1: QMAKE_CXXFLAGS_PRECOMPILE === -x c++-header -c
DEBUG 1: QMAKE_CXXFLAGS_RELEASE === -O2
DEBUG 1: QMAKE_CXXFLAGS_SHLIB === -fPIC
DEBUG 1: QMAKE_CXXFLAGS_THREAD === -D_REENTRANT
DEBUG 1: QMAKE_CXXFLAGS_WARN_OFF === -w
DEBUG 1: QMAKE_CXXFLAGS_WARN_ON === -Wall :: -W
DEBUG 1: QMAKE_CXXFLAGS_YACC === -Wno-unused :: -Wno-parentheses
DEBUG 1: QMAKE_DEL_DIR === rmdir
DEBUG 1: QMAKE_DEL_FILE === rm :: -f
DEBUG 1: QMAKE_EXTENSION_PLUGIN === so
DEBUG 1: QMAKE_EXTENSION_SHLIB === so
DEBUG 1: QMAKE_EXT_CPP === .cpp :: .cc :: .cxx :: .C
DEBUG 1: QMAKE_EXT_H === .h :: .hpp :: .hh :: .H :: .hxx
DEBUG 1: QMAKE_FILETAGS ===
DEBUG 1: QMAKE_GZIP === gzip :: -9f
DEBUG 1: QMAKE_INCDIR_OPENGL === /usr/X11R6/include
DEBUG 1: QMAKE_INCDIR_QT === /usr/share/qt3/include
DEBUG 1: QMAKE_INCDIR_X11 === /usr/X11R6/include
DEBUG 1: QMAKE_INCREMENTAL_STYLE === sublib
DEBUG 1: QMAKE_INSTALL_DIR === $(COPY_DIR)
DEBUG 1: QMAKE_INSTALL_FILE === $(COPY_FILE)
DEBUG 1: QMAKE_INTERNAL_INCLUDED_FILES === /usr/share/qt3/lib/libqt-mt.prl
DEBUG 1: QMAKE_INTERNAL_PRL_LIBS === QMAKE_LIBDIR_FLAGS :: QMAKE_LIBS
DEBUG 1: QMAKE_LEX === flex
DEBUG 1: QMAKE_LFLAGS_PLUGIN === -shared
DEBUG 1: QMAKE_LFLAGS_SHLIB === -shared
DEBUG 1: QMAKE_LFLAGS_SONAME === -Wl,-soname,
DEBUG 1: QMAKE_LIBDIR_FLAGS === -L/usr/share/qt3/lib :: -L/usr/X11R6/lib
DEBUG 1: QMAKE_LIBDIR_OPENGL === /usr/X11R6/lib
DEBUG 1: QMAKE_LIBDIR_QT === /usr/share/qt3/lib
DEBUG 1: QMAKE_LIBDIR_X11 === /usr/X11R6/lib
DEBUG 1: QMAKE_LIBS === -lqt-mt :: -lXext :: -lX11 :: -lm :: -lpthread
DEBUG 1: QMAKE_LIBS_DYNLOAD === -ldl
DEBUG 1: QMAKE_LIBS_NIS === -lnsl
DEBUG 1: QMAKE_LIBS_OPENGL === -lGLU :: -lGL :: -lXmu
DEBUG 1: QMAKE_LIBS_OPENGL_QT === -lGL :: -lXmu
DEBUG 1: QMAKE_LIBS_QT === -lqt
DEBUG 1: QMAKE_LIBS_QT_THREAD === -lqt-mt
DEBUG 1: QMAKE_LIBS_THREAD === -lpthread
DEBUG 1: QMAKE_LIBS_X11 === -lXext :: -lX11 :: -lm
DEBUG 1: QMAKE_LIBS_X11SM === -lSM :: -lICE
DEBUG 1: QMAKE_LIBTOOL === libtool --silent
DEBUG 1: QMAKE_LINK === g++
DEBUG 1: QMAKE_LINK_SHLIB === g++
DEBUG 1: QMAKE_MAKEFILE === /home/freeballer/qkismet-0.1.1/src/Makefile
DEBUG 1: QMAKE_MKDIR === mkdir :: -p
DEBUG 1: QMAKE_MOC === /usr/share/qt3/bin/moc
DEBUG 1: QMAKE_MOVE === mv :: -f
DEBUG 1: QMAKE_ORIG_DESTDIR === ../build/release
DEBUG 1: QMAKE_ORIG_TARGET === qkismet
DEBUG 1: QMAKE_PRL_INTERNAL_FILES === /usr/share/qt3/lib/libqt-mt.prl
DEBUG 1: QMAKE_RUN_CC === $(CC) -c $(CFLAGS) $(INCPATH) -o $obj $src
DEBUG 1: QMAKE_RUN_CC_IMP === $(CC) -c $(CFLAGS) $(INCPATH) -o $@ $<
DEBUG 1: QMAKE_RUN_CXX === $(CXX) -c $(CXXFLAGS) $(INCPATH) -o $obj $src
DEBUG 1: QMAKE_RUN_CXX_IMP === $(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<
DEBUG 1: QMAKE_STRIPFLAGS_LIB === --strip-unneeded
DEBUG 1: QMAKE_SYMBOLIC_LINK === ln -sf
DEBUG 1: QMAKE_TAR === tar :: -cf
DEBUG 1: QMAKE_UIC === /usr/share/qt3/bin/uic
DEBUG 1: QMAKE_YACC === yacc
DEBUG 1: QMAKE_YACCFLAGS === -d
DEBUG 1: QMAKE_YACCFLAGS_MANGLE === -p :: $base :: -b :: $base
DEBUG 1: QMAKE_YACC_HEADER === $base.tab.h
DEBUG 1: QMAKE_YACC_SOURCE === $base.tab.c
DEBUG 1: QT === network
DEBUG 1: RCC_DIR === ../build/release
DEBUG 1: RESOURCES === qkismet.qrc
DEBUG 1: SOURCES === headmenu.cpp :: settings.cpp :: configdialog.cpp :: configpages.cpp :: infoview.cpp :: graph.cpp :: kisfilter.cpp :: netmodel.cpp :: netitem.cpp :: netview.cpp :: alertmodel.cpp :: alertview.cpp :: statmodel.cpp :: kisview.cpp :: protprops.cpp :: kisock.cpp :: main.cpp :: mwnd.cpp :: mwtoolbar.cpp :: viewtoolbar.cpp :: filteredit.cpp :: about.cpp :: statview.cpp :: manuf.cpp
DEBUG 1: SRCMOC === ../build/release/moc_headmenu.cpp :: ../build/release/moc_configdialog.cpp :: ../build/release/moc_infoview.cpp :: ../build/release/moc_graph.cpp :: ../build/release/moc_kisfilter.cpp :: ../build/release/moc_netview.cpp :: ../build/release/moc_alertmodel.cpp :: ../build/release/moc_alertview.cpp :: ../build/release/moc_kisview.cpp :: ../build/release/moc_kisock.cpp :: ../build/release/moc_main.cpp :: ../build/release/moc_mwnd.cpp :: ../build/release/moc_mwtoolbar.cpp :: ../build/release/moc_viewtoolbar.cpp :: ../build/release/moc_filteredit.cpp :: ../build/release/moc_about.cpp :: ../build/release/moc_netmodel.cpp :: ../build/release/moc_statview.cpp :: ../build/release/moc_statmodel.cpp
DEBUG 1: TARGET === ../build/release/qkismet
DEBUG 1: TEMPLATE === app
DEBUG 1: VERSION === 1.0.0
DEBUG 1: VER_MAJ === 1
DEBUG 1: VER_MIN === 0
DEBUG 1: VER_PAT === 0
DEBUG 1: _HDRMOC === ../build/release/moc_headmenu.cpp :: ../build/release/moc_configdialog.cpp :: ../build/release/moc_infoview.cpp :: ../build/release/moc_graph.cpp :: ../build/release/moc_kisfilter.cpp :: ../build/release/moc_netview.cpp :: ../build/release/moc_alertmodel.cpp :: ../build/release/moc_alertview.cpp :: ../build/release/moc_kisview.cpp :: ../build/release/moc_kisock.cpp :: ../build/release/moc_main.cpp :: ../build/release/moc_mwnd.cpp :: ../build/release/moc_mwtoolbar.cpp :: ../build/release/moc_viewtoolbar.cpp :: ../build/release/moc_filteredit.cpp :: ../build/release/moc_about.cpp :: ../build/release/moc_netmodel.cpp :: ../build/release/moc_statview.cpp :: ../build/release/moc_statmodel.cpp
DEBUG 1: target.path === /usr/bin/
DEBUG 1: target.uninstall === -$(DEL_FILE) "$(INSTALL_ROOT)/usr/bin/$(QMAKE_TARGET)"


```

---

### Post by Bachstelze on 2009-09-01
And what does make release output?

---

### Post by freeballer on 2009-09-01
let me double check when I reboot. there was an error afterwards... I need to reboot into ubuntu later when I feel better



make: *** No rule to make target `release'.  Stop.

---

### Post by psmecker on 2009-09-02
Same Error with app after reboot[

```
[root@bt4-desktop:~/qk/qkismet-0.1.1/src# qmake -d
DEBUG 1: Resetting dir to: /root/qk/qkismet-0.1.1/src/
DEBUG 1: Changing dir to: /root/qk/qkismet-0.1.1/src
DEBUG 1: QMAKESPEC conf: reading /usr/share/qt3/mkspecs/default/qmake.conf
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:6 :MAKEFILE_G
ENERATOR: :=: (UNIX)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:7 :TEMPLATE:
:=: (app)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:8 :CONFIG: :+
=: (qt :: warn_on :: release :: incremental :: link_prl :: thread)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:9 :QMAKE_INCR
EMENTAL_STYLE: :=: (sublib)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:11 :QMAKE_CC:
 :=: (gcc)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:12 :QMAKE_LEX
: :=: (flex)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:13 :QMAKE_LEX
FLAGS: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:14 :QMAKE_YAC
C: :=: (yacc)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:15 :QMAKE_YAC
CFLAGS: :=: (-d)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:16 :QMAKE_YAC
CFLAGS_MANGLE: :=: (-p :: $base :: -b :: $base)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:17 :QMAKE_YAC
C_HEADER: :=: ($base.tab.h)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:18 :QMAKE_YAC
C_SOURCE: :=: ($base.tab.c)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:19 :QMAKE_CFL
AGS: :=: (-pipe :: -g)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:20 :QMAKE_CFL
AGS_DEPS: :=: (-M)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:21 :QMAKE_CFL
AGS_WARN_ON: :=: (-Wall :: -W)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:22 :QMAKE_CFL
AGS_WARN_OFF: :=: (-w)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:23 :QMAKE_CFL
AGS_RELEASE: :=: (-O2)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:24 :QMAKE_CFL
AGS_DEBUG: :=: (-O0)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:25 :QMAKE_CFL
AGS_SHLIB: :=: (-fPIC)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:26 :QMAKE_CFL
AGS_YACC: :=: (-Wno-unused :: -Wno-parentheses)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:27 :QMAKE_CFL
AGS_THREAD: :=: (-D_REENTRANT)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:29 :QMAKE_CXX
: :=: (g++)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:30 :QMAKE_CXX
FLAGS: :=: (-pipe :: -g)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:31 :QMAKE_CXX
FLAGS_DEPS: :=: (-M)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:32 :QMAKE_CXX
FLAGS_WARN_ON: :=: (-Wall :: -W)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:33 :QMAKE_CXX
FLAGS_WARN_OFF: :=: (-w)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:34 :QMAKE_CXX
FLAGS_RELEASE: :=: (-O2)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:35 :QMAKE_CXX
FLAGS_DEBUG: :=: (-O0)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:36 :QMAKE_CXX
FLAGS_SHLIB: :=: (-fPIC)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:37 :QMAKE_CXX
FLAGS_YACC: :=: (-Wno-unused :: -Wno-parentheses)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:38 :QMAKE_CXX
FLAGS_THREAD: :=: (-D_REENTRANT)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:40 :QMAKE_INC
DIR: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:41 :QMAKE_LIB
DIR: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:42 :QMAKE_INC
DIR_X11: :=: (/usr/X11R6/include)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:43 :QMAKE_LIB
DIR_X11: :=: (/usr/X11R6/lib)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:44 :QMAKE_INC
DIR_QT: :=: (/usr/share/qt3/include)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:45 :QMAKE_LIB
DIR_QT: :=: (/usr/share/qt3/lib)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:46 :QMAKE_INC
DIR_OPENGL: :=: (/usr/X11R6/include)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:47 :QMAKE_LIB
DIR_OPENGL: :=: (/usr/X11R6/lib)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:49 :QMAKE_LIN
K: :=: (g++)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:50 :QMAKE_LIN
K_SHLIB: :=: (g++)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:51 :QMAKE_LFL
AGS: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:52 :QMAKE_LFL
AGS_RELEASE: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:53 :QMAKE_LFL
AGS_DEBUG: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:54 :QMAKE_LFL
AGS_SHLIB: :=: (-shared)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:55 :QMAKE_LFL
AGS_PLUGIN: :=: (-shared)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:56 :QMAKE_LFL
AGS_SONAME: :=: (-Wl,-soname,)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:57 :QMAKE_LFL
AGS_THREAD: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:58 :QMAKE_RPA
TH: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:60 :QMAKE_LIB
S: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:61 :QMAKE_LIB
S_DYNLOAD: :=: (-ldl)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:62 :QMAKE_LIB
S_X11: :=: (-lXext :: -lX11 :: -lm)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:63 :QMAKE_LIB
S_X11SM: :=: (-lSM :: -lICE)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:64 :QMAKE_LIB
S_NIS: :=: (-lnsl)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:65 :QMAKE_LIB
S_QT: :=: (-lqt)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:66 :QMAKE_LIB
S_QT_THREAD: :=: (-lqt-mt)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:67 :QMAKE_LIB
S_OPENGL: :=: (-lGLU :: -lGL :: -lXmu)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:68 :QMAKE_LIB
S_OPENGL_QT: :=: (-lGL :: -lXmu)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:69 :QMAKE_LIB
S_THREAD: :=: (-lpthread)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:71 :QMAKE_MOC
: :=: (/usr/share/qt3/bin/moc)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:72 :QMAKE_UIC
: :=: (/usr/share/qt3/bin/uic)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:74 :QMAKE_AR:
 :=: (ar :: cqs)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:75 :QMAKE_RAN
LIB: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:77 :QMAKE_TAR
: :=: (tar :: -cf)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:78 :QMAKE_GZI
P: :=: (gzip :: -9f)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:80 :QMAKE_COP
Y: :=: (cp :: -f)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:81 :QMAKE_COP
Y_FILE: :=: ($(COPY))
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:82 :QMAKE_COP
Y_DIR: :=: ($(COPY) :: -r)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:83 :QMAKE_MOV
E: :=: (mv :: -f)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:84 :QMAKE_DEL
_FILE: :=: (rm :: -f)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:85 :QMAKE_DEL
_DIR: :=: (rmdir)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:86 :QMAKE_STR
IP: :=: ()
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:87 :QMAKE_STR
IPFLAGS_LIB: :+=: (--strip-unneeded)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:88 :QMAKE_CHK
_DIR_EXISTS: :=: (test :: -d)
DEBUG 1: Project Parser: /usr/share/qt3/mkspecs/default/qmake.conf:89 :QMAKE_MKD
IR: :=: (mkdir :: -p)
DEBUG 1: Project file: reading qkismet.pro
DEBUG 1: Project Parser: qkismet.pro:5 :TEMPLATE: :=: (app)
DEBUG 1: Project Parser: qkismet.pro:7 :DEPENDPATH: :+=: (.)
DEBUG 1: Project Parser: qkismet.pro:8 :INCLUDEPATH: :+=: (.)
DEBUG 1: Project Parser: qkismet.pro:10 :RESOURCES: :=: (qkismet.qrc)
DEBUG 1: Project Parser: qkismet.pro:12 :target.path: :=: (/usr/bin/)
DEBUG 1: Project Parser: qkismet.pro:13 :INSTALLS: :+=: (target)
DEBUG 1: Project Parser: qkismet.pro:16 :HEADERS: :+=: (headmenu.h :: settings.h
 :: configdialog.h :: configpages.h :: infoview.h :: graph.h :: kisfilter.h :: n
etview.h :: kismodel.h :: alertmodel.h :: alertview.h :: kisview.h :: protprops.
h :: kisock.h :: main.h :: mwnd.h :: mwtoolbar.h :: viewtoolbar.h :: filteredit.
h :: about.h :: netmodel.h :: netitem.h :: statview.h :: statmodel.h :: manuf.h)
DEBUG 1: Project Parser: qkismet.pro:17 :SOURCES: :+=: (headmenu.cpp :: settings
.cpp :: configdialog.cpp :: configpages.cpp :: infoview.cpp :: graph.cpp :: kisf
ilter.cpp :: netmodel.cpp :: netitem.cpp :: netview.cpp :: alertmodel.cpp :: ale
rtview.cpp :: statmodel.cpp :: kisview.cpp :: protprops.cpp :: kisock.cpp :: mai
n.cpp :: mwnd.cpp :: mwtoolbar.cpp :: viewtoolbar.cpp :: filteredit.cpp :: about
.cpp :: statview.cpp :: manuf.cpp)
DEBUG 1: Project Parser: qkismet.pro:19 :QT: :+=: (network)
DEBUG 1: Project Parser: qkismet.pro:20 :QMAKE_CXXFLAGS_DEBUG: :+=: (-ggdb)
DEBUG 1: Project Parser: qkismet.pro:21 :CONFIG: :+=: (release)
DEBUG 1: Running project test: CONFIG( debug::debug|release )
qkismet.pro:24: Unknown test function: CONFIG
DEBUG 1: Project Parser: qkismet.pro:24 : Test (CONFIG(debug, debug|release)) fa
iled.
DEBUG 1: Project Parser: qkismet.pro:24 : Entering block 1 (0).
DEBUG 1: Project Parser: qkismet.pro:25 : Ignored due to block being false.
DEBUG 1: Project Parser: qkismet.pro:26 : Ignored due to block being false.
DEBUG 1: Project Parser: qkismet.pro:27 : Ignored due to block being false.
DEBUG 1: Project Parser: qkismet.pro:28 : Ignored due to block being false.
DEBUG 1: Project Parser: qkismet.pro:29 : Leaving block 1
DEBUG 1: Project Parser: qkismet.pro:29 : Else considered.
DEBUG 1: Project Parser: qkismet.pro:29 : Entering block 1 (1).
DEBUG 1: Project Parser: qkismet.pro:30 :DESTDIR: :=: (../build/release)
DEBUG 1: Project Parser: qkismet.pro:31 :OBJECTS_DIR: :=: (../build/release)
DEBUG 1: Project Parser: qkismet.pro:32 :MOC_DIR: :=: (../build/release)
DEBUG 1: Project Parser: qkismet.pro:33 :RCC_DIR: :=: (../build/release)
DEBUG 1: Project Parser: qkismet.pro:34 : Leaving block 1
DEBUG 1: Dependency Directories: .
DEBUG 1: Processing PRL file: /usr/share/qt3/lib/libqt-mt
DEBUG 1: Project file: reading /usr/share/qt3/lib/libqt-mt.prl
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:1 :QMAKE_PRL_BUILD_DIR:
 :=: (/usr/share/qt3/src)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:2 :QMAKE_PRO_INPUT: :=:
 (qt.pro)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:3 :QMAKE_PRL_TARGET: :=
: (libqt-mt.so.3.3.8)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:4 :QMAKE_PRL_DEFINES: :
=: (QT_SHARED :: QT_TABLET_SUPPORT :: QT_NO_DEBUG :: QT_THREAD_SUPPORT)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:5 :QMAKE_PRL_CFLAGS: :=
: (-D_REENTRANT)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:6 :QMAKE_PRL_CXXFLAGS:
:=: (-D_REENTRANT)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:7 :QMAKE_PRL_CONFIG: :=
: (qt :: warn_on :: release :: incremental :: link_prl :: thread :: nocrosscompi
ler :: dlopen_opengl :: minimal-config :: small-config :: medium-config :: large
-config :: full-config :: styles :: tools :: kernel :: widgets :: dialogs :: ico
nview :: workspace :: inputmethod :: network :: canvas :: table :: xml :: opengl
 :: sql :: opengl :: release :: dll :: thread :: largefile :: stl :: ipv6 :: sys
tem-mng :: system-jpeg :: jpeg :: system-png :: png :: gif :: system-zlib :: nis
 :: cups :: nas :: bigcodecs :: x11sm :: xshape :: xinerama :: xcursor :: xrandr
 :: xrender :: xftfreetype :: tablet :: xkb :: inputmethod :: dylib :: create_pr
l :: link_prl :: qt :: warn_on :: depend_includepath :: qmake_cache :: x11 :: x1
1inc :: create_libtool :: create_pc :: moc :: x11lib)
DEBUG 1: Project Parser: /usr/share/qt3/lib/libqt-mt.prl:8 :QMAKE_PRL_VERSION: :
=: (3.3.8)
DEBUG 1: CONFIG === qt :: warn_on :: release :: incremental :: link_prl :: threa
d :: release :: moc :: x11lib
DEBUG 1: DEFINES === QT_NO_DEBUG :: QT_THREAD_SUPPORT :: QT_SHARED :: QT_TABLET_
SUPPORT
DEBUG 1: DEPENDPATH === .
DEBUG 1: DESTDIR === ../build/release/
DEBUG 1: DISTFILES === /root/qk/qkismet-0.1.1/src/qkismet.pro
DEBUG 1: HEADERS === headmenu.h :: settings.h :: configdialog.h :: configpages.h
 :: infoview.h :: graph.h :: kisfilter.h :: netview.h :: kismodel.h :: alertmode
l.h :: alertview.h :: kisview.h :: protprops.h :: kisock.h :: main.h :: mwnd.h :
: mwtoolbar.h :: viewtoolbar.h :: filteredit.h :: about.h :: netmodel.h :: netit
em.h :: statview.h :: statmodel.h :: manuf.h
DEBUG 1: INCLUDEPATH === . :: /usr/include/qt3 :: ../build/release/
DEBUG 1: INSTALLS === target
DEBUG 1: MAKEFILE_GENERATOR === UNIX
DEBUG 1: MOC_DIR === ../build/release/
DEBUG 1: OBJECTS === ../build/release/headmenu.o :: ../build/release/settings.o
:: ../build/release/configdialog.o :: ../build/release/configpages.o :: ../build
/release/infoview.o :: ../build/release/graph.o :: ../build/release/kisfilter.o
:: ../build/release/netmodel.o :: ../build/release/netitem.o :: ../build/release
/netview.o :: ../build/release/alertmodel.o :: ../build/release/alertview.o :: .
./build/release/statmodel.o :: ../build/release/kisview.o :: ../build/release/pr
otprops.o :: ../build/release/kisock.o :: ../build/release/main.o :: ../build/re
lease/mwnd.o :: ../build/release/mwtoolbar.o :: ../build/release/viewtoolbar.o :
: ../build/release/filteredit.o :: ../build/release/about.o :: ../build/release/
statview.o :: ../build/release/manuf.o
DEBUG 1: OBJECTS_DIR === ../build/release/
DEBUG 1: OBJMOC === ../build/release/moc_headmenu.o :: ../build/release/moc_conf
igdialog.o :: ../build/release/moc_infoview.o :: ../build/release/moc_graph.o ::
 ../build/release/moc_kisfilter.o :: ../build/release/moc_netview.o :: ../build/
release/moc_alertmodel.o :: ../build/release/moc_alertview.o :: ../build/release
/moc_kisview.o :: ../build/release/moc_kisock.o :: ../build/release/moc_main.o :
: ../build/release/moc_mwnd.o :: ../build/release/moc_mwtoolbar.o :: ../build/re
lease/moc_viewtoolbar.o :: ../build/release/moc_filteredit.o :: ../build/release
/moc_about.o :: ../build/release/moc_netmodel.o :: ../build/release/moc_statview
.o :: ../build/release/moc_statmodel.o
DEBUG 1: PRL_EXPORT_CFLAGS === -D_REENTRANT
DEBUG 1: PRL_EXPORT_CXXFLAGS === -D_REENTRANT
DEBUG 1: QMAKE_APP_FLAG === 1
DEBUG 1: QMAKE_AR === ar :: cqs
DEBUG 1: QMAKE_CC === gcc
DEBUG 1: QMAKE_CFLAGS === -pipe :: -g :: -Wall :: -W :: -O2 :: -D_REENTRANT
DEBUG 1: QMAKE_CFLAGS_DEBUG === -O0
DEBUG 1: QMAKE_CFLAGS_DEPS === -M
DEBUG 1: QMAKE_CFLAGS_PRECOMPILE === -x c-header -c
DEBUG 1: QMAKE_CFLAGS_RELEASE === -O2
DEBUG 1: QMAKE_CFLAGS_SHLIB === -fPIC
DEBUG 1: QMAKE_CFLAGS_THREAD === -D_REENTRANT
DEBUG 1: QMAKE_CFLAGS_USE_PRECOMPILE === -include
DEBUG 1: QMAKE_CFLAGS_WARN_OFF === -w
DEBUG 1: QMAKE_CFLAGS_WARN_ON === -Wall :: -W
DEBUG 1: QMAKE_CFLAGS_YACC === -Wno-unused :: -Wno-parentheses
DEBUG 1: QMAKE_CHK_DIR_EXISTS === test :: -d
DEBUG 1: QMAKE_COPY === cp :: -f
DEBUG 1: QMAKE_COPY_DIR === $(COPY) :: -r
DEBUG 1: QMAKE_COPY_FILE === $(COPY)
DEBUG 1: QMAKE_CXX === g++
DEBUG 1: QMAKE_CXXFLAGS === -pipe :: -g :: -Wall :: -W :: -O2 :: -D_REENTRANT
DEBUG 1: QMAKE_CXXFLAGS_DEBUG === -O0 :: -ggdb
DEBUG 1: QMAKE_CXXFLAGS_DEPS === -M
DEBUG 1: QMAKE_CXXFLAGS_PRECOMPILE === -x c++-header -c
DEBUG 1: QMAKE_CXXFLAGS_RELEASE === -O2
DEBUG 1: QMAKE_CXXFLAGS_SHLIB === -fPIC
DEBUG 1: QMAKE_CXXFLAGS_THREAD === -D_REENTRANT
DEBUG 1: QMAKE_CXXFLAGS_WARN_OFF === -w
DEBUG 1: QMAKE_CXXFLAGS_WARN_ON === -Wall :: -W
DEBUG 1: QMAKE_CXXFLAGS_YACC === -Wno-unused :: -Wno-parentheses
DEBUG 1: QMAKE_DEL_DIR === rmdir
DEBUG 1: QMAKE_DEL_FILE === rm :: -f
DEBUG 1: QMAKE_EXTENSION_PLUGIN === so
DEBUG 1: QMAKE_EXTENSION_SHLIB === so
DEBUG 1: QMAKE_EXT_CPP === .cpp :: .cc :: .cxx :: .C
DEBUG 1: QMAKE_EXT_H === .h :: .hpp :: .hh :: .H :: .hxx
DEBUG 1: QMAKE_FILETAGS ===
DEBUG 1: QMAKE_GZIP === gzip :: -9f
DEBUG 1: QMAKE_INCDIR_OPENGL === /usr/X11R6/include
DEBUG 1: QMAKE_INCDIR_QT === /usr/share/qt3/include
DEBUG 1: QMAKE_INCDIR_X11 === /usr/X11R6/include
DEBUG 1: QMAKE_INCREMENTAL_STYLE === sublib
DEBUG 1: QMAKE_INSTALL_DIR === $(COPY_DIR)
DEBUG 1: QMAKE_INSTALL_FILE === $(COPY_FILE)
DEBUG 1: QMAKE_INTERNAL_INCLUDED_FILES === /usr/share/qt3/lib/libqt-mt.prl
DEBUG 1: QMAKE_INTERNAL_PRL_LIBS === QMAKE_LIBDIR_FLAGS :: QMAKE_LIBS
DEBUG 1: QMAKE_LEX === flex
DEBUG 1: QMAKE_LFLAGS_PLUGIN === -shared
DEBUG 1: QMAKE_LFLAGS_SHLIB === -shared
DEBUG 1: QMAKE_LFLAGS_SONAME === -Wl,-soname,
DEBUG 1: QMAKE_LIBDIR_FLAGS === -L/usr/share/qt3/lib :: -L/usr/X11R6/lib
DEBUG 1: QMAKE_LIBDIR_OPENGL === /usr/X11R6/lib
DEBUG 1: QMAKE_LIBDIR_QT === /usr/share/qt3/lib
DEBUG 1: QMAKE_LIBDIR_X11 === /usr/X11R6/lib
DEBUG 1: QMAKE_LIBS === -lqt-mt :: -lXext :: -lX11 :: -lm :: -lpthread
DEBUG 1: QMAKE_LIBS_DYNLOAD === -ldl
DEBUG 1: QMAKE_LIBS_NIS === -lnsl
DEBUG 1: QMAKE_LIBS_OPENGL === -lGLU :: -lGL :: -lXmu
DEBUG 1: QMAKE_LIBS_OPENGL_QT === -lGL :: -lXmu
DEBUG 1: QMAKE_LIBS_QT === -lqt
DEBUG 1: QMAKE_LIBS_QT_THREAD === -lqt-mt
DEBUG 1: QMAKE_LIBS_THREAD === -lpthread
DEBUG 1: QMAKE_LIBS_X11 === -lXext :: -lX11 :: -lm
DEBUG 1: QMAKE_LIBS_X11SM === -lSM :: -lICE
DEBUG 1: QMAKE_LIBTOOL === libtool --silent
DEBUG 1: QMAKE_LINK === g++
DEBUG 1: QMAKE_LINK_SHLIB === g++
DEBUG 1: QMAKE_MAKEFILE === /root/qk/qkismet-0.1.1/src/Makefile
DEBUG 1: QMAKE_MKDIR === mkdir :: -p
DEBUG 1: QMAKE_MOC === /usr/share/qt3/bin/moc
DEBUG 1: QMAKE_MOVE === mv :: -f
DEBUG 1: QMAKE_ORIG_DESTDIR === ../build/release
DEBUG 1: QMAKE_ORIG_TARGET === qkismet
DEBUG 1: QMAKE_PRL_INTERNAL_FILES === /usr/share/qt3/lib/libqt-mt.prl
DEBUG 1: QMAKE_RUN_CC === $(CC) -c $(CFLAGS) $(INCPATH) -o $obj $src
DEBUG 1: QMAKE_RUN_CC_IMP === $(CC) -c $(CFLAGS) $(INCPATH) -o $@ $<
DEBUG 1: QMAKE_RUN_CXX === $(CXX) -c $(CXXFLAGS) $(INCPATH) -o $obj $src
DEBUG 1: QMAKE_RUN_CXX_IMP === $(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<
DEBUG 1: QMAKE_STRIPFLAGS_LIB === --strip-unneeded
DEBUG 1: QMAKE_SYMBOLIC_LINK === ln -sf
DEBUG 1: QMAKE_TAR === tar :: -cf
DEBUG 1: QMAKE_UIC === /usr/share/qt3/bin/uic
DEBUG 1: QMAKE_YACC === yacc
DEBUG 1: QMAKE_YACCFLAGS === -d
DEBUG 1: QMAKE_YACCFLAGS_MANGLE === -p :: $base :: -b :: $base
DEBUG 1: QMAKE_YACC_HEADER === $base.tab.h
DEBUG 1: QMAKE_YACC_SOURCE === $base.tab.c
DEBUG 1: QT === network
DEBUG 1: RCC_DIR === ../build/release
DEBUG 1: RESOURCES === qkismet.qrc
DEBUG 1: SOURCES === headmenu.cpp :: settings.cpp :: configdialog.cpp :: configp
ages.cpp :: infoview.cpp :: graph.cpp :: kisfilter.cpp :: netmodel.cpp :: netite
m.cpp :: netview.cpp :: alertmodel.cpp :: alertview.cpp :: statmodel.cpp :: kisv
iew.cpp :: protprops.cpp :: kisock.cpp :: main.cpp :: mwnd.cpp :: mwtoolbar.cpp
:: viewtoolbar.cpp :: filteredit.cpp :: about.cpp :: statview.cpp :: manuf.cpp
DEBUG 1: SRCMOC === ../build/release/moc_headmenu.cpp :: ../build/release/moc_co
nfigdialog.cpp :: ../build/release/moc_infoview.cpp :: ../build/release/moc_grap
h.cpp :: ../build/release/moc_kisfilter.cpp :: ../build/release/moc_netview.cpp
:: ../build/release/moc_alertmodel.cpp :: ../build/release/moc_alertview.cpp ::
../build/release/moc_kisview.cpp :: ../build/release/moc_kisock.cpp :: ../build/                                                                            release/moc_main.cpp :: ../build/release/moc_mwnd.cpp :: ../build/release/moc_mw                                                                            toolbar.cpp :: ../build/release/moc_viewtoolbar.cpp :: ../build/release/moc_filt                                                                            eredit.cpp :: ../build/release/moc_about.cpp :: ../build/release/moc_netmodel.cp                                                                            p :: ../build/release/moc_statview.cpp :: ../build/release/moc_statmodel.cpp
DEBUG 1: TARGET === ../build/release/qkismet
DEBUG 1: TEMPLATE === app
DEBUG 1: VERSION === 1.0.0
DEBUG 1: VER_MAJ === 1
DEBUG 1: VER_MIN === 0
DEBUG 1: VER_PAT === 0
DEBUG 1: _HDRMOC === ../build/release/moc_headmenu.cpp :: ../build/release/moc_c                                                                            onfigdialog.cpp :: ../build/release/moc_infoview.cpp :: ../build/release/moc_gra                                                                            ph.cpp :: ../build/release/moc_kisfilter.cpp :: ../build/release/moc_netview.cpp                                                                             :: ../build/release/moc_alertmodel.cpp :: ../build/release/moc_alertview.cpp ::                                                                             ../build/release/moc_kisview.cpp :: ../build/release/moc_kisock.cpp :: ../build                                                                            /release/moc_main.cpp :: ../build/release/moc_mwnd.cpp :: ../build/release/moc_m                                                                            wtoolbar.cpp :: ../build/release/moc_viewtoolbar.cpp :: ../build/release/moc_fil                                                                            teredit.cpp :: ../build/release/moc_about.cpp :: ../build/release/moc_netmodel.c                                                                            pp :: ../build/release/moc_statview.cpp :: ../build/release/moc_statmodel.cpp
DEBUG 1: target.path === /usr/bin/
DEBUG 1: target.uninstall === -$(DEL_FILE) "$(INSTALL_ROOT)/usr/bin/$(QMAKE_TARG                                                                            ET)"
root@bt4-desktop:~/qk/qkismet-0.1.1/src# CODE]
```CODE][/code]
/CODE]qkismet.pro:24: Unknown test function: CONFIG

---

### Post by freeballer on 2009-09-02
wow. guess its time to ask the author for help... I wish this guy made this available in .deb form with all dependancies.

but at least it wasn't just me. feel out of the game as far as linux goes nowadays

---

### Post by krzych on 2009-09-09
Hi,

I'm the author of qKismet. I've already answered your question at sf.net forum, but since someone with the same problem may find this thread, I will copy answer here:

> It seems that you installed wrong package. QKismet is Qt4 application, and you are using qmake from Qt3. So, install correct Qt development package, and run qmake again (if you will leave Qt3 version, 'qmake' may still point to Qt3 version and you will see the error again. In this case, run qmake-qt4 instead of qmake).

---

### Post by Sandiep on 2010-04-30
[COLOR=Magenta]**Does rmdir remove empty directories?**[/COLOR]

---

