---
title: "warning: Need basic cursor movement capability, using vt100"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by caine2000 on 2009-12-29
I had an irritating problem with ssh2 where it kept spitting out a vt100 terminal warning.  Mostly irritating because the top 30 or 40 google hits did not say how to fix it.  Fortunately, the solution is simple.  I apologize if this was posted elsewhere, but I wasn't able to find it easily.


user@ubuntu-1:~$ ssh ubuntu-2
warning: Need basic cursor movement capability, using vt100
Authentication successful.
Last login: Tue Dec 29 2009 20:14:23 from ubuntu-1
Linux 2.4.20.
No mail.
user@ubuntu-2:~$


[ From: [http://gd.tuwien.ac.at/utils/shells/ssh/README.SSH2](http://gd.tuwien.ac.at/utils/shells/ssh/README.SSH2) ]


    * If your sftp2 complains something like this: "Need basic
      cursor movement capability, using vt100", then no library
      containing tgetent() function was found when you ran
      ./configure . If you have a Linux system, then that is
      probably because you don't have either termcap-devel or
      ncurses-devel packages installed. If you want to get rid of
      the message, and/or to use some more exotic terminals
      capabilities, you should install either package. (A good 
      place to look for those is your distribution's web-page.)


The fix I found for Jaunty Ubuntu was to install all ncurses packages, especially the dev ones, and reconfigure/remake ssh2.  Here's what I have installed:


user@ubuntu-1:~# dpkg -l | grep ncurses
libncurses5
libncurses5-dev
libncursesw5
libncursesw5-dev
mtr-tiny
ncurses-base
ncurses-bin
ncurses-term


Et voila:


user@ubuntu-1:~$ ssh ubuntu-2
Authentication successful.
Last login: Tue Dec 29 2009 20:46:38 from ubuntu-1
Linux 2.4.20.
No mail.
user@ubuntu-2:~$


And, my versions of Ubuntu and ssh2, for the record:


user@ubuntu-1:~$ more /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
user@ubuntu-1:~$ ssh -V
ssh: SSH Secure Shell 3.2.0 (non-commercial version) on i686-pc-linux-gnu

---

