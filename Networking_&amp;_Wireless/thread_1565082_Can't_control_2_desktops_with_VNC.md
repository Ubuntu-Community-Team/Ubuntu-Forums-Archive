---
title: "Can't control 2 desktops with VNC"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by IndyGunFreak on 2010-08-31
I think this is the right forum for this, if not, I'd appreciate it being moved.  I hope I've included enough info below, if not, ask and I'll provide additional details.

Network:
1 XP wireless desktop
1 Ubuntu 10.04 wireless laptop
2 Ubuntu 10.04 wired desktops
All updates are current on all of them.

Router:  WNDR3300 - Right now, all ports are closed, as I don't want access to them from the outside.  However, I've tested w/ port 5900 forwarded to the two problem machines, and coming in through my IP address, and it didn't change anything.

Success: I can connect to all the boxes, from any other machine on the network using tightvncserver and xtightvncviewer or tsc.  I can "control" the XP desktop and the Ubuntu laptop from any machine on the network.  

Problem: When trying to control to two Ubuntu desktops.  They just do not respond, and it's like looking at a frozen screen.  After clicking the menu, right clicking desktop, etc... nothing happens on my screen, but it appears to be happening on the remote machine.  Example: If I click the Application menu or open a folder on the machine I've VNC'd into, nothing happens locally(where I'm sitting).  However if I get up and walk to the machine, I can see on the desktop the things I've done(open folders or if I left a menu open, etc..)...

The 3 Ubuntu machines have exactly the same vnc programs installed on them, and I just can't figure out why this is happening.  FWIW, the same thing also happens when I use Ubuntu's "remote desktop" program.  I have tried all 3 protocols under TSC, w/ the same results(VNC, RDP, RDPv5).  As one final test to try this, I downloaded the free version of TeamViewer, and put it on my Ubuntu laptop, and the problem desktops.  Using Teamviewer, gives me control of the problem desktops.

I hope that is clear enough, I'd appreciate any insight as to what the problem could be.

IGF

---

### Post by IndyGunFreak on 2010-08-31
One other bit of interesting info...

One one of the Ubuntu PC's, I have Virtualbox installed, and XP as a VMachine.  I set up Virtualbox to call for it's own IP address from the router, and installed TightVNC inside Virtual XP.

I can control the Guest XP on that PC, but not host Ubuntu..

IGF

---

