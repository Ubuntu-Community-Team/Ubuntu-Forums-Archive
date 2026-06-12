---
title: "Remmina RDP can't connect"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by roadlesstraveled on 2011-09-12
OS:  Ubuntu 11.04 64-bit
Connecting To:  Win7 Ultimate 64-bit

I have successfully installed Remmina but can't seem to get RDP working.  The profile has the following settings:
User Name:  username for my windows client
Password:  pass for my windows client
Domain: <ip address>:<port> (the port is forwarded)
Resolution:  1024x768
Color Depth:  256 colors

Advanced
Quality:  Good
Sound:  Off

I've used the same domain, username, and password successfully with a computer running the same version of windows.
Any ideas on what the problem is?

Any help would be greatly appreciated.

---

### Post by poolet on 2011-09-13
Why you are trying to connect via RDP ?? Did you try via VNC??

---

### Post by smurphy_it on 2011-09-13
Check your windows7 box you are trying to connect to.  For RDP and windows 7 it has an extra layer of security.  Of course, you can't use this extra layer of security with linux, as it's MS Proprietary.

I don't have a win7 box here to look at, but it should be under your network settings somewhere.

---

### Post by dennis1200 on 2011-10-27
I am also having trouble with this one. First, I should recommend never doing straight RDP for security reasons. It should be in an SSH tunnel. And I'm trying to figure out how to setup Remmina to do that. I'm currently combining putty for the tunnel and tsclient for the rdp. Here's my setup:
Ubuntu 11.10 accessing remote XP computer
Remote computer IP linked to DynDNS address (name:XXXX)
Remote router forwards port DynDNS:XXXX to remote-computer:ZZZZ
Putty connects to SSH at DynDNS:XXXX and forwards localhost:YYYY to remote-computer:ZZZZ - the latter part of this is the step I'm having most trouble with
SSH is authenticated with a password-protected key file pair - also having trouble with this, but that may be the previous step 

localhost:YYYY needs to be mapped to remote:ZZZZ, but I don't see how to do that in Remmina. It's nowhere near as configurable as putty, but this seems like a key part of SSH configuration. Any help is appreciated, since I don't like tsclient that much (but it works!)

---

### Post by collisionystm on 2011-10-27
Do you have network level authentication enabled?

Open start menu

RIGHT CLICK on COMPUTER

Go to properties

Go to advanced settings on the left

Go to REMOTE tab

Choose 

ALLOW REMOTE DESKTOP FROM COMPUTERS RUNNING ANY VERSION OF REMOTE DESKTOP

---

### Post by collisionystm on 2011-10-27
Did that work? If so please mark this solved.

---

