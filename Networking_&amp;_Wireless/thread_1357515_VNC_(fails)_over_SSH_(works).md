---
title: "VNC (fails) over SSH (works)"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by rafalr on 2009-12-17
Hi,

I am trying to connect from a laptop with Ubuntu 9.04 LXDE (plus some Gnome applications) to my home PC running Ubuntu 9.04 (Gnome).

I did forward port 2222 to my local IP on the router while on the firewall I opened both 2222 to incoming SSH service and port 5900 to localhost.

I configured SHH to open tunnell using private/public key. 

```
ssh -C 82.160.xxx.xxx -p 22222 -L 5900:localhost:5900 -l rafa
```

This works well and I can see my home PC, use command line, install programmes from commandline etc.

But any attempt to use graphic mode of desktop access fails. 

Launching any application from command line renders an error: 
> Gtk-WARNING **: cannot open display: 
Tried this with simplest applications like gedit or gnome-commander.

Upon launching x11vnc server, that reports:

> The VNC desktop is:      Rafal-AMD:1
PORT=5901

But after starting vinagre this works, but I can only see black screen.
Another client - xvnc4viewer reports an error "unable to connect to host: Connection refused (111)"
Launching vncviewer reports immediately after attemt to connect that "your connection has been closed"

Instead of the x11vnc I tried to use vncserver:

```
vncserver -geometry 1024x768 -depth 24 -fp /usr/lib/X11/fonts/misc/
```

but with the same result - black screen in vinagre, refused connection in other clients.

Any ideas how to work this out ?

rafal

---

### Post by krunge on 2009-12-17
For running X apps over your ssh link, e.g. gedit, you probably need to add the "-X" or "-Y" option to the ssh cmdline to enable X11 forwarding.

For accessing x11vnc via your ssh link, note that x11vnc says he is using port 5901.  This means something else has already taken port 5900 (vino or vncserver?)  So your port redir "-L 5900:localhost:5900" won't reach x11vnc on 5901.

When you run x11vnc, be sure to specify "-display :0" ( I assume your desktop is X display :0 ) on its cmdline. That way you explicity tell it to use that display instead of accidentally using $DISPLAY which might be set for your ssh X11 forwarding (i.e. the desktop you are sitting at, not the remote desktop.)

Note that x11vnc attaches to the physical display (i.e. one on the graphics hardware.)  If you only want a virtual (RAM-only) desktop use vncserver. 

(PS: x11vnc has the -create option that will also create RAM-only/virtual desktops; it requires the "xvfb" package.)

---

### Post by doas777 on 2009-12-17
instead of configuring a local ssh tunnel, try this (with no tunnel established)
```

vncviewer -via user@sshserver:sshprt localhost:0

```

---

### Post by rafalr on 2009-12-18
Hi, Krunge. It seems you know what you are talking about - I am still learning ...

One question: what is the practical difference between using X (X11 forwarding) and Y (trusted forwarding) ?

As far as x11vnc starting with port 5901 not 5900. I always started the server with -display :0, but you were right, something was taking the display 0: already. It was my first attempt like that so I thought I will first try launching some VNC server on home PC to be sure it is up and running when I try to access it from remote location; later on, after successfull connecting with SSH I found that running VNC client does not do the job and I first need to start the VNC server from remote location, thus most likely I had two active VNC servers running on home PC; later on I tried to kill both and start anew, but I am not sure if it worked.

I am still bit confused: if I use the System -> Remote Desktop and do the appropriate settings opening the desktop for remote access, does this automatically start vino server ? Or it is just setting some configuration options for VNC server which needs to be started manually, for example from remote location ?

Again, to be sure of properly aligning ports made available by SSH and later on used by VNC server, it would seem I first need to open SSH tunnel (to whichever port like 5900), then run VNC server to see which port/display it makes available, then shut down SSH and re-open it with a proper port number (aligned to the one VNC server wants to make available).
Seems a bit stupid ...

> 
Note that x11vnc attaches to the physical display (i.e. one on the graphics hardware.)  If you only want a virtual (RAM-only) desktop use vncserver. 

(PS: x11vnc has the -create option that will also create RAM-only/virtual desktops; it requires the "xvfb" package.)

Sorry, I am not getting this - what is the difference and why would you prefer to use hardware display on some occasions and virtual on others ?

Rafal

---

### Post by Lars Noodén on 2009-12-18
> **rafalr said:**
> 
One question: what is the practical difference between using X (X11 forwarding) and Y (trusted forwarding) ?


Neither are relevant for tunneling vnc.  However, -X and -Y are similar in that the both give all kinds of access to your system via X.  -Y gives more.  

