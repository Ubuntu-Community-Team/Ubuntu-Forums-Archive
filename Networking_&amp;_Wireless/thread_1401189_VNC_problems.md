---
title: "VNC problems"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by Tsquad on 2010-02-07
Hello, i have a ubuntu server set up that i can VNC to no problem from multipull windows machines. I just tryd to VNC to it from my ubuntu 9.10 laptop and im having problems. 

First off im unsure what the best VNC client would be for 9.10. Im using the default Terminal Server Client and it is not working.

Im getting an error message of " unable to resolve host by name: Connection timed out(110)

any ideas as to whats causing this? or a better VNC client

---

### Post by Tsquad on 2010-02-09
any one here have an answer to this?

---

### Post by johnson.d on 2010-02-11
You can probably try to connect the server using the client rdesktop available in ubuntu
Gnome menu -> Applications -> Internet -> Remote Desktop Viewer.

If it is not available you can install it by using the command:
$ sudo apt-get install rdesktop

And the server is not able to be resolved by the hostname, you can probably try to connect using the ip address.

---

### Post by Iowan on 2010-02-11
[Here]("https://help.ubuntu.com/community/VNC/Clients") is a help page on VNC clients.
 Another [VNC]("https://help.ubuntu.com/community/VNC") help page that might be useful.

---

