---
title: "X / xorg problem: ... lost the connection to the display"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by andiii on 2006-09-13
An application I need to run keeps coming up with an errors msg. Strange thing is, that I had it running but can't get back to that status.

Here's the error msg when I run it local:
SAC> p1  
(this command opens a window to plot data... but I can't click that window.. and closing it closes the application and puts out:)
SAC> Seismic Analysis Code (SAC) lost the connection to the display
Most likely the X server was shut down or you killed/destroyed the application

If I run it on another machine with ssh:
ssh:
SAC> q
X connection to localhost:15.0 broken (explicit kill or server shutdown).


The software installation is ok (it ran + it runs on the remote machine), so it's a problem with my X or xorg..

Here some detai, I'm not sure if it's ok or not..

$ printenv DISPLAY
:0.0

$ c .Xauthority 
dell0MIT-MAGIC-COOKIE-1Q&#65533;&#65533;q&#1032;&#65533;w&#65533;9&#65533;localhost.localdomain0MIT-MAGIC-COOKIE-1Q&#65533;&#65533;q&#1032;&#65533;w&#65533;9&#65533;]0;aw@dell: ~aw@dell:~$ 

$ c .xsession-errors 
!nothing!


$ Xorg -version

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux dell 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03
3:28 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present


I think the problem could be fixed by doing something with my xorg.conf, I had the software running but not anymore. 

Maybe here?
Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "DRI"
        Mode    0666
EndSection


Any ideas what to do or where to look at?

---

