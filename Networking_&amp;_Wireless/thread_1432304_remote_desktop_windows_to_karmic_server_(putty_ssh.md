---
title: "remote desktop windows to karmic server (putty ssh vnc)"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by now_here on 2010-03-17
Hi everybody! I am new to linux, just built my first computer acouple of months ago, and decided to try linux. i've learned alot these last couple months, and have been getting more comfortable with the command line interface. with that increased comfort has come the confidence to try out some new things, and so here i am asking for help :) .

I am running ubuntu 9.10 on a desktop (hereafter referred to as desktop) and windows vista on a laptop, both behind a router running ddwrt. 

my goal is to be able to boot up the desktop remotely from the laptop using wake on lan, ssh in using putty, and then get a tunneled encrypted remote gui session. ultimately, id like to be able to do this over the internet from outside my lan, but for now i'm just trying to get it running locally. 

I'll give a quick rundown on what i have been able to do so far. i have configured unencrypted remote desktop access successfully using a tight vnc client on the laptop, and that works fine, but only if i physically log into gnome on the desktop first (its a multi user home pc that boots to the login screen). so i figured the next step was setting up ssh access in order to get gnome running, and then be able to use tight vnc to control the desktop, (with the bonus of encryption). so i got openssh on the desktop and putty on the laptop, and got that working, with a tunnel on 5900. then i setup x11vnc, which seems to be working 
> Last login: Wed Mar 17 14:31:51 2010 from nexus
nowhere@nowhere-desktop:~$ sudo x11vnc -create -safer -localhost -nopw -once -auth /var/lib/gdm/:0.Xauth
[sudo] password for nowhere:
17/03/2010 15:25:32 -safer mode:
17/03/2010 15:25:32    vnc_connect=0
17/03/2010 15:25:32    accept_remote_cmds=0
17/03/2010 15:25:32    safe_remote_only=1
17/03/2010 15:25:32    launch_gui=0
17/03/2010 15:25:32 x11vnc version: 0.9.3 lastmod: 2007-09-30
17/03/2010 15:25:32 wait_for_client: WAIT:cmd=FINDCREATEDISPLAY-Xvfb
17/03/2010 15:25:32 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
17/03/2010 15:25:32
17/03/2010 15:25:32 Autoprobing TCP port
17/03/2010 15:25:32 Autoprobing selected port 5900

The VNC desktop is:      nowhere-desktop:0
PORT=5900but when i try to connect tightvnc through the tunnel, i get "connecting to localhost... status: connection established" and then a pop up saying "connection closed". i read some advice about making some changes to the gdm.conf-custom file, but i couldnt find that anywhere, and i'm kind of at a loss for what to do next. any help is appreciated, but bear in mind that im pretty inexperienced.

---

### Post by krunge on 2010-03-17
Please show how you set up and used the ssh tunnel.

Also, x11vnc will print out info when viewers are connecting, so check for more output being printed after the part you pasted.

If you don't see any additional output from x11vnc when you try to connect, then you know that a firewall or some other problem has completely prevented you from reaching x11vnc.

If you do get extra output when trying to connect, please show it here.

---

### Post by now_here on 2010-03-17
> **krunge said:**
> Please show how you set up and used the ssh tunnel.

Also, x11vnc will print out info when viewers are connecting, so check for more output being printed after the part you pasted.

If you don't see any additional output from x11vnc when you try to connect, then you know that a firewall or some other problem has completely prevented you from reaching x11vnc.

If you do get extra output when trying to connect, please show it here.
no further output, here are some screengrabs from the putty configuration:
[IMG]http://imgur.com/POY36.jpg[/IMG]
[IMG]http://imgur.com/ayt7M.jpg[/IMG]
i would think its not a firewall or something like that, because if i physically turn on the desktop and log in, i have no problem getting vnc running through the tunnel.

---

### Post by krunge on 2010-03-17
The Putty Forwarded port setting should be ```
L5900  localhost:5900
``` not   L5900  192.x.x.x:5900.

You are running x11vnc with '-localhost' which in general is a very smart thing to do if you plan for access only by SSH tunnel.  So x11vnc is only listening on localhost (aka 127.0.0.1) not 192.168.1.100. That explains why you are getting connection closed.

---

### Post by krunge on 2010-03-17
BTW: A tip about SSH local port forwarding: the 'destination' is always **relative** to the process on the remote side (sshd on linux in this case.)

For SSH remote port forwarding it is switched around: the 'destination' is always relative to the ssh client process on the local side (putty.exe on windows in this case.)

---

### Post by now_here on 2010-03-17
> **krunge said:**
> The Putty Forwarded port setting should be ```
L5900  localhost:5900
``` not   L5900  192.x.x.x:5900.

You are running x11vnc with '-localhost' which in general is a very smart thing to do if you plan for access only by SSH tunnel.  So x11vnc is only listening on localhost (aka 127.0.0.1) not 192.168.1.100. That explains why you are getting connection closed.

i tried changing, that, and now vnc says "connecting to localhost... status:connection established, i get the below output in the terminal, and a pop up from vnc saying "connection closed" 

> 17/03/2010 21:05:50 Got connection from client 127.0.0.1
17/03/2010 21:05:50   other clients:
17/03/2010 21:05:50 check_access: client 127.0.0.1 matches host 127.0.0.1
17/03/2010 21:05:50 wait_for_client: got client
17/03/2010 21:05:50 wait_for_client: running: env X11VNC_SKIP_DISPLAY='' /bin/sh   /tmp/x11vnc-find_display.ngqZTK
xauth:  creating new authority file /var/lib/gdm/:0.Xauth
17/03/2010 21:05:50 wait_for_client: find display cmd failed
17/03/2010 21:05:50 wait_for_client: FINDCREATEDISPLAY cmd: /bin/sh /tmp/x11vnc-  find_display.ngqZTK Xvfb
trying N=20 ...
17/03/2010 21:05:51 wait_for_client: read failed: /bin/sh /tmp/x11vnc-find_displ  ay.ngqZTK Xvfb
17/03/2010 21:05:51 fgets: Bad file descriptor

---

### Post by krunge on 2010-03-18
> **now_here said:**
> 
17/03/2010 21:05:50 Got connection from client 127.0.0.1
17/03/2010 21:05:50 other clients:
17/03/2010 21:05:50 check_access: client 127.0.0.1 matches host 127.0.0.1
17/03/2010 21:05:50 wait_for_client: got client
17/03/2010 21:05:50 wait_for_client: running: env X11VNC_SKIP_DISPLAY='' /bin/sh /tmp/x11vnc-find_display.ngqZTK
xauth: creating new authority file /var/lib/gdm/:0.Xauth
17/03/2010 21:05:50 wait_for_client: find display cmd failed
17/03/2010 21:05:50 wait_for_client: FINDCREATEDISPLAY cmd: /bin/sh /tmp/x11vnc- find_display.ngqZTK Xvfb
trying N=20 ...
17/03/2010 21:05:51 wait_for_client: read failed: /bin/sh /tmp/x11vnc-find_displ ay.ngqZTK Xvfb
17/03/2010 21:05:51 fgets: Bad file descriptor

OK, this is where I thought we'd go next once we fixed your putty port forwarding to be "localhost:5900".

Can you explain to me why you want to use the x11vnc '-create' option? Do you really want a virtual (RAM-only) X server created? Or instead do you want to view via VNC the X server on the physical graphics hardware?

If you want the X server on the physical hardware, get rid of '-create'. (Also, your -auth argument may be out of date, e.g. it has moved to a different file location in ubuntu 9.10)

If you want virtual RAM-only X servers apt-get install the 'xvfb' package and remove the '-auth /var/lib/gdm/:0.Xauth' from the x11vnc command line.

---

### Post by suseendran.rengabashyam on 2010-03-18
Hi,

A similar thread related to PuTTy, SSH and VNC

[http://ubuntuforums.org/showthread.php?t=1410679](http://ubuntuforums.org/showthread.php?t=1410679)

Hope this helps.

---

### Post by now_here on 2010-03-18
> **krunge said:**
> OK, this is where I thought we'd go next once we  fixed your putty port forwarding to be "localhost:5900".

Can you explain to me why you want to use the x11vnc '-create' option?  Do you really want a virtual (RAM-only) X server created? Or instead do  you want to view via VNC the X server on the physical graphics hardware?

If you want the X server on the physical hardware, get rid of '-create'.  (Also, your -auth argument may be out of date, e.g. it has moved to a  different file location in ubuntu 9.10)

If you want virtual RAM-only X servers apt-get install the 'xvfb'  package and remove the '-auth /var/lib/gdm/:0.Xauth' from the x11vnc  command line.

haha no, i can't really explain, i stumbled onto that combination  through a relatively long process of trial and error, helped along the  way by various forum threads and other sources, many of which i didn't  fully understand, so i don't really have an overarching conception of  what exactly its doing. i think i understand -nopw -once -localhost and  -auth, but -create just kind of got thrown in there, it seemed like a  good idea at the time? so, not knowing what the functional difference  would be between a virtual x server and one running on the physical  graphics hardware, i cant say i have a preference, and i will defer to  your implication that i can do without the -create.

so i went  ahead and removed -create , and it worked, i was able to see the login  screen. Success! but the thrill of victory was somewhat short lived, as  when i attempted to login, i got a "connection closed". that reminded me  of one of the threads i read which discussed this problem, and  recommended editing the killinits portion of the gdm.conf-custom file.  when i first read that thread i was sure my inability to find and edit  this file was what was holding me back, and i spent quite a while  searching high and low for it in a most inefficient manner, becoming  increasingly sure that it didnt exist, or i was an idiot.

now,  looking into this further i came across this thread [http://ubuntuforums.org/showthread.php?t=1306696](http://ubuntuforums.org/showthread.php?t=1306696)  where you discuss this issue, and the workaround you have developed. i  feel somewhat heartened that gdm.conf-custom file does not, in fact  exist on my machine, and that my inability to find it wasn't due to my  ineptitude. 

thank you very much for the help so far. tomorrow i  will try to implement your solution, although i have to say i'm a little  frightened by the words tarball and compile.

---

### Post by krunge on 2010-03-18
> **now_here said:**
> 
so i went  ahead and removed -create , and it worked, i was able to see the login  screen. Success! but the thrill of victory was somewhat short lived, as  when i attempted to login, i got a "connection closed". that reminded me  of one of the threads i read which discussed this problem, and  recommended editing the killinits portion of the gdm.conf-custom file.

Glad it worked (before that GDM problem of course.)

Are you on ubuntu 9.10?  If so, the killinitclients in GDM has been removed.

You shouldn't be afraid of tarball and compiling; it is really a very powerful aspect of open source and a handy skill to have. (Sadly the distros make it hard for you to compile these days and have you jump through hoops... it was much easier 10 years ago.)  BTW: for x11vnc you can simply compile it as your own userid (no sudo) so there is very little risk.

If you feel you can't compile you can get a precompiled x11vnc 0.9.10 at my site:
[INDENT][http://www.karlrunge.com/x11vnc/bins/](http://www.karlrunge.com/x11vnc/bins/)[/INDENT]
the 'x11vnc-0.9.10_TEST_i686-Linux' one should work on most Linuxes (also x11vnc-0.9.10_TEST_amd64-Linux for amd64)

Anyway, the x11vnc 0.9.10 should avoid all of the GDM killinitclients issues and other other bugs with GDM and/or Xorg.

---

### Post by now_here on 2010-03-20
> **krunge said:**
> 
Are you on ubuntu 9.10?  If so, the killinitclients in GDM has been removed.

You shouldn't be afraid of tarball and compiling; it is really a very powerful aspect of open source and a handy skill to have. (Sadly the distros make it hard for you to compile these days and have you jump through hoops... it was much easier 10 years ago.)  BTW: for x11vnc you can simply compile it as your own userid (no sudo) so there is very little risk.

 
yes i am on 9.10. i figured i'd have a crack at compiling, because im doing this to learn some new stuff as much as for immediate practical purposes. i got the tar and unarchived it, but when i run ./configure i get this output:

> nowhere@nowhere-desktop:/usr/local/src/x11vnc-0.9.9$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for ar... /usr/bin/ar
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking thenonexistentheader.h usability... no
checking thenonexistentheader.h presence... no
checking for thenonexistentheader.h... no
checking for X... no
checking for XGetImage in -lX11... no
configure: error:
==========================================================================
*** A working X window system build environment is required to build ***
x11vnc.  Make sure any required X development packages are installed.
If they are installed in non-standard locations, one can use the
--x-includes=DIR and --x-libraries=DIR configure options or set the
CPPFLAGS and LDFLAGS environment variables to indicate where the X
window system header files and libraries may be found.  On 64+32 bit
machines you may need to point to lib64 or lib32 directories to pick up
the correct word size.

If you want to build x11vnc without X support (e.g. for -rawfb use only
or for native Mac OS X), specify the --without-x configure option.
==========================================================================

from what i can tell it seems like i have the dependencies, but they aren't where they're expected to be, and i just need to point configure to the correct location. however, i'm confused about how to do do that, and what "pick up the correct word length" means. (i am on a 64 bit system)

---

### Post by krunge on 2010-03-20
For building there are some notes here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-build](http://www.karlrunge.com/x11vnc/faq.html#faq-build)
[http://www.karlrunge.com/x11vnc/#building](http://www.karlrunge.com/x11vnc/#building)[/INDENT]
The first link mentions a list of packages one might need that your distro does not install automatically:
```

For Debian the list seems to be:

  gcc
  make
  libc6-dev
  libjpeg8-dev           (formerly libjpeg62-dev)
  libx11-dev
  x11proto-core-dev      (formerly x-dev)
  libxext-dev
  libxtst-dev
  libxdamage-dev
  libxfixes-dev
  libxrandr-dev
  libxinerama-dev
  libxss-dev             (formerly xlibs-static-dev)
  zlib1g-dev
  libssl-dev
  libavahi-client-dev
  linux-libc-dev         (only needed for linux console rawfb support)

Note that depending on your OS version the above names may have
been changed and/or additional packages may be needed.

```
So try apt-get install-ing those. If apt-get complains that a package does not exist that means your distro has renamed it and they want you to jump through a hoop to try to figure out what they renamed it to.

---

### Post by now_here on 2010-03-21
success! got it compiled and everything works. thanks so much for the help Karl! not that this hasn't been an excellent learning experience, but is there some way to vote for ubuntu to update their x11vnc package?

---

### Post by krunge on 2010-03-21
> **now_here said:**
> success! got it compiled and everything works

Great, glad it is working for you.
> is there some way to vote for ubuntu to update their x11vnc package?
ubuntu picks up the debian x11vnc package:
[INDENT][http://packages.debian.org/squeeze/x11vnc](http://packages.debian.org/squeeze/x11vnc)[/INDENT]
which has been staying up-to-date since last summer. It is at 0.9.9, which should solve your problem as well, (0.9.10 is not released yet.)

---

