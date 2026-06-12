---
title: "kaffeine-sc-plugin-0.4.0"
date: 2009-11-26
forum: Multimedia Software
---

### Post by r00te on 2009-11-26
hey
i am using Ubuntu 9.10
[php]root@desktop:~# uname -a
Linux ahmad-desktop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux[/php]i tried to install kaffeine-sc-plugin-0.4.0
[php]kaffeine-sc-plugin-0.4.0# make
make  all-recursive
make[1]: Entering directory `/root/cccam/kaffeine-sc-plugin-0.4.0'
Making all in src
make[2]: Entering directory `/root/cccam/kaffeine-sc-plugin-0.4.0/src'
Making all in mgcam
make[3]: Entering directory `/root/cccam/kaffeine-sc-plugin-0.4.0/src/mgcam'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/root/cccam/kaffeine-sc-plugin-0.4.0/src/mgcam'
Making all in FFdecsa
make[3]: Entering directory `/root/cccam/kaffeine-sc-plugin-0.4.0/src/FFdecsa'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/root/cccam/kaffeine-sc-plugin-0.4.0/src/FFdecsa'
make[3]: Entering directory `/root/cccam/kaffeine-sc-plugin-0.4.0/src'
if /bin/bash ../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -fasynchronous-unwind-tables -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -MT kaffeinesc.lo -MD -MP -MF ".deps/kaffeinesc.Tpo" -c -o kaffeinesc.lo kaffeinesc.cpp; \
 then mv -f ".deps/kaffeinesc.Tpo" ".deps/kaffeinesc.Plo"; else rm -f ".deps/kaffeinesc.Tpo"; exit 1; fi
In file included from kaffeinesc.cpp:22:
kaffeinesc.h:13:40: error: kaffeine/kaffeinedvbplugin.h: No such file or directory
In file included from /usr/share/qt3/include/qstrlist.h:45,
                 from /usr/share/qt3/include/qdir.h:46,
                 from kaffeinesc.cpp:7:
/usr/share/qt3/include/qstring.h: In member function 'char QChar::latin1() const':
/usr/share/qt3/include/qstring.h:197: warning: conversion to 'char' from 'int' may alter its value
/usr/share/qt3/include/qstring.h: In member function 'void QChar::setCell(uchar)':
/usr/share/qt3/include/qstring.h:222: warning: conversion to 'ushort' from 'int' may alter its value
/usr/share/qt3/include/qstring.h: In member function 'void QChar::setRow(uchar)':
/usr/share/qt3/include/qstring.h:223: warning: conversion to 'ushort' from 'int' may alter its value
/usr/share/qt3/include/qstring.h: In constructor 'QChar::QChar(uchar, uchar)':
/usr/share/qt3/include/qstring.h:267: warning: conversion to 'ushort' from 'int' may alter its value
/usr/share/qt3/include/qstring.h: In constructor 'QStringData::QStringData(QChar*, uint, uint)':
/usr/share/qt3/include/qstring.h:365: warning: conversion to 'unsigned int:30' from 'uint' may alter its value
/usr/share/qt3/include/qstring.h:365: warning: conversion to 'unsigned int:30' from 'uint' may alter its value
In file included from /usr/share/qt3/include/qobject.h:48,
                 from /usr/share/qt3/include/qlayout.h:45,
                 from kaffeinesc.cpp:9:
/usr/share/qt3/include/qevent.h: In constructor 'QContextMenuEvent::QContextMenuEvent(QContextMenuEvent::Reason, const QPoint&, const QPoint&, int)':
/usr/share/qt3/include/qevent.h:432: warning: conversion to 'unsigned char' from 'uint' may alter its value
/usr/share/qt3/include/qevent.h: In member function 'void QDropEvent::setAction(QDropEvent::Action)':
/usr/share/qt3/include/qevent.h:523: warning: conversion to 'unsigned char' from 'uint' may alter its value
In file included from /usr/include/kde/kaboutdata.h:24,
                 from /usr/include/kde/kparts/genericfactory.h:7,
                 from kaffeinesc.cpp:18:
/usr/share/qt3/include/qimage.h: In member function 'bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const':
/usr/share/qt3/include/qimage.h:61: warning: suggest parentheses around '&&' within '||'
In file included from mgcam/crypto.h:31,
                 from mgcam/viaccess.h:4,
                 from mgcam/mgcam.h:12,
                 from dvbscam.h:12,
                 from kaffeinesc.cpp:21:
mgcam/misc.h: At global scope:
mgcam/misc.h:134: warning: unused parameter 'data'
mgcam/misc.h:135: warning: unused parameter 'ad'
In file included from kaffeinesc.cpp:22:
kaffeinesc.h:78: error: expected class-name before '{' token
In file included from kaffeinesc.cpp:23:
kaffeinesc.moc: In static member function 'static QMetaObject* KaffeineSc::staticMetaObject()':
kaffeinesc.moc:203: error: 'KaffeineDvbPlugin' has not been declared
kaffeinesc.moc: In member function 'virtual void* KaffeineSc::qt_cast(const char*)':
kaffeinesc.moc:253: error: 'KaffeineDvbPlugin' has not been declared
kaffeinesc.moc: In member function 'virtual bool KaffeineSc::qt_invoke(int, QUObject*)':
kaffeinesc.moc:267: error: 'KaffeineDvbPlugin' has not been declared
kaffeinesc.moc: In member function 'virtual bool KaffeineSc::qt_emit(int, QUObject*)':
kaffeinesc.moc:274: error: 'KaffeineDvbPlugin' has not been declared
kaffeinesc.moc: In member function 'virtual bool KaffeineSc::qt_property(int, int, QVariant*)':
kaffeinesc.moc:280: error: 'KaffeineDvbPlugin' has not been declared
kaffeinesc.cpp: In member function 'void ScConfigDialog::gboxEnabled(bool)':
kaffeinesc.cpp:120: error: no matching function for call to 'ScConfigDialog::connect(CardClient*&, const char [21], KaffeineSc*&, const char [29])'
/usr/share/qt3/include/qobject.h:118: note: candidates are: static bool QObject::connect(const QObject*, const char*, const QObject*, const char*)
/usr/share/qt3/include/qobject.h:228: note:                 bool QObject::connect(const QObject*, const char*, const char*) const
kaffeinesc.cpp: In member function 'void ScConfigDialog::ccamEnabled(bool)':
kaffeinesc.cpp:149: error: no matching function for call to 'ScConfigDialog::connect(CardClient*&, const char [21], KaffeineSc*&, const char [29])'
/usr/share/qt3/include/qobject.h:118: note: candidates are: static bool QObject::connect(const QObject*, const char*, const QObject*, const char*)
/usr/share/qt3/include/qobject.h:228: note:                 bool QObject::connect(const QObject*, const char*, const char*) const
kaffeinesc.cpp: In member function 'void ScConfigDialog::addEntry()':
kaffeinesc.cpp:180: error: no matching function for call to 'ScConfigDialog::connect(CardClient*&, const char [21], KaffeineSc*&, const char [29])'
/usr/share/qt3/include/qobject.h:118: note: candidates are: static bool QObject::connect(const QObject*, const char*, const QObject*, const char*)
/usr/share/qt3/include/qobject.h:228: note:                 bool QObject::connect(const QObject*, const char*, const char*) const
kaffeinesc.cpp: In constructor 'KaffeineSc::KaffeineSc(QWidget*, const char*, QObject*, const char*, const QStringList&)':
kaffeinesc.cpp:344: error: class 'KaffeineSc' does not have any field named 'KaffeineDvbPlugin'
kaffeinesc.cpp:351: error: 'setInstance' was not declared in this scope
kaffeinesc.cpp:366: error: invalid conversion from 'CardClient*' to 'int'
kaffeinesc.cpp:366: error: cannot convert 'const char*' to 'const sockaddr*' for argument '2' to 'int connect(int, const sockaddr*, socklen_t)'
kaffeinesc.cpp:368: error: invalid conversion from 'QTimer*' to 'int'
kaffeinesc.cpp:368: error: cannot convert 'const char*' to 'const sockaddr*' for argument '2' to 'int connect(int, const sockaddr*, socklen_t)'
kaffeinesc.cpp: In member function 'void KaffeineSc::configDialog()':
kaffeinesc.cpp:406: error: invalid conversion from 'ScConfigDialog*' to 'int'
kaffeinesc.cpp:406: error: cannot convert 'const char*' to 'const sockaddr*' for argument '2' to 'int connect(int, const sockaddr*, socklen_t)'
kaffeinesc.cpp:407: error: invalid conversion from 'ScConfigDialog*' to 'int'
kaffeinesc.cpp:407: error: cannot convert 'const char*' to 'const sockaddr*' for argument '2' to 'int connect(int, const sockaddr*, socklen_t)'
kaffeinesc.cpp: In member function 'void KaffeineSc::newKey(const QStringList&)':
kaffeinesc.cpp:517: warning: comparison between signed and unsigned integer expressions
kaffeinesc.cpp:517: warning: comparison between signed and unsigned integer expressions
kaffeinesc.cpp: In member function 'void* KaffeineSc::init(int, int, int, int)':
kaffeinesc.cpp:608: error: invalid conversion from 'CatParser*' to 'int'
kaffeinesc.cpp:608: error: cannot convert 'const char*' to 'const sockaddr*' for argument '2' to 'int connect(int, const sockaddr*, socklen_t)'
kaffeinesc.cpp:617: error: invalid conversion from 'DVBscam*' to 'int'
kaffeinesc.cpp:617: error: cannot convert 'const char*' to 'const sockaddr*' for argument '2' to 'int connect(int, const sockaddr*, socklen_t)'
In file included from kaffeinesc.cpp:18:
/usr/include/kde/kparts/genericfactory.h: In member function 'KParts::Part* KParts::GenericFactory<T>::createPartObject(QWidget*, const char*, QObject*, const char*, const char*, const QStringList&) [with T = KaffeineSc]':
kaffeinesc.cpp:691:   instantiated from here
/usr/include/kde/kparts/genericfactory.h:118: error: cannot convert 'KaffeineSc*' to 'KParts::Part*' in return
In file included from /usr/include/kde/kgenericfactory.h:25,
                 from /usr/include/kde/kparts/genericfactory.h:6,
                 from kaffeinesc.cpp:18:
/usr/include/kde/kgenericfactory.tcc: In static member function 'static Product* KDEPrivate::ConcreteFactory<Product, ParentType>::create(QWidget*, const char*, QObject*, const char*, const QStringList&, KDEPrivate::Type2Type<QObject>) [with Product = KaffeineSc, ParentType = QObject]':
/usr/include/kde/kgenericfactory.tcc:133:   instantiated from 'static Product* KDEPrivate::ConcreteFactory<Product, ParentType>::create(QWidget*, const char*, QObject*, const char*, const char*, const QStringList&) [with Product = KaffeineSc, ParentType = QObject]'
/usr/include/kde/kparts/genericfactory.h:110:   instantiated from 'KParts::Part* KParts::GenericFactory<T>::createPartObject(QWidget*, const char*, QObject*, const char*, const char*, const QStringList&) [with T = KaffeineSc]'
kaffeinesc.cpp:691:   instantiated from here
/usr/include/kde/kgenericfactory.tcc:167: error: no matching function for call to 'KaffeineSc::KaffeineSc(QObject*&, const char*&, const QStringList&)'
kaffeinesc.cpp:343: note: candidates are: KaffeineSc::KaffeineSc(QWidget*, const char*, QObject*, const char*, const QStringList&)
kaffeinesc.h:78: note:                 KaffeineSc::KaffeineSc(const KaffeineSc&)
make[3]: *** [kaffeinesc.lo] Error 1
make[3]: Leaving directory `/root/cccam/kaffeine-sc-plugin-0.4.0/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/cccam/kaffeine-sc-plugin-0.4.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/cccam/kaffeine-sc-plugin-0.4.0'
make: *** [all] Error 2[/php] anyhelp plz

---

