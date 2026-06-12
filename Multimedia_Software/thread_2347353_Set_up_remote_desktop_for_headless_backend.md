---
title: "Set up remote desktop for headless backend"
date: 2016-12-23
forum: Multimedia Software
---

### Post by ashtangiman on 2016-12-23
I have installed MythBuntu on an older MacMini and set it up as a backend only.  I am not sure what I am doing wrong, but i installed vnc4server, and my main computer (mac os) cannot connect using vnc://xxx.xxx.xxx.xxx (go to server from finder).  The error tells me to configure desktop sharing on the remote computer.  On the MythBuntu box (with monitor and keyboard plugged in) there is no desktop sharing in the system panels that I have found.  What can I do to get this working?  I can successfully ssh using the same ip address that doesn't work so I know the system is reachable.

Thanks for any help.  Paul

---

### Post by TheFu on 2016-12-24
Apple calls things by non-standard names, which confuses non-Apple users. Also, I've never seen vnc:// used anywhere, ever. Doesn't mean that won't work, just that I've never seen it.

For remote desktops, I use x2go.  It uses the same ssh you already have setup for the tunnel AND authentication (handy if you have ssh-keys working). There are x2go clients for the 3 main desktop OSes (Linux, Windows, OSX). It is about 2-3x faster than VNC and safe to use from anywhere in the world, if ssh-keys are used for authentication.

Install and configure ssh on the server and clients - you've done this already.
Install the x2go server on the Ubuntu machine: [http://wiki.x2go.org/doku.php/doc:installation:x2goserver](http://wiki.x2go.org/doku.php/doc:installation:x2goserver)
Install the x2go client on the Mac: [http://wiki.x2go.org/doku.php/doc:installation:x2goclient](http://wiki.x2go.org/doku.php/doc:installation:x2goclient)

The "server" needs to have a lite-desktop loaded. NOT Unity, so xfce, lxde, would be the normal DEs most people would load.  This is important for key-bindings to work correctly.  Other environments can also work, I use straight openbox, but for a 1st-time x2go user, getting something working first is important.  People coming from VNC say x2go is like walking into daylight after being in the darkness of VNC. ;)

For Windows clients, installing the x2go-fonts is recommended. Don't know about OSX.

I know the Windows and Linux x2go clients are extremely stable.

If you need support for VNC (using android/iPad), then I cannot help. Sorry. Haven't used VNC in about 6 yrs, but I vaguely remember there were about 5 steps necessary to get it working from the server-side.

---

