---
title: "Problems installing Sopcast"
date: 2008-08-14
forum: Multimedia Software
---

### Post by r2cool on 2008-08-14
Hi,
I was trying to install sopcast on my Hardy Heron. I installed the QT3 package and then went into the SRC directory of qsopcast 0.3.3 I did qmake. It worked fine. But when I do $ sudo mak, I get the following errors
```

raghu@raghu-desktop:~/Desktop/qsopcast-0.3.3/src$ sudo make
[sudo] password for raghu: 
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -I.moc/ -o .obj/channel.o channel.cpp
In file included from channel.cpp:21:
header.h:4:26: error: qapplication.h: No such file or directory
header.h:5:24: error: qtabwidget.h: No such file or directory
header.h:6:19: error: qvbox.h: No such file or directory
header.h:7:19: error: qhbox.h: No such file or directory
header.h:8:23: error: qlistview.h: No such file or directory
header.h:9:20: error: qlabel.h: No such file or directory
header.h:10:21: error: qslider.h: No such file or directory
header.h:11:25: error: qpushbutton.h: No such file or directory
header.h:12:23: error: qlineedit.h: No such file or directory
header.h:13:19: error: qhttp.h: No such file or directory
header.h:14:21: error: qbuffer.h: No such file or directory
header.h:15:21: error: qregexp.h: No such file or directory
header.h:16:22: error: qprocess.h: No such file or directory
header.h:17:24: error: qstatusbar.h: No such file or directory
header.h:18:20: error: qtimer.h: No such file or directory
header.h:19:23: error: qsettings.h: No such file or directory
header.h:20:22: error: qpalette.h: No such file or directory
header.h:21:29: error: qsocketnotifier.h: No such file or directory
header.h:22:21: error: qsocket.h: No such file or directory
header.h:23:22: error: qmenubar.h: No such file or directory
header.h:24:26: error: qradiobutton.h: No such file or directory
header.h:25:25: error: qmessagebox.h: No such file or directory
header.h:26:18: error: qdom.h: No such file or directory
header.h:27:25: error: qtoolbutton.h: No such file or directory
header.h:28:23: error: qptrlist.h: No such file or directory
In file included from channel.cpp:22:
channel.h:13: error: expected class-name before ‘{’ token
channel.h:14: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
channel.h:15: error: expected ‘;’ before ‘public’
channel.h:24: error: ‘QString’ has not been declared
channel.h:24: error: ‘QString’ has not been declared
channel.h:24: error: ‘QString’ has not been declared
channel.h:27: error: ‘QMouseEvent’ has not been declared
channel.h:36: error: expected `:' before ‘slots’
channel.h:37: error: expected primary-expression before ‘void’
channel.h:37: error: ISO C++ forbids declaration of ‘slots’ with no type
channel.h:37: error: expected ‘;’ before ‘void’
channel.h:38: error: ‘QListViewItem’ has not been declared
channel.h:38: error: expected ‘,’ or ‘...’ before ‘&’ token
channel.h:38: error: ISO C++ forbids declaration of ‘QPoint’ with no type
channel.h:39: error: ‘QListViewItem’ has not been declared
channel.h:43: error: expected `:' before ‘slots’
channel.h:44: error: expected primary-expression before ‘void’
channel.h:44: error: ISO C++ forbids declaration of ‘slots’ with no type
channel.h:44: error: expected ‘;’ before ‘void’
In file included from channel.cpp:23:
mainwindow.h:20: error: expected class-name before ‘{’ token
mainwindow.h:21: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
mainwindow.h:22: error: expected ‘;’ before ‘public’
mainwindow.h:41: error: ‘QKeyEvent’ has not been declared
mainwindow.h:43: error: expected `:' before ‘slots’
mainwindow.h:44: error: expected primary-expression before ‘void’
mainwindow.h:44: error: ISO C++ forbids declaration of ‘slots’ with no type
mainwindow.h:44: error: expected ‘;’ before ‘void’
In file included from channel.cpp:24:
mylistitem.h:7: error: expected class-name before ‘{’ token
mylistitem.h:9: error: expected `)' before ‘*’ token
mylistitem.h:14: error: expected `)' before ‘*’ token
mylistitem.h:19: error: expected `)' before ‘*’ token
mylistitem.h:25: error: expected `)' before ‘*’ token
mylistitem.h:32: error: ‘QColor’ does not name a type
mylistitem.h:33: error: ‘QColor’ does not name a type
mylistitem.h:38: error: ‘QPainter’ has not been declared
mylistitem.h:38: error: expected ‘,’ or ‘...’ before ‘&’ token
mylistitem.h:39: error: ISO C++ forbids declaration of ‘QColorGroup’ with no type
mylistitem.h:56: error: ‘QListViewItem’ has not been declared
mylistitem.h: In member function ‘void MyListItem::paintCell(int*, int)’:
mylistitem.h:40: error: expected `;' before ‘_cg’
mylistitem.h:40: warning: statement has no effect
mylistitem.h:42: error: ‘_cg’ was not declared in this scope
mylistitem.h:42: error: ‘QColorGroup’ is not a class or namespace
mylistitem.h:42: error: ‘bcolor’ was not declared in this scope
mylistitem.h:43: error: ‘QColorGroup’ is not a class or namespace
mylistitem.h:43: error: ‘fcolor’ was not declared in this scope
mylistitem.h:45: error: ‘QListViewItem’ has not been declared
mylistitem.h:45: error: ‘column’ was not declared in this scope
mylistitem.h:45: error: ‘width’ was not declared in this scope
mylistitem.h:45: error: ‘alignment’ was not declared in this scope
mylistitem.h: In member function ‘int MyListItem::compare(int*, int, bool) const’:
mylistitem.h:64: error: ‘text’ was not declared in this scope
mylistitem.h:64: error: request for member ‘text’ in ‘* i’, which is of non-class type ‘int’
mylistitem.h:65: error: ‘QListViewItem’ has not been declared
In file included from channel.cpp:25:
config.h: At global scope:
config.h:9: error: expected class-name before ‘{’ token
config.h:10: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
config.h:11: error: expected ‘;’ before ‘public’
config.h:23: error: expected `:' before ‘slots’
config.h:24: error: expected primary-expression before ‘void’
config.h:24: error: ISO C++ forbids declaration of ‘slots’ with no type
config.h:24: error: expected ‘;’ before ‘void’
In file included from channel.cpp:26:
mylabel.h:8: error: invalid use of incomplete type ‘struct QLabel’
config.h:7: error: forward declaration of ‘struct QLabel’
mylabel.h:10: error: expected `)' before ‘*’ token
mylabel.h:12: error: ‘QMouseEvent’ has not been declared
In file included from channel.cpp:27:
menubar.h:12: error: expected class-name before ‘{’ token
menubar.h:13: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
menubar.h:14: error: expected ‘;’ before ‘public’
menubar.h:29: error: expected `:' before ‘slots’
menubar.h:30: error: expected primary-expression before ‘void’
menubar.h:30: error: ISO C++ forbids declaration of ‘slots’ with no type
menubar.h:30: error: expected ‘;’ before ‘void’
menubar.h:32: error: expected `:' before ‘slots’
menubar.h:33: error: expected primary-expression before ‘void’
menubar.h:33: error: ISO C++ forbids declaration of ‘slots’ with no type
menubar.h:33: error: expected ‘;’ before ‘void’
In file included from pageplay.h:6,
                 from channel.cpp:28:
./myhbox.h:9: error: expected class-name before ‘{’ token
./myhbox.h:11: error: expected `)' before ‘*’ token
./myhbox.h:16: error: ‘QString’ does not name a type
In file included from channel.cpp:28:
pageplay.h:13: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
pageplay.h:14: error: expected ‘;’ before ‘public’
pageplay.h:20: error: ‘QString’ does not name a type
pageplay.h:21: error: ‘QString’ does not name a type
pageplay.h:22: error: ‘QString’ does not name a type
pageplay.h:28: error: expected `:' before ‘slots’
pageplay.h:29: error: expected primary-expression before ‘void’
pageplay.h:29: error: ISO C++ forbids declaration of ‘slots’ with no type
pageplay.h:29: error: expected ‘;’ before ‘void’
pageplay.h:32: error: expected `:' before ‘slots’
pageplay.h:33: error: expected primary-expression before ‘void’
pageplay.h:33: error: ISO C++ forbids declaration of ‘slots’ with no type
pageplay.h:33: error: expected ‘;’ before ‘void’
In file included from channel.cpp:29:
record.h:16: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
record.h:17: error: expected ‘;’ before ‘public’
record.h:22: error: field ‘channelurl’ has incomplete type
record.h:23: error: field ‘channelname’ has incomplete type
record.h:24: error: field ‘channeltype’ has incomplete type
record.h:32: error: ISO C++ forbids declaration of ‘QTimer’ with no type
record.h:32: error: expected ‘;’ before ‘*’ token
record.h:33: error: ISO C++ forbids declaration of ‘QTimer’ with no type
record.h:33: error: expected ‘;’ before ‘*’ token
record.h:35: error: expected `:' before ‘slots’
record.h:36: error: expected primary-expression before ‘void’
record.h:36: error: ISO C++ forbids declaration of ‘slots’ with no type
record.h:36: error: expected ‘;’ before ‘void’
In file included from channel.cpp:30:
tabwidget.h:12: error: expected class-name before ‘{’ token
tabwidget.h:13: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
tabwidget.h:14: error: expected ‘;’ before ‘public’
tabwidget.h:17: error: ISO C++ forbids declaration of ‘QPtrList’ with no type
tabwidget.h:17: error: expected ‘;’ before ‘<’ token
tabwidget.h:18: error: ‘QWidget’ has not been declared
tabwidget.h:20: error: ‘QWidget’ has not been declared
tabwidget.h:26: error: ‘QMouseEvent’ has not been declared
tabwidget.h:28: error: expected `:' before ‘slots’
tabwidget.h:29: error: expected primary-expression before ‘void’
tabwidget.h:29: error: ISO C++ forbids declaration of ‘slots’ with no type
tabwidget.h:29: error: expected ‘;’ before ‘void’
tabwidget.h:33: error: ‘QWidget’ has not been declared
tabwidget.h:19: error: default argument for parameter of type ‘QString’ has type ‘const char [4]’
channel.cpp:32: error: expected `)' before ‘*’ token
make: *** [.obj/channel.o] Error 1
raghu@raghu-desktop:~/Desktop/qsopcast-0.3.3/src$ g++ --version
g++ (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

Does Sopcast not work on 8.04? Any tips on how to fix them would be really appreciated. 
Thanks in advance

---

