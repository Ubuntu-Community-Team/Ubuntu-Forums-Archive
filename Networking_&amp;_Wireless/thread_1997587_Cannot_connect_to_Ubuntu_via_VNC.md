---
title: "Cannot connect to Ubuntu via VNC"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by AlHadjiMurad on 2012-06-05
I am trying to get VNC working on my UBUNTU workstation. I have been trying for days and have tried everything I can find.

I would really appreciate someone out there applying their big brain to this, if you can spare a few minutes, please! :)

So it's the latest version (12.04?) installed on a slow P3 Celeron (~800Mhz).

I have set up XFCE on the machine itself and can log in physically and get to the desktop.

However, I cannot VNC to it.

ALL attempts to connect just time out.

I have installed tight vnc server and cannot connect.

I have installed x11vnc and that does not connect either.

I have used the tightvnc and standard vnc clients (from windows).

I have turned the firewall off with ufw (sudo ufw status is "disabled").

I can use PUTTY to SSH to the machine and do whatever, that works fine.

I have tried to telnet to 5900/1/2 and no response.

I have tried to connect using tightvnc and putty and telnet to 5900/1/2 from a machine on the same physical hub, so there is no router or anything in the way, no luck.

It's like something is either blocking 5900/1/2 or x11vnc is not able to link to it.

Here below is x11vnc's output - note that it's running in another session too I think, but when I connect normally it tells me its running on 5901. 

However, all attempts to connect just time out.

Any help at all from you gurus is most appreciated!!! Thank you in advance!

