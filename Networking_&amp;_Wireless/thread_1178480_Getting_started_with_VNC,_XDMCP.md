---
title: "Getting started with VNC, XDMCP"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by sfl on 2009-06-04
Hi there, 

While I've used VNC before, it's only been in the most basic of ways from windows to windows with the server desktop being logged-in already. Now I've got a fresh Jaunty install but it's not always connected to a screen (TV is sometimes in use when I need it). 

I'd like to set things up to enable connecting via VNC to  Jaunty when nobody is logged-in to a desktop and this while taking advantage of Jaunty's built-in VNC capabilities as much as possible. I know I can cook my own solution but I figure Vino is included for a reason and if it can be configured to do what I want I'd prefer doing that than going against the integrated tools. 

I've seen a few references about this online but I believe this might have been before Vino was included with Ubuntu or when there were still quirks with the way it worked out of the box. 
I don't mind doing some reading on the subject but I'd first like to know what I should be able to do out of the box with Vino and what it's relation to Xvnc and VNC is. 

Any help or pointers to docs (yes I don't mind RTFM as long as I have the *Right*FM ;-) ) would be greatly appreciated.

---

### Post by jamie0nz on 2009-07-15
This is something of a frustration to me also.

I am going to start by summarizing the concepts. A unix box does not need windows running on it, and when some windows are present, there does not need to be just one and it does not need to be running on the box itself.

The vinagre solution seems Windows(MS) in conception, it shares a window you already have running on the box. What if you want to create a window as your remote log in? This is where XDMCP is really cool, BUT I don't want extra software on my Windows boxes to get at this stuff other than vnc which I use all over the place.

How to proceed, Xvnc fits in between XDMCP and VNC to present the XDMCP as a VNC host. Xinetd is required to serve up the socket to achieve it.

There are heaps of threads on the issue and may be even one or two solutions, so I started with this one [https://bugs.launchpad.net/ubuntu/+bug/363519](https://bugs.launchpad.net/ubuntu/+bug/363519)

OK, so far so good, vncviewer [box address]:1 serves up a bare xserver screen (which you'd recognise and the bare bones x display if you've been around too long).

The last piece of the puzzle popped up in [http://ubuntuforums.org/showthread.php?t=1128225&page=2](http://ubuntuforums.org/showthread.php?t=1128225&page=2) where d1mag said to change the Xvnc xinet.d config to -query 127.0.0.1 instead of localhost to avoid the ipv6 problem.

So right now I have a greeter screen on the box itself (no windows running) and on a remote box by doing vncviewer [box address]:1 once and then vncviewer [box address]:1 a second time I have two independent client screens running.

Very cool. In fact superb I am really happy with this.

ETA: the wait=yes alternate is interesting too ... the one wrinkle I have noticed so far is that the greeter on the host box dissappeared ... I wonder why

---

### Post by jamie0nz on 2009-07-15
wait=yes ties the vnc port as if it were a single workstation, this is all very well but ...

wait=no means several different people can log in at the same time, or that you can log in several different times.

wait=yes means you can start a process in the window and disconnect, coming back later to see how it is going, though I am unsure how long wait waits :).

---

