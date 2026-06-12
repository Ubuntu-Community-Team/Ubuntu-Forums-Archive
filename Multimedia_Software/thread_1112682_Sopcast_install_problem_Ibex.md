---
title: "Sopcast install problem Ibex"
date: 2009-03-31
forum: Multimedia Software
---

### Post by bogman on 2009-03-31
I'm having difficulties installing sopcast on ibex. I used the instructions for installing sopcast on hardy [http://www.icelab.eu/en/blog/ubuntu-and-linux-12/how-to-install-sopcast-on-ubuntu-85.htm](http://www.icelab.eu/en/blog/ubuntu-and-linux-12/how-to-install-sopcast-on-ubuntu-85.htm) and got errors when it comes to installing the gui frontend.  I've looked around for explicit ibex install instructions but couldn't find any.  Any help or pointers on where to look would be appreciated.


user@user-laptop:~/Apps/sopcast/qsopcast-0.3.5/src$ qmake-qt3 && make && sudo make install
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/channel.o channel.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/config.o config.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/playfork.o playfork.cpp
playfork.cpp: In member function ‘void PlayFork::onPlayerExit()’:
playfork.cpp:117: warning: suggest explicit braces to avoid ambiguous ‘else’
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/loadsave.o loadsave.cpp
loadsave.cpp: In member function ‘void LoadSave::saveopenstate()’:
loadsave.cpp:130: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/main.o main.cpp
main.cpp: In function ‘int main(int, char**)’:
main.cpp:47: error: ‘srand’ was not declared in this scope
make: *** [.obj/main.o] Error 1

---

### Post by hyz on 2009-07-06
i have the same problem :(

---

### Post by hyz on 2009-07-06
I think I found a fix 

from : [http://somebody650.spaces.live.com/blog/cns!DE647D405381DAA7!910.entry](http://somebody650.spaces.live.com/blog/cns!DE647D405381DAA7!910.entry)


[I]"When doing the 'make and install' part, I caught this error:

main.cpp: In function 'int main(int, char**)':
main.cpp:47: error: 'srand' was not declared in this scope
make: *** [.obj/main.o] Error 1

At first, I though there may be something wrong with gcc or maybe the standar lib on my Ubuntu is missing. But actually those things have been installed.
After reading some references, I find the way to solve the problem. That is: open the header.h file in ../qsopcast-0.3.5/src and append the '#include <cstdlib>' in the include block of the code.
Save and go back to build again. It should work now."[/I]

---