```

download@Server-3:~$ x11vnc -usepw -ncache 10 &
[1] 4509
download@Server-3:~$ 05/06/2012 13:45:23 -usepw: found /home/download/.vnc/passwd
05/06/2012 13:45:23 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 4509
05/06/2012 13:45:23 XOpenDisplay("") failed.
05/06/2012 13:45:23 Trying again with XAUTHLOCALHOSTNAME=localhost ...
05/06/2012 13:45:23
05/06/2012 13:45:23 *** XOpenDisplay failed. No -display or DISPLAY.
05/06/2012 13:45:23 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
05/06/2012 13:45:23 *** 1 2 3 4
05/06/2012 13:45:27 *** XOpenDisplay of ":0" successful.
05/06/2012 13:45:27
05/06/2012 13:45:27 Using X display :0
05/06/2012 13:45:27 rootwin: 0x133 reswin: 0x5600001 dpy: 0xa3585d0
05/06/2012 13:45:27
05/06/2012 13:45:27 ------------------ USEFUL INFORMATION ------------------
05/06/2012 13:45:27 X DAMAGE available on display, using it for polling hints.
05/06/2012 13:45:27   To disable this behavior use: '-noxdamage'
05/06/2012 13:45:27
05/06/2012 13:45:27   Most compositing window managers like 'compiz' or 'beryl'
05/06/2012 13:45:27   cause X DAMAGE to fail, and so you may not see any screen
05/06/2012 13:45:27   updates via VNC.  Either disable 'compiz' (recommended) or
05/06/2012 13:45:27   supply the x11vnc '-noxdamage' command line option.
05/06/2012 13:45:27
05/06/2012 13:45:27 Wireframing: -wireframe mode is in effect for window moves.
05/06/2012 13:45:27   If this yields undesired behavior (poor response, painting
05/06/2012 13:45:27   errors, etc) it may be disabled:
05/06/2012 13:45:27    - use '-nowf' to disable wireframing completely.
05/06/2012 13:45:27    - use '-nowcr' to disable the Copy Rectangle after the
05/06/2012 13:45:27      moved window is released in the new position.
05/06/2012 13:45:27   Also see the -help entry for tuning parameters.
05/06/2012 13:45:27   You can press 3 Alt_L's (Left "Alt" key) in a row to
05/06/2012 13:45:27   repaint the screen, also see the -fixscreen option for
05/06/2012 13:45:27   periodic repaints.
05/06/2012 13:45:27
05/06/2012 13:45:27 XFIXES available on display, resetting cursor mode
05/06/2012 13:45:27   to: '-cursor most'.
05/06/2012 13:45:27   to disable this behavior use: '-cursor arrow'
05/06/2012 13:45:27   or '-noxfixes'.
05/06/2012 13:45:27 using XFIXES for cursor drawing.
05/06/2012 13:45:27 GrabServer control via XTEST.
05/06/2012 13:45:27
05/06/2012 13:45:27 Scroll Detection: -scrollcopyrect mode is in effect to
05/06/2012 13:45:27   use RECORD extension to try to detect scrolling windows
05/06/2012 13:45:27   (induced by either user keystroke or mouse input).
05/06/2012 13:45:27   If this yields undesired behavior (poor response, painting
05/06/2012 13:45:27   errors, etc) it may be disabled via: '-noscr'
05/06/2012 13:45:27   Also see the -help entry for tuning parameters.
05/06/2012 13:45:27   You can press 3 Alt_L's (Left "Alt" key) in a row to
05/06/2012 13:45:27   repaint the screen, also see the -fixscreen option for
05/06/2012 13:45:27   periodic repaints.
05/06/2012 13:45:27
05/06/2012 13:45:27 Client Side Caching: -ncache mode is in effect to provide
05/06/2012 13:45:27   client-side pixel data caching.  This speeds up
05/06/2012 13:45:27   iconifying/deiconifying windows, moving and raising
05/06/2012 13:45:27   windows, and reposting menus.  In the simple CopyRect
05/06/2012 13:45:27   encoding scheme used (no compression) a huge amount
05/06/2012 13:45:27   of extra memory (20-100MB) is used on both the server and
05/06/2012 13:45:27   client sides.  This mode works with any VNC viewer.
05/06/2012 13:45:27   However, in most you can actually see the cached pixel
05/06/2012 13:45:27   data by scrolling down, so you need to re-adjust its size.
05/06/2012 13:45:27   See [http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching).
05/06/2012 13:45:27   If this mode yields undesired behavior (poor response,
05/06/2012 13:45:27   painting errors, etc) it may be disabled via: '-ncache 0'
05/06/2012 13:45:27   You can press 3 Alt_L's (Left "Alt" key) in a row to
05/06/2012 13:45:27   repaint the screen, also see the -fixscreen option for
05/06/2012 13:45:27   periodic repaints.
05/06/2012 13:45:27
05/06/2012 13:45:27 XKEYBOARD: number of keysyms per keycode 7 is greater
05/06/2012 13:45:27   than 4 and 51 keysyms are mapped above 4.
05/06/2012 13:45:27   Automatically switching to -xkb mode.
05/06/2012 13:45:27   If this makes the key mapping worse you can
05/06/2012 13:45:27   disable it with the "-noxkb" option.
05/06/2012 13:45:27   Also, remember "-remap DEAD" for accenting characters.
05/06/2012 13:45:27
05/06/2012 13:45:27 X FBPM extension not supported.
05/06/2012 13:45:27 X display is capable of DPMS.
05/06/2012 13:45:27 --------------------------------------------------------
05/06/2012 13:45:27
05/06/2012 13:45:27 Default visual ID: 0x21
05/06/2012 13:45:28 Read initial data from X display into framebuffer.
05/06/2012 13:45:28 initialize_screen: fb_depth/fb_bpp/fb_Bpl 16/16/2048
05/06/2012 13:45:28
05/06/2012 13:45:28 X display :0 is 16bpp depth=16 true color
05/06/2012 13:45:28
05/06/2012 13:45:28 Autoprobing TCP port
05/06/2012 13:45:28 Autoprobing selected port 5902
05/06/2012 13:45:28 Listening also on IPv6 port 5902 (socket 11)
05/06/2012 13:45:28
05/06/2012 13:45:28 Xinerama is present and active (e.g. multi-head).
05/06/2012 13:45:28 Xinerama: number of sub-screens: 1
05/06/2012 13:45:28 Xinerama: no blackouts needed (only one sub-screen)
05/06/2012 13:45:28
05/06/2012 13:45:28 fb read rate: 5 MB/sec
05/06/2012 13:45:28 The X server says there are 10 mouse buttons.
05/06/2012 13:45:28 screen setup finished.
05/06/2012 13:45:28

The VNC desktop is:      Server-3:2
PORT=5902
```

---

