---
title: "VNC Server/Client - need speed"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by ripken204 on 2009-07-05
i am running ubuntu 9.04 64bit and win7 64bit.
the server is ubuntu and the client is win7.
they are on a gigabit network.

i am currently using the default vnc server that ubuntu has, i believe that is vino?

the clients i have tried are realvnc, tightvnc, and ultravnc.
all three of them just dont seem like they are fast enough, especially over a gigabit network. very laggy..

what i want to know is what is the most optimal setup for over a gigabit network. i am up for trying different vnc servers, i just want speed. what should i try?

---

### Post by pytheas22 on 2009-07-05
Which VNC server software are you using?  Did you simply go to System>Preferences and enable your desktop to be shared, or did you install a VNC server package like vnc4server?  As far as I know, vino is just a VNC client.

I ask because I set up vnc4server on Ubuntu 8.04 about six months ago and experienced severe speed issues.  Even on my local 10-gigabit network, screen redraw rates were very slow.  As I recall, this was due to an upstream bug in the vnc4server software.  I don't know if this issue still exists in Ubuntu 9.04, but it's possible.

I worked around the problem by installing a more recent version of the software.  I couldn't find a .deb package, so I used a Fedora 10 RPM package.  alien couldn't t convert the RPM properly, so I ended up having to take it apart and copy the binaries manually into the appropriate directories in Ubuntu.  This was tedious, but it significantly improved speed.

So I'd recommend that you check the version of your VNC server software and google a bit to see if you're affected by the same issue I was.

You could also consider an alternative to VNC like [FreeNX]("https://help.ubuntu.com/community/FreeNX").

---

### Post by ripken204 on 2009-07-05
yes i did go into System>Preferences....

i will check those out, thanks.

---

### Post by ripken204 on 2009-07-05
wow freenx is fast.
the only thing that i dislike is how you have to have a different session.
is there a way to join the current session thats running on the server?

---

### Post by pytheas22 on 2009-07-05
I don't know anything about FreeNX as I've never actually used it, so I'm not sure if there's a way to make it forward your current session.  You might want to start a new thread on that topic if no one responds here and you can't find an answer via Google.

---

