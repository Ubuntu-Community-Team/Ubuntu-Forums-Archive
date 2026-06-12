---
title: "VNC through SSH tunnel connection problems after apt-upgrade"
date: 2008-02-16
forum: Mythbuntu
---

### Post by SadaraX on 2008-02-16
I am running MythBuntu 7.10 with kernel 

I connect using TightVNC through an SSH tunnel to a remote computer running MythBuntu 7.10 (kernel 2.6.22-14-generic dual-core AMD ). Until about 2 days ago, I was connecting just fine. But now it will not work.

Around the same time, I did an apt-get upgrade and I am not sure if that has caused a problem. 

Here is how I connect to my remote computer. 

 ssh server.address.com -L 5900:server.address.com:5909
 # I connect to desktop number 9 typically

I can still connect with SSH no problem, but VNC will not connect. I am using KDE's remote desktop client (krdc) to connect vnc:/127.0.0.1:0 which does the whole ssh tunnel thing.

When I click connect, krdc (the vnc-viewer) just sits there trying to authenticate, but nothing happens. Occasionally on the SSH window (which is still connect just fine), I get messages like: 

> 
channel 4: open failed: connect failed: Connection timed out


Here is the log from desktop 9 (which is the one I usually use) from my ~/.vnc:

> 
14/02/08 05:53:28 Xvnc version 3.3.tight1.2.9
14/02/08 05:53:28 Copyright (C) 1999 AT&T Laboratories Cambridge.
14/02/08 05:53:28 Copyright (C) 2000-2002 Constantin Kaplinsky.
14/02/08 05:53:28 All Rights Reserved.
14/02/08 05:53:28 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
14/02/08 05:53:28 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
14/02/08 05:53:28 Desktop name 'X' (MythTV:9)
14/02/08 05:53:28 Protocol version supported 3.3
14/02/08 05:53:28 Listening for VNC connections on TCP port 5909
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/home/username/.Xresources'

** (x-window-manager:6116): WARNING **: The display does not support the XRender extension.

** (x-window-manager:6116): WARNING **: The display does not support the XRandr extension.

** (x-window-manager:6116): WARNING **: The display does not support the XComposite extension.

** (x-window-manager:6116): WARNING **: The display does not support the XDamage extension.

** (x-window-manager:6116): WARNING **: The display does not support the XFixes extension.

** (x-window-manager:6116): WARNING **: Compositing manager disabled.
** Message: Querying Xkb extension
** Message: Your X server does not support Xkb extension
Xlib:  extension "RANDR" missing on display ":9.0".
Xlib:  extension "XFree86-VidModeExtension" missing on display ":9.0".
alsa: error: master control not found. I even tried to guess wildly, but to no avail.
alsa: info: developer information follows: (send E-Mail to Developer with that)
alsa: * Headphone,0
alsa: * Front,0  <--- hint hint
alsa: * Front Mic,0  <--- hint hint
alsa: * Surround,0  <--- hint hint
alsa: * Center,0  <--- hint hint
alsa: * LFE,0  <--- hint hint
alsa: * Side,0  <--- hint hint
alsa: * Line,0  <--- hint hint
alsa: * Mic,0  <--- hint hint
alsa: * Capture,0
alsa: * Capture,1
alsa: * Input Source,0
alsa: * Input Source,1
alsa: info: end of developer information
** Message: This build doesn't include support for XF86Misc extension
** Message: Querying Xkb extension
** Message: Your X server does not support Xkb extension


And after I kill the VNC session, there is this added to the log file:

> 
The application 'x-window-manager' lost its connection to the display :9.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'xfce-mcs-manager' lost its connection to the display :9.0;
most likely the X server was shut down or you killed/destroyed
the application.

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800046 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800038 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800045 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800044 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800043 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800042 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800041 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x180003d unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x180003c unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800033 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x180000e unexpectedly destroyed
The application 'xfce4-terminal' lost its connection to the display :9.0;
most likely the X server was shut down or you killed/destroyed
the application.