### Post by malapradej on 2013-03-19
I have the same problem here. There is not even an error message to try and find a solution. I just gets to:
[B]
19/03/2013 12:08:54 screen setup finished.
19/03/2013 12:08:54 

The VNC desktop is:      localhost:0
PORT=5900
[/B]

and seems to hang. Anybody there having the same problem...????

---

### Post by steeldriver on 2013-03-19
That's normal I think it just says the **server** is done setting up - what error message do you get from the VNC **client** when you try to connect? what client are you using? from where (within the LAN of the server or from outside?) What version of Ubuntu are you running?

---

### Post by malapradej on 2013-03-19
Hi, Thanks for your reply.

I am running ubuntu 12.04 on my laptop and xubuntu on my desktop. I am trying to setup a vnc connection to my desktop from my laptop. I am running the following commands as described here: [HTML]https://help.ubuntu.com/community/VNC[/HTML].
I have amended it slightly due to problems with running the gdm version. I first run ssh as follows:
```

ssh  -L 5901:localhost:5901 malapradej@<blabla>.org

```
Once on the desktop I try and run this:
```

        sudo x11vnc -safer -localhost -nopw -once \
                    -auth /var/run/lightdm/root/:0 -display :0 \
        ; bg \
        && vncviewer localhost:0

```
This is where I am at a loss... It does not seem to want to go any further.
The output to screen is as follows:
```

19/03/2013 14:48:33 -safer mode:
19/03/2013 14:48:33    vnc_connect=0
19/03/2013 14:48:33    accept_remote_cmds=0
19/03/2013 14:48:33    safe_remote_only=1
19/03/2013 14:48:33    launch_gui=0
19/03/2013 14:48:33 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 32172
19/03/2013 14:48:33 Using X display :0
19/03/2013 14:48:33 rootwin: 0x101 reswin: 0x4a00001 dpy: 0x9aae6f0
19/03/2013 14:48:33 
19/03/2013 14:48:33 ------------------ USEFUL INFORMATION ------------------
19/03/2013 14:48:33 X DAMAGE available on display, using it for polling hints.
19/03/2013 14:48:33   To disable this behavior use: '-noxdamage'
19/03/2013 14:48:33 
19/03/2013 14:48:33   Most compositing window managers like 'compiz' or 'beryl'
19/03/2013 14:48:33   cause X DAMAGE to fail, and so you may not see any screen
19/03/2013 14:48:33   updates via VNC.  Either disable 'compiz' (recommended) or
19/03/2013 14:48:33   supply the x11vnc '-noxdamage' command line option.
19/03/2013 14:48:33 
19/03/2013 14:48:33 Wireframing: -wireframe mode is in effect for window moves.
19/03/2013 14:48:33   If this yields undesired behavior (poor response, painting
19/03/2013 14:48:33   errors, etc) it may be disabled:
19/03/2013 14:48:33    - use '-nowf' to disable wireframing completely.
19/03/2013 14:48:33    - use '-nowcr' to disable the Copy Rectangle after the
19/03/2013 14:48:33      moved window is released in the new position.
19/03/2013 14:48:33   Also see the -help entry for tuning parameters.
19/03/2013 14:48:33   You can press 3 Alt_L's (Left "Alt" key) in a row to 
19/03/2013 14:48:33   repaint the screen, also see the -fixscreen option for
19/03/2013 14:48:33   periodic repaints.
19/03/2013 14:48:33 
19/03/2013 14:48:33 XFIXES available on display, resetting cursor mode
19/03/2013 14:48:33   to: '-cursor most'.
19/03/2013 14:48:33   to disable this behavior use: '-cursor arrow'
19/03/2013 14:48:33   or '-noxfixes'.
19/03/2013 14:48:33 using XFIXES for cursor drawing.
19/03/2013 14:48:33 GrabServer control via XTEST.
19/03/2013 14:48:33 
19/03/2013 14:48:33 Scroll Detection: -scrollcopyrect mode is in effect to
19/03/2013 14:48:33   use RECORD extension to try to detect scrolling windows
19/03/2013 14:48:33   (induced by either user keystroke or mouse input).
19/03/2013 14:48:33   If this yields undesired behavior (poor response, painting
19/03/2013 14:48:33   errors, etc) it may be disabled via: '-noscr'
19/03/2013 14:48:33   Also see the -help entry for tuning parameters.
19/03/2013 14:48:33   You can press 3 Alt_L's (Left "Alt" key) in a row to 
19/03/2013 14:48:33   repaint the screen, also see the -fixscreen option for
19/03/2013 14:48:33   periodic repaints.
19/03/2013 14:48:33 
19/03/2013 14:48:33 XKEYBOARD: number of keysyms per keycode 7 is greater
19/03/2013 14:48:33   than 4 and 192 keysyms are mapped above 4.
19/03/2013 14:48:33   Automatically switching to -xkb mode.
19/03/2013 14:48:33   If this makes the key mapping worse you can
19/03/2013 14:48:33   disable it with the "-noxkb" option.
19/03/2013 14:48:33   Also, remember "-remap DEAD" for accenting characters.
19/03/2013 14:48:33 
19/03/2013 14:48:33 X FBPM extension not supported.
19/03/2013 14:48:33 X display is capable of DPMS.
19/03/2013 14:48:33 --------------------------------------------------------
19/03/2013 14:48:33 
19/03/2013 14:48:33 Default visual ID: 0x21
19/03/2013 14:48:33 Read initial data from X display into framebuffer.
19/03/2013 14:48:33 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
19/03/2013 14:48:33 
19/03/2013 14:48:33 X display :0 is 32bpp depth=24 true color
19/03/2013 14:48:33 
19/03/2013 14:48:33 Autoprobing TCP port 
19/03/2013 14:48:33 Autoprobing selected port 5900
19/03/2013 14:48:33 Listening also on IPv6 port 5900 (socket 11)
19/03/2013 14:48:33 
19/03/2013 14:48:33 Xinerama is present and active (e.g. multi-head).
19/03/2013 14:48:33 Xinerama: number of sub-screens: 1
19/03/2013 14:48:33 Xinerama: no blackouts needed (only one sub-screen)
19/03/2013 14:48:33 
19/03/2013 14:48:33 fb read rate: 56 MB/sec
19/03/2013 14:48:33 The X server says there are 24 mouse buttons.
19/03/2013 14:48:33 screen setup finished.
19/03/2013 14:48:33 

The VNC desktop is:      localhost:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching

```
I have tried several options thinking it may be due to a slow connection, but it still does not work.

