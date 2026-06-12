---
title: "Xfix throws out video"
date: 2009-02-05
forum: Multimedia Software
---

### Post by afrodeity on 2009-02-05
I recently plugged in a router and for some reason the whole machine slowed down. Anyway, this problem is now solved. Here is the problem that is plaguing me. What happened is that I booted into restore mode and then chose an xfix option which has completely thrown out the video. I now have crazy jagged stripes and for the life of me cannot find any video options when I dpkg-reconfigure. Just stuff about mouse and keyboard. What must I do to get my video back. PS - I installed with safe graphics mode as the option, because it did something similar in normal mode.

---

### Post by afrodeity on 2009-02-12
> **afrodeity said:**
> I recently plugged in a router and for some reason the whole machine slowed down. Anyway, this problem is now solved. Here is the problem that is plaguing me. What happened is that I booted into restore mode and then chose an xfix option which has completely thrown out the video. I now have crazy jagged stripes and for the life of me cannot find any video options when I dpkg-reconfigure. Just stuff about mouse and keyboard. What must I do to get my video back. PS - I installed with safe graphics mode as the option, because it did something similar in normal mode.

I'm posting this hack by a za-ubuntu member which fixed the problem for informational purposes:

press <esc> when the computer boot to get to the grub menu. start in
recovery mode and get into the root shell. you should not have to edit
any files. try this:

cd /etc/X11/
ls -ltr xorg.co*

it should show something like:
-rw-r--r-- 1 root root 1225 2008-06-29 00:32
/etc/X11/xorg.conf.20080629003247  <-- older xorg.conf backup
-rw-r--r-- 1 root root 1225 2008-06-30 15:05
/etc/X11/xorg.conf.1                            <-- older xorg.conf backup
-rw-r--r-- 1 root root 1225 2008-08-27 19:30
/etc/X11/xorg.conf.20080827193042  <-- older xorg.conf backup
-rw-r--r-- 1 root root 1225 2008-08-27 19:55 /etc/X11/xorg.conf.working
-rw-r--r-- 1 root root 1326 2008-09-19 00:54
/etc/X11/xorg.conf.2                            <-- xfix moved
xorg.conf to here before creating xorg.conf again
-rw-r--r-- 1 root root 3378 2008-09-19 00:54 /etc/X11/xorg.conf
scorpking@scorpking-desktop:~$

as you can see i always keep a working copy as a backup. the second last
line contains the last used config file that was in use before xfix was
ran. to get it back run:

cp xorg.conf.2 xorg.conf

please replace xorg.conf.2 with the second last filename showing on your
computer. after that type exit and select resume. if it does not work
copy the third file to xorg.conf and so on... if you need to edit
xorg.conf from cli use nano or vim
([http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html))

good luck
hannes

---