Here is my /var/log/dpkg.log file. I am not sure if it is relevant:
> 
2008-02-14 04:17:39 upgrade linux-image-2.6.22-14-generic 2.6.22-14.51 2.6.22-14.52
2008-02-14 04:17:39 status half-configured linux-image-2.6.22-14-generic 2.6.22-14.51
2008-02-14 04:17:39 status unpacked linux-image-2.6.22-14-generic 2.6.22-14.51
2008-02-14 04:17:39 status half-installed linux-image-2.6.22-14-generic 2.6.22-14.51
2008-02-14 04:17:45 status half-installed linux-image-2.6.22-14-generic 2.6.22-14.51
2008-02-14 04:17:46 status unpacked linux-image-2.6.22-14-generic 2.6.22-14.52
2008-02-14 04:17:47 status unpacked linux-image-2.6.22-14-generic 2.6.22-14.52
2008-02-14 04:17:47 upgrade libpq5 8.2.6-0ubuntu0.7.10.1 8.3.0-1~gutsy1
2008-02-14 04:17:47 status half-configured libpq5 8.2.6-0ubuntu0.7.10.1
2008-02-14 04:17:47 status unpacked libpq5 8.2.6-0ubuntu0.7.10.1
2008-02-14 04:17:47 status half-installed libpq5 8.2.6-0ubuntu0.7.10.1
2008-02-14 04:17:48 status half-installed libpq5 8.2.6-0ubuntu0.7.10.1
2008-02-14 04:17:48 status unpacked libpq5 8.3.0-1~gutsy1
2008-02-14 04:17:48 status unpacked libpq5 8.3.0-1~gutsy1
2008-02-14 04:17:48 upgrade linux-libc-dev 2.6.22-14.51 2.6.22-14.52
2008-02-14 04:17:48 status half-configured linux-libc-dev 2.6.22-14.51
2008-02-14 04:17:48 status unpacked linux-libc-dev 2.6.22-14.51
2008-02-14 04:17:48 status half-installed linux-libc-dev 2.6.22-14.51
2008-02-14 04:17:48 status half-installed linux-libc-dev 2.6.22-14.51
2008-02-14 04:17:48 status unpacked linux-libc-dev 2.6.22-14.52
2008-02-14 04:17:48 status unpacked linux-libc-dev 2.6.22-14.52
2008-02-14 04:17:48 startup packages configure
2008-02-14 04:17:48 configure linux-image-2.6.22-14-generic 2.6.22-14.52 2.6.22-14.52
2008-02-14 04:17:48 status unpacked linux-image-2.6.22-14-generic 2.6.22-14.52
2008-02-14 04:17:48 status half-configured linux-image-2.6.22-14-generic 2.6.22-14.52
2008-02-14 04:18:02 status installed linux-image-2.6.22-14-generic 2.6.22-14.52
2008-02-14 04:18:02 configure libpq5 8.3.0-1~gutsy1 8.3.0-1~gutsy1
2008-02-14 04:18:02 status unpacked libpq5 8.3.0-1~gutsy1
2008-02-14 04:18:02 status half-configured libpq5 8.3.0-1~gutsy1
2008-02-14 04:18:02 status installed libpq5 8.3.0-1~gutsy1
2008-02-14 04:18:02 status triggers-pending libc6 2.6.1-1ubuntu10
2008-02-14 04:18:02 configure linux-libc-dev 2.6.22-14.52 2.6.22-14.52
2008-02-14 04:18:02 status unpacked linux-libc-dev 2.6.22-14.52
2008-02-14 04:18:02 status half-configured linux-libc-dev 2.6.22-14.52
2008-02-14 04:18:02 status installed linux-libc-dev 2.6.22-14.52
2008-02-14 04:18:02 trigproc libc6 2.6.1-1ubuntu10 2.6.1-1ubuntu10
2008-02-14 04:18:02 status half-configured libc6 2.6.1-1ubuntu10
2008-02-14 04:18:05 status installed libc6 2.6.1-1ubuntu10
2008-02-16 01:27:56 upgrade xserver-xorg-video-intel 2:2.1.1-0ubuntu9 2:2.1.1-0ubuntu9.1
2008-02-16 01:27:56 status half-configured xserver-xorg-video-intel 2:2.1.1-0ubuntu9
2008-02-16 01:27:56 status unpacked xserver-xorg-video-intel 2:2.1.1-0ubuntu9
2008-02-16 01:27:56 status half-installed xserver-xorg-video-intel 2:2.1.1-0ubuntu9
2008-02-16 01:27:56 status half-installed xserver-xorg-video-intel 2:2.1.1-0ubuntu9
2008-02-16 01:27:56 status unpacked xserver-xorg-video-intel 2:2.1.1-0ubuntu9.1
2008-02-16 01:27:56 status unpacked xserver-xorg-video-intel 2:2.1.1-0ubuntu9.1
2008-02-16 01:27:56 startup packages configure
2008-02-16 01:27:56 configure xserver-xorg-video-intel 2:2.1.1-0ubuntu9.1 2:2.1.1-0ubuntu9.1
2008-02-16 01:27:56 status unpacked xserver-xorg-video-intel 2:2.1.1-0ubuntu9.1
2008-02-16 01:27:56 status half-configured xserver-xorg-video-intel 2:2.1.1-0ubuntu9.1
2008-02-16 01:27:56 status installed xserver-xorg-video-intel 2:2.1.1-0ubuntu9.1
2008-02-16 01:27:56 status triggers-pending libc6 2.6.1-1ubuntu10
2008-02-16 01:27:56 trigproc libc6 2.6.1-1ubuntu10 2.6.1-1ubuntu10
2008-02-16 01:27:56 status half-configured libc6 2.6.1-1ubuntu10
2008-02-16 01:27:59 status installed libc6 2.6.1-1ubuntu10



---

### Post by joosteto on 2008-04-02
```
ssh server.address.com -L 5900:server.address.com:5909
```
That seems OK, and works for me.

It could be that the server is behind a firewall, and doesn't have a network interface with adress server.address.com. If so, you could try:
```
ssh server.address.com -L 5900:localhost:5909
```

It could also be that the server has a firewall, that blocks porrt 5909. You could try by typing "telnet server.address.com 5909" or "telnet localhost 5909" on the server (If you see gibberish like "RFB 003.008", you can connect. If the connection just sits there "Trying", or receives connection refused, you eigther have a firewall, or vncserver isn't started properly).

You could also try typing "telnet localhost 5900" on the client, that should give the same output as "telnet localhost 5909" on the server.

---

