---
title: "a fontend of mplayer --- CMMusic"
date: 2009-03-13
forum: Multimedia Software
---

### Post by bargain685 on 2009-03-13
cmmusic (Console Mplayer Music) ver 1.4

LANG:EN

HOW TO DO:
---------------------------------------------------------

Introduce:

What is CMMusic?Why should I use it?
CMMusic is a frontend of MPlayer which develop base on (n)curses.It has the following advantage:
a.media support: almost every media type is supported by using mplayer powerful ability.even vedio.
b.resource use: as a console application,the memory and cpu use is almost depend on mplayer but no CMMusic.
c.skin and looks: looks like xmms layout.font and effect depend on console application.such as xterm,urxvt,gnome-terminal,konsole.
d.operation: in X,you can use mouse and hot key to finish the work.

---------------------------------------------------------

You can get the software from the following url:
[https://sourceforge.net/projects/cmmusic/](https://sourceforge.net/projects/cmmusic/)

BUG REPORT:
[https://sourceforge.net/tracker2/?fu...7&atid=1126799](https://sourceforge.net/tracker2/?fu...7&atid=1126799)

--------------------------------------------------------

Require:
1.Linux.
2.mplayer installed.
3.ncurses or curses lib and header file.

--------------------------------------------------------

Install:
[1] ./configure
[2] configure option:
--enable-envcode=[ARG] set env code,default UTF-8.
--enable-lrccode=[ARG] set LRC code,default GBK.

Note:

As the app is define to run in Chinese system default.But for the system
which use single length char such as English, should use the following
options for best effects:
<a> --enable-lrccode=[ARG] define your lrc file code.such as UTF-8.

[3] make
[4] make install
[5] install directory:
bin file: /usr/local/bin/cmmusic
plugins file: /usr/local/share/cmmusic/plugins/*
user data: ~/.cmmusic/*
[6] make uninstall or manual delete the directory or file.

--------------------------------------------------------

How to use:
1.Just run cmmusic in console after install.
2.INS to add file to music list.
3.ENTER to play and enjoy!

you can find the key map in the unzip source.tar.gz's directory or
website of software.

----------------------END--------------------------------

---

