---
title: "Help Request:  vncserver on kubuntu 10.04"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by ghamilton on 2010-06-23
Just upgraded to Ubuntu 10.04 from 8.x and I'm having a non-trivial problem with vncserver following the upgrade.

Before the upgrade, my ~/.vnc/xstartup file looked like this:
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec sh /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
# xsetroot -solid grey
# vncconfig -iconic &
# xterm -geometry 80x25+10+10 -ls -title "$VNCDESKTOP Desktop" &
# startx &

```

This worked just fine under KDE for the last couple of years (both Ubuntu 7.x and 8,x).  I got a "clone" of my desktop on display :55 (or whichever number I chose) and everything behaved as it should.  No blurring, no failures to start GUI applications, no odd behavior.

For QT development support lib reasons, I was compelled to upgrade from 8.x to either 9.x or 10.x, and that required replacing my video card (yes, the ATI X1300 running dual screens is unsupported on 10.x, so enter a shiny new nVidia GT9500) and, of course, its driver.

Happy dance:  everything works, the major target application compiles now with the correct QT libs, and -- after figuring out that nepomuk is a deep and heinous evil which must be destroyed -- I now get acceptable performance.

So, I have a working Kubuntu 10.04 with KDE 4.4.2 and Plasma.

Yay me.

However . . .

Now my remote display is . . . weird.

When I run, for example, "vncviewer localhost:55" from my desktop, the remote view has blurred text for the desktop icons (you can't read it), and the *remote session has an instance of every stinking program that was running on display :0 when vncserver was launched*.

Further, some applications, launched from the remote view command line (display :55), would execute *in the primary session, display :0*.  Seriously.  I would type "dolphin &" in the remote view, and dolphin would pop up in the local view.  Every time.  Konquerer will behave and run in the remote view, but not Dolphin?  WTF?

I messed with the xstartup file, tried the other (twm, etc.) window managers -- tried this for example:
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec sh /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x25+10+10 -ls -title "$VNCDESKTOP Desktop" &
startkde &

```

-- and got various errors (like RANDR missing), and a generally useless remote view.


