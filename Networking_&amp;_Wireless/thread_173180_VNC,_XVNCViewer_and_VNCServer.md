---
title: "VNC, XVNCViewer and VNCServer"
date: 2006-05-09
forum: Networking &amp; Wireless
---

### Post by NeoGreen on 2006-05-09
I want to install VNC on my Ubuntu machine, but when I run the command sudo apt-get install VNC I get this message a message stating that the package VNC has no installation candidate.  What does that mean?:confused:

---

### Post by brentoboy on 2006-05-10
do you want to install vnc in order to view a differnt PC (as a client), or do you want to allow other PCs to log into yours (as a server)?

open synaptic, and search for VNC
that will show all the available vnc packages (both client and server)

I belive that the remote desktop option that comes installed on a fresh ubuntu install can open a remote VNC session (making it a client)

but I have never setup my ubuntu box as a vnc server

---

### Post by NeoGreen on 2006-05-10
I want to be able to view other PC.  this is what I did, I installed VCN on a Fedora Core 5 computer, I then used VCN to get to my Ubuntu computer, which it did.  Now I want to be able to get to my Fedora Core computer from my ubuntu computer.  You said that there is a VCN program automatically installed on  Ubuntu, but how can I run it?](*,)

---

### Post by brentoboy on 2006-05-15
the vncviewer is installed by default.

alt+f2 (opens the run command window)
xvncviewer

im not sure why I cant find it in the apps menu, it was there last time I looked for it.

---

### Post by aysiu on 2006-05-15
Assuming [you have the Universe repositories enabled](http://www.psychocats.net/ubuntu/sources), try pasting these commands into the terminal: ```
sudo apt-get update
sudo apt-get install xtightvncviewer
xvncviewer
```

---

