---
title: "intrepid kdenlive 0.7.6 crashes after mlt update from source"
date: 2009-10-19
forum: Multimedia Software
---

### Post by redxine on 2009-10-19
EDIT2: Disregard this post. I found the working executable in ~/kdenlive/bin/ after I played with the kdenlive source. So [solved]: To correct the problem download the source builder by:

1. Create a kdenlive directory in your home folder if not done already. Follow the tutorial at [https://help.ubuntu.com/community/KdenliveSVN](https://help.ubuntu.com/community/KdenliveSVN)
2. cd to the source directory, and run ```
make clean
make
sudo make install
```
3. run or update menu to point to ~/kdenlive/bin/kdenlive

I had kdenlive installed and running just fine from the third party repo for intrepid. It reecently updated and complained that MLT was not the right version, so I downlaoded the latest source and compiled + installed. Now kdenlive crashes at startup with SIGSEV 11. I tried removing all the files the source installed and also tried reinstalling from the repo with no luck. The problem lies with the ./profiles director of MLT. Any suggestions?

EDIT: I tried running the builder wizard, and after compiling 0.7.7 and running through the inital setup wizard it crashes. I get the following error:
```
Application: Kdenlive (kdenlive), signal SIGSEGV
[Current thread is 0 (LWP 20348)]

Thread 2 (Thread 0xb28a5b90 (LWP 20349)):
#0  0xb8052430 in __kernel_vsyscall ()
#1  0xb66e3df1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb73f8350 in ?? () from /usr/lib/libQtCore.so.4
#3  0xb732696e in ?? () from /usr/lib/libQtCore.so.4
#4  0xb65f250f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb66eba0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb5c836c0 (LWP 20348)):
[KCrash Handler]
#6  0xb6a18162 in QWidget::insertAction () from /usr/lib/libQtGui.so.4
#7  0xb6a1838a in QWidget::addActions () from /usr/lib/libQtGui.so.4
#8  0x0809b839 in MainWindow (this=0x8cbe250, MltPath=@0xbfd521a8, Url=@0xbfd52190, parent=0x0) at /home/redxine/Desktop/kdenlive/kdenlive/src/mainwindow.cpp:303
#9  0x08081c1a in main (argc=136813868, argv=0x8cbeb28) at /home/redxine/Desktop/kdenlive/kdenlive/src/main.cpp:80

```

---

