---
title: "trying to use X11 and ssh (cannot open display)"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by Neezer on 2009-10-16
So I am working on getting my ssh up and running. I have a server box at home with ubuntu desktop 9.04 running, and I am accessing it via ssh on a remote computer with vista.

I'm trying to get X11 up and running, and I get the following messages when logged into my ubuntu machine...named server.

```

nate@server:~$ echo $DISPLAY
localhost:10.0
nate@server:~$ firefox
Error: cannot open display: localhost:10.0

```

I'm using putty and I am pretty sure I have all of the settings in putty set up to allow X11 port forwarding and things.

---

### Post by Neezer on 2009-10-17
Bump for saturday morning.

---

### Post by Neezer on 2009-10-17
So I was doing some digging and found this thread
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

It was great...
I used 
```

nate@server:~$ sudo apt-get install x11vnc

```

once it was installed, I used this:
```

nate@server:~$ x11vnc -safer -localhost -nopw -once -display :0

```

and installed tight vnc viewer for windows on my remote vista machine.

opened up Tight VNC Viewer and entered localhost in the dialogue box and clicked connect. VOILA! I am working on my ubuntu desktop right now.

Is this connection secure because I went through ssh? I think that is what I did anyways.....Can someone let me know if it is indeed a tunneled connection through ssh?

---

### Post by dmizer on 2009-10-17
What is the exact command you're using to ssh into your server? What is the IP address of your server, and the machine you're testing ssh from? Is the machine you're testing ssh from a Windows box?

Edit:
Since you appear to be running your ssh client from a Windows box, you'll have to make sure there is an X11 server running on your Windows box, otherwise your X11 apps have no X11 window to open into. That would most likely be why you're getting the "cannot open display" error.

---

### Post by Neezer on 2009-10-17
> **dmizer said:**
> What is the exact command you're using to ssh into your server? What is the IP address of your server, and the machine you're testing ssh from? Is the machine you're testing ssh from a Windows box?

Edit:
Since you appear to be running your ssh client from a Windows box, you'll have to make sure there is an X11 server running on your Windows box, otherwise your X11 apps have no X11 window to open into. That would most likely be why you're getting the "cannot open display" error.

well, after I typed in the command:
```

nate@server:~$ x11vnc -safer -localhost -nopw -once -display :0

```
I don't have a prompt anymore. Then I started TightVNCviewer from my vista start menu and entered localhost in the startup box. Then my Ubuntu desktop popped up in a new window.

so I don't really know if I am doing a true tunnel through ssh or not...

---

### Post by kevdog on 2009-10-17
Did you install the xauth package?

---

### Post by Neezer on 2009-10-17
> **kevdog said:**
> Did you install the xauth package?

I don't know....I know I didn't forward any ports except for port 22 from my router to my server....is there a way I can check to see if I have installed the package?


EDIT:

I found this about xauth.

```

nate@server:~$ man Xauth
nate@server:~$ xauth info
Authority file:       /home/nate/.Xauthority
File new:             no
File locked:          no
Number of entries:    3
Changes honored:      yes
Changes made:         no
Current input:        (argv):1

```

So I would guess that I have xauth on my machine.

---

### Post by dmizer on 2009-10-17
> **Neezer said:**
> well, after I typed in the command:
```

nate@server:~$ x11vnc -safer -localhost -nopw -once -display :0

```
I don't have a prompt anymore. Then I started TightVNCviewer from my vista start menu and entered localhost in the startup box. Then my Ubuntu desktop popped up in a new window.

so I don't really know if I am doing a true tunnel through ssh or not...

You're manually starting the x11vnc server, that's why you don't have a prompt. You won't get a prompt back until you stop the x11vnc server.

As long as you typed localhost in your "connect to server" box then yes, you ARE connecting to vnc through the ssh tunnel.

---

### Post by CharlesA on 2009-10-17
Not to derail the thread, but when you start X11server, does it drop you to the login prompt?

I've been using tightvncserver for a while, but I am guessing they do VNC using different means. tightvnc creates a virtual desktop, but does X11 do the same?

---

### Post by Neezer on 2009-10-17
> **CharlesA said:**
> Not to derail the thread, but when you start X11server, does it drop you to the login prompt?

I've been using tightvncserver for a while, but I am guessing they do VNC using different means. tightvnc creates a virtual desktop, but does X11 do the same?

Not exactly sure what you're asking, but when I type in my command to start x11vnc this is the output I get.