Here is a very old write up of what's going on.  There have been some improvements since then:
[http://snakeoil.de/gcih.pdf](http://snakeoil.de/gcih.pdf)

> **rafalr said:**
> 
I always started the server with -display :0, but you were right, something was taking the display 0: already. 


Yes you have to forward the right ports so that they match the displays. For display 0 it should be port 5900 and you'll have to tell the vncviewer to connect to 0.  Or set up display one on the remote machine and forward port 5901.  

Or, a third choice, if you want to be tricky, is to have different ports on the ends of the tunnel so that you have display 0 on the remote machine and display 1 on the local machine:

```

# display :0 on the remote, display :1 locally
ssh -CNTnq -l rafa -L 5901:localhost:5900 82.160.xxx.xxx

```

That should address the specific situation described in the original question.

---

### Post by krunge on 2009-12-18
> 
One question: what is the practical difference between using X (X11 forwarding) and Y (trusted forwarding) ?

Yes, as Lars points out, they both allow X11 forwarding but -Y is less secure because it allows the X11 clients (apps) to do more.  Sometimes "do more " means simple things like copy-n-paste the selection so I usually recommend -Y to people unless they have a reason to be paranoid.
> 
I am still bit confused: if I use the System -> Remote Desktop and do the appropriate settings opening the desktop for remote access, does this automatically start vino server ? Or it is just setting some configuration options for VNC server which needs to be started manually, for example from remote location?
In GNOME 'System -> Remote Desktop' will start the GNOME program vino. Nothing to do with x11vnc.  In KDE there is a similar menu item that will start krfb.
> 
Again, to be sure of properly aligning ports made available by SSH and later on used by VNC server, it would seem I first need to open SSH tunnel (to whichever port like 5900), then run VNC server to see which port/display it makes available, then shut down SSH and re-open it with a proper port number (aligned to the one VNC server wants to make available).
Seems a bit stupid ...

Assuming you want x11vnc (I'm not sure if you do) you can supply, e.g. "-rfbport 5908" to its cmdline, to try to stay away from other vncservers.  Then x11vnc will only use that port, and you can put "-L 5900:localhost:5908" in your ssh cmd. 

The companion viewer to x11vnc, named ssvnc, can use ssh's dynamic SOCKS proxy (-D option) to dynamically attach to the PORT=NNNN that x11vnc prints out.  If you try ssvnc this way, I recommend its "Terminal Services" mode that sets this up automatically for you. 
> 
Sorry, I am not getting this - what is the difference and why would you prefer to use hardware display on some occasions and virtual on others ?

Think of Terminal Services.  E.g. you might have 10 or 20 users with desktops on a server machine simultaneously. These desktops need to be virtual: they can't all use the graphics hardware at the same time.

Regarding wanting to attach to the X display (desktop) on the physical graphics hardware: suppose you left work with an important document unfinished and unsaved and you need to send it out tonight.  You connect with x11vnc and finish it.  Or you are at your X workstation and you decide it is a nice day and you want to work out on the deck for a while, but you don't want to restart all of your applications and etc.  You take your laptop out to the deck and connect to your workstation via x11vnc.  I do this all the time, and will do so again starting in next May or so!

---

### Post by rafalr on 2009-12-21
> Assuming you want x11vnc (I'm not sure if you do) you can supply, e.g. "-rfbport 5908" to its cmdline, to try to stay away from other vncservers. Then x11vnc will only use that port, and you can put "-L 5900:localhost:5908" in your ssh cmd.

I would use whichever server, but I hear x11vnc is gnome/kde independent, so would rather use it. 

Do I need the port on remote machine (here 5908) opened in firewall for localhost ? If so, then atually I first need access to local machine and pre-open this port before I can tell x11vnc to use at and later on the vnc client to use it, too ...

I am asking, because:

> In GNOME 'System -> Remote Desktop' will start the GNOME program vino

So if I once have this set, then each time I start PC the vino server is running and taking port 5900. Which would be bad, because I already set my firewall to pass only port 5900 for local host, so any other port taken by other server will possibly be blocked, I assume ...

R.

---

### Post by krunge on 2009-12-21
> 
So if I once have this set, then each time I start PC the vino server is running and taking port 5900. Which would be bad, because I already set my firewall to pass only port 5900 for local host, so any other port taken by other server will possibly be blocked, I assume ...
I think that once enabled via the menu vino will **only** start up once that user has logged into his X session desktop.  Before that, i.e. when the login greeter is up, there is no vino running.

You can check this easily by running ps(1) and netstat(1) in a shell before anyone has logged into the desktop.

---

### Post by krunge on 2009-12-21
> 
Do I need the port on remote machine (here 5908) opened in firewall for localhost ? If so, then atually I first need access to local machine and pre-open this port before I can tell x11vnc to use at and later on the vnc client to use it, too ...

Since you are using an SSH tunnel to access the the VNC server, there is **no need at all** to open any of the 590* ports in your firewall.  You just need it to let in SSH.

In addition to the "-rfbport 5908" I suggested, you might as well add "-localhost" to x11vnc's cmdline. That way the VNC can only be accessed locally (i.e. thru your SSH tunnel.)

So modifying the example you provided:
```

ssh -C 82.160.xxx.xxx -p 22222 -L 5900:localhost:5908 -l rafa "x11vnc -display :0 -rfbport 5908 -localhost"

and then start vncviewer somehow pointed at localhost:0

```

---

