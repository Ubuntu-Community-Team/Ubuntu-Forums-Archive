---
title: "More VNC Questions"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by bkg-22 on 2009-12-20
I have been lurking in the shadows in these forums for about a year and have made great progress with other Ubuntu based projects - my most useful being a NAS server and print server.  Has been rock solid thanks to all the input I have found from other people doing the same thing.  Thanks to ALL of you.

New project - different objective - and I have been through so many discussions and threads now that it makes my head swim.  Either the specifics do not apply to my version of Ubuntu or the solutions that do work don't really meet my objective.  So, i am really hoping someone can pick this up where other threads leave off.
[SIZE=4][B]
My Env:[/B][/SIZE]
Ubuntu 9.10 - fresh install
Windows XP desktop clients

[SIZE=4]**My Objective:**[/SIZE] To setup a VNC "type" server I can access from anywhere I have internet access - like I have used for so long in a Microsoft env.
1.  I travel for business quite a lot - so I would like to build a headless server I just mount in a wiring closet and forget about it.  Specifically, if it gets rebooted, I may not have access to it to manually start any special tasks or services.
2.  I do not want to depend on having an existing session already running before the VNC server is accessible remotely (i.e. vino will not work)
3.  I need to access a full blown remote desktop env remotely - not just a terminal session.  For testing purposes, just access from my LAN, but eventually this would be via the internet.  I know there will be security issues to deal with (Openssh, putty, etc) but I will take it one step at a time for now.
4. I already have apps installed and running nicely under gnome, so would prefer to have that as the default desktop env unless there is a compelling reason to change.
5. All clients will be Windows XP Pro and higher (Vista, Win7, etc)
[SIZE=4][B]
Tried so far:[/B][/SIZE]
**Vino** - worked great - except it appears a user has to be logged in locally before you can access remotely.  Does not meet primary objective.
**x11vnc** - looks promising as i can get a gnome login screen from a remote Windows box, but when trying to login remotely, the connection is reset at the server (or so it appears).  I have hours into trying various x11vnc startup options, xauth security variations, and it just gets worse, not better.
**vncserver** (tightvnc) - Honestly, I forget the nature of the problems I experienced, but again, I had hours into research, testing and failing due to various issues encountered.

I have read a fair amount about x11vnc, and have played the most with it.  It seems so close - but just not there.

I know there has to be folks out there that have had to do the same thing I have.  This is not rocket science.

Any suggestions would be very much appreciated!

---

### Post by bkg-22 on 2009-12-20
Well, i no more than typed this all up and I stumble across this:
[http://ubuntuforums.org/showthread.php?t=1128225&page=2](http://ubuntuforums.org/showthread.php?t=1128225&page=2)

> Step by step, here's what I did:

**1) Install xinetd and vnc4server** (sudo apt-get install xinetd vnc4server)

**2) Add xinetd service for Xvnc:**

Create new file /etc/xinetd.d/Xvnc with contents:

     Code:
     service Xvnc
{
  socket-type = stream
  protocol = tcp
  wait = no
  user = nobody
  server = /usr/bin/Xvnc
  server_args = -inetd -once -query localhost -SecurityTypes None -geometry 1024x768 -depth 24 -extension XFIXES
  type = UNLISTED
  port = 5900
  disable = no
} 
Including the "-extension XFIXES" arg was critical; otherwise the VNC window would flash a black screen (briefly) and then quit.

**3) Disable IPv6:**

Create new file /etc/modprobe.d/no-ipv6.conf with contents:
     Code:
     alias net-pf-10 off 
**4) Reboot.**This seems to work although now one of the apps I am trying to run remotely has an issue of screen resolution via an X server - thus the app window is black.  But that is another issue altogether for now.

So, to billycub, I thank you!  :)

---

### Post by krunge on 2009-12-25
> 
**x11vnc** - looks promising as i can get a gnome login screen from a remote Windows box, but when trying to login remotely, the connection is reset at the server (or so it appears).  I have hours into trying various x11vnc startup options, xauth security variations, and it just gets worse, not better.

Well, it sounds like you are set, but for the record for anyone searching the forums: There are a number of bugs in Xorg and GDM that cause Xorg crashes after the user logs in; this is in addition to GDM's **default** behavior of killing all connected X apps (x11vnc included) right after the user logs in.  More info at these links for workarounds and upstream fixes:

[INDENT][http://ubuntuforums.org/showthread.php?t=1346895](http://ubuntuforums.org/showthread.php?t=1346895)
[http://ubuntuforums.org/showthread.php?t=1306696](http://ubuntuforums.org/showthread.php?t=1306696)
[http://ubuntuforums.org/showthread.php?t=965695](http://ubuntuforums.org/showthread.php?t=965695)[/INDENT]

---

