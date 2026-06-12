---
title: "can i run sopcast on ubuntu"
date: 2008-05-25
forum: Multimedia Software
---

### Post by kulkarniniraj on 2008-05-25
can anyone help me how to install sopcast on my machine

i have Ubuntu 7.10 for 64 bit & core2duo processor

i have tried numerous ways to install sopcast

i have installed gsopcast using .386 deb package but when i start it
neither it gives channel lists nor it responds when i enter url in it

i installed sopcast webplayer for windows & tried it using wine but it hangs i run it.

i tried for sopcast firefox plugin but it gives error during installation of plugin that some dll cannot b installed and error code -202

i tried internet explorer using IEs4Linux but it also gave error during installation

i downloaded qsopcast tarGz package & tried command line version using
./sp-sc-auth sop://broker.sopcast.com:3912/6001 3908 8908 > /dev/null &

also tried [http://localhost:8908/tv.asf](http://localhost:8908/tv.asf) in firefox & mplayer but it didn't worked either

i tried for gui version of sopcast but when executed make command  it gave op

abc@abc-laptop:~/Desktop/qsopcast/src$ sudo make
[sudo] password for abc:
g++  -o qsopcast .obj/channel.o .obj/config.o .obj/playfork.o .obj/loadsave.o .obj/main.o .obj/mainwindow.o .obj/menubar.o .obj/mylabel.o .obj/mystatusbar.o .obj/pageplay.o .obj/record.o .obj/sopfork.o .obj/sound.o .obj/tabwidget.o .obj/timing.o .obj/utils.o .obj/moc_channel.o .obj/moc_config.o .obj/moc_playfork.o .obj/moc_mainwindow.o .obj/moc_menubar.o .obj/moc_pageplay.o .obj/moc_record.o .obj/moc_sopfork.o .obj/moc_sound.o .obj/moc_mytabbar.o .obj/moc_tabwidget.o .obj/moc_timing.o   -L/usr/share/qt3/lib -L/usr/X11R6/lib -lqt-mt -lXext -lX11 -lm -lpthread
.obj/loadsave.o: In function `LoadSave::saveopenstate()':
loadsave.cpp:(.text+0x30): undefined reference to `Channel::updateOpenState()'
.obj/moc_channel.o:(.rodata._ZTV7Channel[vtable for Channel]+0x5f8): undefined reference to `non-virtual thunk to Channel::~Channel()'
collect2: ld returned 1 exit status
make: *** [qsopcast] Error 1


after trying all these options finally can i hop to run internet tv on my laptop ? please help.

---

### Post by xtreme325x on 2008-06-24
[FONT="Franklin Gothic Medium"][SIZE="3"]I think u can try install sopcast web player on wine. And launch wine browser.[/SIZE][/FONT]

---