Currently, I'm running this, which at least gives me readable text for icons and menus:
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec sh /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 128x45+10+10 -ls -title "$VNCDESKTOP Desktop" &
# startx &
/usr/bin/gnome-session &
```

(Yes, I added gnome, just for this purpose.)

The problem with some applications running in the wrong display is still there, and the vncserver startup problem (cloned instance of all current running programs in the remote view) is still there, but at least I can kind of work in the remote view.

Now, I use vnc at home on my CentOS box, I've used it on other boxes, I've used it on earlier versions of Kubuntu.

I've never had this happen.  I'm stumped.


So . . . is there a wizard in the house?

(Thanx in anticipation)

****

---

### Post by SterLo on 2010-06-23
Going to take some random stabs in the dark here:

Could this be a dithering issue?

Dithering generally occurs when a color palette of higher depth must be displayed using a color palette of lower depth. For example, rendering a 24-bit color palette (2^24=16M colors) in a 16-bit display (2^16=64K colors) or a 16-bit color palette in a 8-bit display (2^8=256 colors)

Just a shot in the dark, but vncserver has a -depth flag you can specify to change the color depth of the server to match your desired client display settings.

I'm not sure of the performance implications or whether that even matters to you.

There may be other ways to solve your problem, but this is the first thing that comes to mind.

---

### Post by ghamilton on 2010-06-24
Well, with the substitution of gnome for the remote view desktop, the "can't read menu/icon text" problem is (for now) handled.

The two other significant problems to address are these:
[LIST=1]
[*]when vncserver is started, the remote view "clones" every program that's running on the primary (display 0) desktop -- that is, executes a new instance with the same parameters;
[*]some programs launch properly in the remote view, while others insist on running in the local (display 0) view.
[/LIST]
I can "live with" the first problem:  simply don't have anything but a konsole running on display 0 when launching vncserver, or just log into the remote view and kill off the unneeded instances.  Messy, but not a show stopper.
[INDENT]Incidentally . . . would this phenomenon have anything to do with the ability of KDE to resume all the processes that were running after a system restart?  I guess I need to ask that question on the Desktop forum.[/INDENT]


The second problem is nasty.  One of the primary reasons that vnc supports displays other than 0 is so that separate sessions do not interfere with one another.  Someone working on (virtual) display 1 doesn't impact the guy sitting in the chair working on (real) display 0.

If the guy working on (virtual) display 1 launches a program, and it pops up on the display 0 desktop, both users are going to be confused, and the virtual user will actually be prevented from doing work.


I can put up with a lot of lame stuff, but having my processes run in someone else's space is a little beyond "routine lame."


****

---

### Post by ghamilton on 2010-06-28
Bumpage.

Still looking for an answer.

Beyond the "irritant" stage now.

It's getting in the way of doing work.

****

---

### Post by zn4701 on 2010-08-17
Hi,

if my suspicion is correct, You can't do anything about it and a solution is not in sight.

My suspicion consists of two pars:

1) The plasma engine uses transparancies everywhere. For instance, to get a text label on a button it seems that the label is drawn on a completely transparent bitmap and then the pixmap is printed over the button.

2) vnc4server and thightvnc use an internal X server. As you can check in the version number of your paket or the sources, it still uses one of the last version of the XFree server before the X.org fork. Debian unstable shows 4.1.1+X4.3.0-37 for xvnc4server and tightvnc has as well a XFree server version in the sources.

Together this leads to the interesting effect that the X server inside the vnc server appears to not support transparancy. And somehow the fallback algorithm messes this up big time in trying to fake a sparse text on a transparent background.

x11vnc is, as far as I know, built on recent X.org server sources and should thus not have this problem. Configuration is, per manual, more powerful than with the others, but also more complicated.

Regards, Lutz

---

### Post by krunge on 2010-08-17
> **zn4701 said:**
> 
x11vnc is, as far as I know, built on recent X.org server sources and should thus not have this problem. Configuration is, per manual, more powerful than with the others, but also more complicated.

Regards, Lutz
x11vnc does not contain an X server, rather it connects (as an X client app) to a pre-existing X server and then exports the display via VNC.

If the X server it attaches to is a modern X.org based server then the desired features (i.e. for kde/plasma) should be there.

BTW, x11vnc can emulate 'vncserver' if the 'xvfb' package is installed (see the x11vnc -create option where it will create an Xvfb virtual X session automatically.)  I don't know if the debian Xvfb supports the desired features (i.e. for kde plasma to function.)  There is also the Xdummy hack that uses the X.org dummy driver that should have all X.org features in principle.

---

### Post by zn4701 on 2010-08-18
Slightly off topic, but since it is "straight from the horses mouth":

Is there somewhere some one-piece documentation or  on how to use x11vnc in inetd mode, logging in to the kdm or other display manager via xdmcp? Some time ago I played with the hints on the webpage but always ran into authorization failures. The recent setup with xvnc4server has in /etc/inetd.conf the line

5950 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/Xvnc4 -inetd  -query localhost -once -SecurityTypes None -depth 24 -fp unix/:7100 -co /etc/X11/rgb -geometry 1270x942

To connect from a remote machine a reverse ssh-tunnel is formed, the client starts into the display/login manager.

Regards, Lutz

---

### Post by idokus on 2010-11-12
here is a site which sets up the kde version for the vnc server (Krfb)

[http://www.howtogeek.com/howto/ubuntu/kubuntu/enable-remote-desktop-vnc-on-kubuntu/](http://www.howtogeek.com/howto/ubuntu/kubuntu/enable-remote-desktop-vnc-on-kubuntu/)

I'm working on how to get it to start up automatically, though.

---

### Post by glennr on 2011-03-08
> **zn4701 said:**
> Hi,

if my suspicion is correct, You can't do anything about it and a solution is not in sight.

My suspicion consists of two pars:

1) The plasma engine uses transparancies everywhere. For instance, to get a text label on a button it seems that the label is drawn on a completely transparent bitmap and then the pixmap is printed over the button.

2) vnc4server and thightvnc use an internal X server. As you can check in the version number of your paket or the sources, it still uses one of the last version of the XFree server before the X.org fork. Debian unstable shows 4.1.1+X4.3.0-37 for xvnc4server and tightvnc has as well a XFree server version in the sources.

Together this leads to the interesting effect that the X server inside the vnc server appears to not support transparancy. And somehow the fallback algorithm messes this up big time in trying to fake a sparse text on a transparent background.


The solution is to use a vnc server that supports the features needed for KDE to display properly ( XRENDER I think ). The only one I could find was TigerVNC [http://tigervnc.org/]("http://tigervnc.org/"). I built 1.0.1 from source and it works nicely with KDE 4.4.

TigerVNC has an issue with key repeat on some clients. The only Windows client that worked for me was UltraVNC. The standard vncviewer in 10.04 works fine.

---

### Post by idokus on 2011-03-09
what helped for me was to set colordepth on highest possible, and to disable the compression.

Or at least that's how I got it working.

ps. Is the problem solved in the mean time? That should be nice to know aswell.

---