---

### Post by malapradej on 2013-03-19
I am trying to connect to my desktop which is behind a router at home. There is no problem with port forwarding and I have a dns fixed address I use. My laptop is working over a mobile phone hotspot also from home. I would like to be able to access my desktop form anywhere. I hope this makes it clear.

---

### Post by malapradej on 2013-03-20
I can't run the client software as the server is still running and won't allow me back into the terminal. Is there a problem with my 2nd list of statements. Will the " bg " not make the process run in the background. Please advise if I am doing something awkward.

---

### Post by steeldriver on 2013-03-20
AFAIK 'bg' is only used for interactive job control in the shell - you would typically use it after stopping the command with Ctrl-Z and finding the job number then doing 'bg 2' for example

If you want to start your x11vnc command in the background, just add '&' when you invoke it
```

sudo x11vnc -safer -localhost -nopw -once -auth /var/run/lightdm/root/:0 -display :0 **&**

```
However are you sure you want to start it as root like that? usually x11vnc is invoked by a user (not by root) in order to share the current desktop session, e.g. the default for mythtv is

```
$ ps -ef |grep x11vnc
steeldriver 1675     1  0 Mar08 ?        00:06:04 x11vnc -rfbauth /home/steeldriver/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -xkb

```

OTOH if you are trying to create a remote VNC server that starts with lightdm and allows you to log in remotely then the method that I've used in the past is this:

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

Also why are you tunneling port 5901 when you are telling the server to use port 5900?

---

