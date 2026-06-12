---
title: "Remote Desktop"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by Mr.Dee on 2011-07-06
I have an Ubuntu netbook and an Ubuntu desktop.  I occassionaly need to do CPU intensive work on a file.  I would like to be able to send files from my netbook to my desktop and then provide instructions remotely to my deskop.  
 
I did a good chunk of googlin and have tried a few things, but got stuck at some point... I tried dyndns, openvpn, openssh and port forwarding my router... I really am close to figuring this out and would appreciate any good tutorials/references to documentation on this.  I am going to give this another go, wish me luck.  Thanks in advance for your help.

---

### Post by perspectoff on 2011-07-06
I like to use WebDAV.

It mounts as a folder in Dolphin or Nautilus and can be accessed like a system folder from either system. 

cf.

[http://www.kubuntuguide.info/index.php/Natty#WebDAV](http://www.kubuntuguide.info/index.php/Natty#WebDAV)

or 

[http://ubuntuguide.org/wiki/Ubuntu:Natty#WebDAV](http://ubuntuguide.org/wiki/Ubuntu:Natty#WebDAV)

As to remote access, you need VNC tunneled through SSH, or FreeNX.

Possibly the new iterations of VNC have encryption built-in, but I'm not sure. (I feel my bones creaking.)

---

### Post by CVGH on 2011-07-06
VNC/VINO has no encryption. 
Tunnel thru SSH is the only way.
If 5900 is open to the world, look out.....

---

### Post by smurphy_it on 2011-07-06
OpenVPN (Natted I think they call it) - so it's connection to one machine, and not the entire network.
Then openssh to login and do whatever work needs doing.

---

### Post by perspectoff on 2011-07-06
> **CVGH said:**
> VNC/VINO has no encryption. 
Tunnel thru SSH is the only way.
If 5900 is open to the world, look out.....

Now I remember. I thought I read that TightVNC now encrypts its VNC connections so that an SSH tunnel is not required when using it.

I think both a recent TightVNC server and client are required for that (just like FreeNX).

Server:
 sudo apt-get install tightvncserver

Client:
 sudo apt-get install xtightvncviewer

I can't remember as of which version the encryption is included. (To be safe, I still use SSH tunneling, anyway.)

Nope, after researching it, they plan to do it but it doesn't look like TightVNC encrypts traffic, yet. Better stick with SSH tunneling or FreeNX.

---