```

nate@server:~$ x11vnc -safer -localhost -nopw -once -display :0
17/10/2009 10:09:46 -safer mode:
17/10/2009 10:09:46    vnc_connect=0
17/10/2009 10:09:46    accept_remote_cmds=0
17/10/2009 10:09:46    safe_remote_only=1
17/10/2009 10:09:46    launch_gui=0
17/10/2009 10:09:46 x11vnc version: 0.9.3 lastmod: 2007-09-30
17/10/2009 10:09:46 Using X display :0
17/10/2009 10:09:46
17/10/2009 10:09:46 ------------------ USEFUL INFORMATION ------------------
17/10/2009 10:09:46 X DAMAGE available on display, using it for polling hints.
17/10/2009 10:09:46   To disable this behavior use: '-noxdamage'
17/10/2009 10:09:46
17/10/2009 10:09:46 Wireframing: -wireframe mode is in effect for window moves.
17/10/2009 10:09:46   If this yields undesired behavior (poor response, painting
17/10/2009 10:09:46   errors, etc) it may be disabled:
17/10/2009 10:09:46    - use '-nowf' to disable wireframing completely.
17/10/2009 10:09:46    - use '-nowcr' to disable the Copy Rectangle after the
17/10/2009 10:09:46      moved window is released in the new position.
17/10/2009 10:09:46   Also see the -help entry for tuning parameters.
17/10/2009 10:09:46   You can press 3 Alt_L's (Left "Alt" key) in a row to
17/10/2009 10:09:46   repaint the screen, also see the -fixscreen option for
17/10/2009 10:09:46   periodic repaints.
17/10/2009 10:09:46
17/10/2009 10:09:46 XFIXES available on display, resetting cursor mode
17/10/2009 10:09:46   to: '-cursor most'.
17/10/2009 10:09:46   to disable this behavior use: '-cursor arrow'
17/10/2009 10:09:46   or '-noxfixes'.
17/10/2009 10:09:46 using XFIXES for cursor drawing.
17/10/2009 10:09:46 GrabServer control via XTEST.
17/10/2009 10:09:46
17/10/2009 10:09:46 Scroll Detection: -scrollcopyrect mode is in effect to
17/10/2009 10:09:46   use RECORD extension to try to detect scrolling windows
17/10/2009 10:09:46   (induced by either user keystroke or mouse input).
17/10/2009 10:09:46   If this yields undesired behavior (poor response, painting
17/10/2009 10:09:46   errors, etc) it may be disabled via: '-noscr'
17/10/2009 10:09:46   Also see the -help entry for tuning parameters.
17/10/2009 10:09:46   You can press 3 Alt_L's (Left "Alt" key) in a row to
17/10/2009 10:09:46   repaint the screen, also see the -fixscreen option for
17/10/2009 10:09:46   periodic repaints.
17/10/2009 10:09:46
17/10/2009 10:09:46 XKEYBOARD: number of keysyms per keycode 6 is greater
17/10/2009 10:09:46   than 4 and 290 keysyms are mapped above 4.
17/10/2009 10:09:46   Automatically switching to -xkb mode.
17/10/2009 10:09:46   If this makes the key mapping worse you can
17/10/2009 10:09:46   disable it with the "-noxkb" option.
17/10/2009 10:09:46   Also, remember "-remap DEAD" for accenting characters.
17/10/2009 10:09:46 X FBPM extension not supported.
17/10/2009 10:09:46 X display is capable of DPMS.
17/10/2009 10:09:46 --------------------------------------------------------
17/10/2009 10:09:46
17/10/2009 10:09:46 Default visual ID: 0x21
17/10/2009 10:09:46 Read initial data from X display into framebuffer.
17/10/2009 10:09:46 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4608
17/10/2009 10:09:46
17/10/2009 10:09:46 X display :0.0 is 32bpp depth=24 true color
17/10/2009 10:09:46
17/10/2009 10:09:46 Autoprobing TCP port
17/10/2009 10:09:46 Autoprobing selected port 5900
17/10/2009 10:09:46
17/10/2009 10:09:46 Xinerama is present and active (e.g. multi-head).
17/10/2009 10:09:46 Xinerama: enabling -xwarppointer mode to try to correct
17/10/2009 10:09:46 Xinerama: mouse pointer motion. XTEST+XINERAMA bug.
17/10/2009 10:09:46 Xinerama: Use -noxwarppointer to force XTEST.
17/10/2009 10:09:47 fb read rate: 16 MB/sec
17/10/2009 10:09:47 screen setup finished.
17/10/2009 10:09:47

The VNC desktop is:      localhost:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: http://www.karlrunge.com/x11vnc/#faq-client-caching

```

Then I end up not having a command prompt. Then when I start the Tight VNC Viewer program a window pops up that has my ubuntu desktop in it...

When I close the viewer window, my command prompt comes back up. Also while I am using the remote desktop, I get lots of lines writing to my putty window.

---

### Post by CharlesA on 2009-10-17
I guess I'll play around with it when I get home. Sounds like it's different then tightvnc.

---

### Post by kevdog on 2009-10-17
Type

apt-cache --policy xauth

and see what it states.

---

### Post by krunge on 2009-10-17
> I used this:
```

nate@server:~$ x11vnc -safer -localhost -nopw -once -display :0

```

and installed tight vnc viewer for windows on my remote vista machine.

opened up Tight VNC Viewer and entered localhost in the dialogue box and clicked connect. VOILA! I am working on my ubuntu desktop right now.

That's great it is working.

x11vnc's "-localhost" option means it only allows connections from the same machine it is running on.  So you *must* be using an ssh or putty port redir from the vista machine to the ubuntu machine (i.e. to appear to be coming from localhost.)  Something like this run on the viewer-side:
```

ssh -L 5900:localhost:5900 nate@server

```and then tell the VNC viewer to connect to "localhost:0".

In case it isn't clear for others reading this thread, one can remove the "-localhost" option from x11vnc and then connect directly w/o using ssh.  E.g. if one is running all of this on one's home LAN he might not feel he needs to encrypt the VNC traffic through an ssh tunnel.

---