### Post by malapradej on 2013-03-20
OK. This seems to get me part of the way. I ssh to my desktop from my laptop with the following commands:
```

ssh  -L 5901:localhost:5901 malapradej@<blabla>.org

```
I then use the following as you suggested to start the vnc server:
```

sudo x11vnc -safer -localhost -nopw -once -rfbport 5901 -auth /var/run/lightdm/root/:0 -display :0

```
And get the following feedback. I assume it has worked.
```

20/03/2013 23:14:33 passing arg to libvncserver: -rfbport
20/03/2013 23:14:33 passing arg to libvncserver: 5901
20/03/2013 23:14:33 -safer mode:
20/03/2013 23:14:33    vnc_connect=0
20/03/2013 23:14:33    accept_remote_cmds=0
20/03/2013 23:14:33    safe_remote_only=1
20/03/2013 23:14:33    launch_gui=0
20/03/2013 23:14:33 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 18266
20/03/2013 23:14:33 Using X display :0
20/03/2013 23:14:33 rootwin: 0x101 reswin: 0x1800001 dpy: 0x9eb7758
20/03/2013 23:14:33 
20/03/2013 23:14:33 ------------------ USEFUL INFORMATION ------------------
20/03/2013 23:14:33 X DAMAGE available on display, using it for polling hints.
20/03/2013 23:14:33   To disable this behavior use: '-noxdamage'
20/03/2013 23:14:33 
20/03/2013 23:14:33   Most compositing window managers like 'compiz' or 'beryl'
20/03/2013 23:14:33   cause X DAMAGE to fail, and so you may not see any screen
20/03/2013 23:14:33   updates via VNC.  Either disable 'compiz' (recommended) or
20/03/2013 23:14:33   supply the x11vnc '-noxdamage' command line option.
20/03/2013 23:14:33 
20/03/2013 23:14:33 Wireframing: -wireframe mode is in effect for window moves.
20/03/2013 23:14:33   If this yields undesired behavior (poor response, painting
20/03/2013 23:14:33   errors, etc) it may be disabled:
20/03/2013 23:14:33    - use '-nowf' to disable wireframing completely.
20/03/2013 23:14:33    - use '-nowcr' to disable the Copy Rectangle after the
20/03/2013 23:14:33      moved window is released in the new position.
20/03/2013 23:14:33   Also see the -help entry for tuning parameters.
20/03/2013 23:14:33   You can press 3 Alt_L's (Left "Alt" key) in a row to 
20/03/2013 23:14:33   repaint the screen, also see the -fixscreen option for
20/03/2013 23:14:33   periodic repaints.
20/03/2013 23:14:33 
20/03/2013 23:14:33 XFIXES available on display, resetting cursor mode
20/03/2013 23:14:33   to: '-cursor most'.
20/03/2013 23:14:33   to disable this behavior use: '-cursor arrow'
20/03/2013 23:14:33   or '-noxfixes'.
20/03/2013 23:14:33 using XFIXES for cursor drawing.
20/03/2013 23:14:33 GrabServer control via XTEST.
20/03/2013 23:14:33 
20/03/2013 23:14:33 Scroll Detection: -scrollcopyrect mode is in effect to
20/03/2013 23:14:33   use RECORD extension to try to detect scrolling windows
20/03/2013 23:14:33   (induced by either user keystroke or mouse input).
20/03/2013 23:14:33   If this yields undesired behavior (poor response, painting
20/03/2013 23:14:33   errors, etc) it may be disabled via: '-noscr'
20/03/2013 23:14:33   Also see the -help entry for tuning parameters.
20/03/2013 23:14:33   You can press 3 Alt_L's (Left "Alt" key) in a row to 
20/03/2013 23:14:33   repaint the screen, also see the -fixscreen option for
20/03/2013 23:14:33   periodic repaints.
20/03/2013 23:14:33 
20/03/2013 23:14:33 XKEYBOARD: number of keysyms per keycode 7 is greater
20/03/2013 23:14:33   than 4 and 192 keysyms are mapped above 4.
20/03/2013 23:14:33   Automatically switching to -xkb mode.
20/03/2013 23:14:33   If this makes the key mapping worse you can
20/03/2013 23:14:33   disable it with the "-noxkb" option.
20/03/2013 23:14:33   Also, remember "-remap DEAD" for accenting characters.
20/03/2013 23:14:33 
20/03/2013 23:14:33 X FBPM extension not supported.
20/03/2013 23:14:33 X display is capable of DPMS.
20/03/2013 23:14:33 --------------------------------------------------------
20/03/2013 23:14:33 
20/03/2013 23:14:33 Default visual ID: 0x21
20/03/2013 23:14:33 Read initial data from X display into framebuffer.
20/03/2013 23:14:33 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
20/03/2013 23:14:33 
20/03/2013 23:14:33 X display :0 is 32bpp depth=24 true color
20/03/2013 23:14:33 
20/03/2013 23:14:33 Listening for VNC connections on TCP port 5901
20/03/2013 23:14:33 Listening also on IPv6 port 5901 (socket 11)
20/03/2013 23:14:33 
20/03/2013 23:14:33 Xinerama is present and active (e.g. multi-head).
20/03/2013 23:14:33 Xinerama: number of sub-screens: 1
20/03/2013 23:14:33 Xinerama: no blackouts needed (only one sub-screen)
20/03/2013 23:14:33 
20/03/2013 23:14:33 fb read rate: 55 MB/sec
20/03/2013 23:14:33 The X server says there are 24 mouse buttons.
20/03/2013 23:14:33 screen setup finished.
20/03/2013 23:14:33 

The VNC desktop is:      localhost:1
PORT=5901

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching

```
I then Ctrl-Z to as explained in [HTML]https://help.ubuntu.com/community/VNC[/HTML]. A warning comes up that the job has been stopped.
When I try to run the viewer with:
```

vncviewer localhost:1

```
I get
```

Error: Can't open display: 

```
I have tried several combinations such as without sudo and that brings up a warning that:
```

   Only root will have read permission for the file, and so x11vnc must be run
   as root (or copy it).  The random characters in the filenames will of course
   change and the directory the cookie file resides in is system dependent.

```
I have made sure that port 5901 is used as you mentioned but I still can't get it to work. I am assuming that vncviewer is run on the remote machine, right??

