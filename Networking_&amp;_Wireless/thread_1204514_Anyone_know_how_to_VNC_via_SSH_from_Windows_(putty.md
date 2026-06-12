---
title: "Anyone know how to VNC via SSH from Windows (putty) to Ubuntu?"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-07-04
A friend of mine and I have setup a server at my house that we can both VNC into as well as SSH.  I've done VNC over SSH from ubuntu to ubuntu using the "-via" option on vncviewer in the terminal, and that's quite easy, but I was wondering if anyone knows how to do this over putty from a Windows machine to the Ubuntu server.

Edit: Nevermind.  Just found this via google.  Pretty simple:

[http://www.linuxreaders.com/2009/06/09/vnc-over-ssh-windows/](http://www.linuxreaders.com/2009/06/09/vnc-over-ssh-windows/)

---

### Post by wojox on 2009-07-04
It's been a while since windows but I believe you open PuTTY

Enter host name and port
use protocol ssh

Then on the left side under ssh click on Tunnels
Add source port and destination

---

### Post by JohnnySage50307 on 2009-07-07
I have to do this for school alot. Assuming you have a working vncserver on your ubuntu machine, you want to do the following:
 
From PuTTY:
1. Enter the Hostname of the server (either IP or DNS).
2. In the connection settings, expand the SSH tab and click on X11; check the "Enable X11 forwarding" box.
3. Open!
 
From the Terminal:
1. Type "vncserver". Typically, this will assign you the first available open port and viewing settings. I don't sugest trying to statically define the port assignment, however you can change your viewing settings. You might want to look at the man-page for vncserver to get a feel for it. If this is the first time you're accessing the VNCserver, it may ask you for a password that is 8 characters or less.
 
Back on your computer:
1. You need to open a VNCviewer or VNCclient. I sugest TightVNC. From there, enter the Hostname followed by a colon and the assigned port number (e.g. mybox.org:1).
2. Enjoy your VNC session!
3. When you are finished, close your VNCviewer/Client, then go back to your SSH terminal...
 
Back on PuTTY:
1. Type "vncserver -kill :LOG" where LOG is the assigned port number (make sure the colon is there!). If you do not do this, three things can result:
A. You can just reopen your VNCviewer/client whenever you want and resume your 
session.
B. Someone can hack into your system rather easily (128^8 might seem like a
large number, but simple hacking programs can crack that in about a minute).
C. If you reopen vncserver enough times, all the ports get filled, the system grinds
to a halt, and you need to say a rosary whenever you restart your server from its
crash!
 
Have fun and good luck!!

---

### Post by dnoyeb on 2011-05-09
when you use VNC client to connect, like so "mybox.org:1", that '1' is not a port number.  for :1 the port would be 5900.

---

### Post by diablo75 on 2011-05-11
> **dnoyeb said:**
> when you use VNC client to connect, like so "mybox.org:1", that '1' is not a port number.  for :1 the port would be 5900.

Actually it is a port number, albeit a short version of the full "5900".  Except the lack of a number means "5900".  If it were "1" it would mean "5901".  I have to VNC into different PCs at home from work all the time and the second is setup for 5901, but I type ":1" after the hostname.

---

