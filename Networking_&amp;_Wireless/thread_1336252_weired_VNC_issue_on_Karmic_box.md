---
title: "weired VNC issue on Karmic box"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by eaglepeng on 2009-11-24
I got a weird thing on my Karmic box. My VNC is kind of working.  I have two ports almost having identical setup. One is working, one is not. Here's my set up. It is hooked under Xinetd.


service Xvnc-p1
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = xp1
        server = /usr/bin/Xvnc
        server_args = -inetd :2 -query localhost -geometry 1152x864 -depth 16 -once -desktop MediaStudio(xp1) -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared -rfbauth /home/xp1/.vnc/passwd -extension XFIXES
         port = 5902
}

service Xvnc-p2
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = xp2
        server = /usr/bin/Xvnc
        server_args = -inetd :3 -query localhost -geometry 1152x864 -depth 16 -once -desktop MediaStudio(xp2) -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared -rfbauth /home/xp2/.vnc/passwd -extension XFIXES
         port = 5903
}

p2 always works. I can directly connect to this port or through a ssh tunnel. I always got "no password configured for vnc auth" for p1. the ssh tunnel doesn't work either. But if I login the box through an ssh terminal, then the p1 VNC worked. I tired change the user to be root for p1. I got the same result. I'm sure about that the password file is not empty because I check it and use vncpasswd to fill it again.Anyone can help me to figure out why p1 doesn't work?

---