---

### Post by steeldriver on 2013-03-20
No you run the viewer on the local machine - well, you *could* run it on the remote machine, but then it would display on the remote machine... which would display the display on the remote machine... which would display the display of the display on the remote machine...

Also I'm still not convinced root auth is what you want - what exactly is your goal?

If you are running the standard Ubuntu desktop on the remote machine, why not just use the default Desktop Sharing application (vino-server)?

---

### Post by malapradej on 2013-03-20
The desktop-pc at home is running Xubuntu and my laptop on Ubuntu. I would like to be able to log into the desktop-pc from outside the home and have a windowed session as opposed to something like an ssh-terminal session. Ideally, similar to logging in to the home pc with a xubuntu-desktop but doing it from a location outside the home. Is this possible, and is this what I have been working at for the past few days....? Or, is there another alternative?

---

### Post by steeldriver on 2013-03-20
Did you check out the link I posted?

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

Be sure to include the -localhost flag as well though if you are going to use this over a public network. Remember that the port number and the display number are related by default i.e. if you start the X server on display :0 then the port defaults to 5900, display :1 to port 5901 etc.

I would advise getting it working with both machines on your home LAN first and then figure out the port forwarding - you will also need some kind of static addressing / dynamic dns setup in order to 'see' the desktop machine at your home

Yes there are alternatives freeNX / nomachine / teamviewer or plane 'ssh -X' but I don't have experience with those

---

### Post by malapradej on 2013-03-21
Excellent! The upstart job works like magic. No need to run a script to start the vnc server, it run's at startup on the home-pc. I have added -localhost flag to make it safe to use over a public network (I assume this is all that is needed). All I need to do is ssh into the desktop-pc at home from anywhere on the internet and run
```

vncviewer localhost:0

```
and I have a tight vnc viewer session from which I can log into my account. Are there any tricks to optimize a slow connection? I guess I can look at creating a script that would run on the laptop and ssh to the home-pc and run the viewer. Will reply with this once it works. 

Thanks

---

### Post by malapradej on 2013-03-22
Try as I might I could not get the bash script to work. I found and example script which I tailored for my needs from [http://ubuntuforums.org/showthread.php?t=614894](http://ubuntuforums.org/showthread.php?t=614894). The most successful version is:
```

#!/bin/bash
ssh -C -f 192.168.0.6 "gnome-terminal --command '/bin/bash -c (while ! netcat -z localhost 5900; do sleep 1; done; vncviewer localhost:5900)'"

```
But it comes up with an error.
```

Failed to parse arguments: Cannot open display: 

```

---

