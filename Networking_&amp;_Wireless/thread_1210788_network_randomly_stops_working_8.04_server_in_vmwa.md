---
title: "network randomly stops working 8.04 server in vmware"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by senor_smile on 2009-07-11
I am having a problem that I cannot find a solution to.  I have an ubuntu 8.04 server as a guest vm in vmware server 2, with windows xp pro as the host OS.  Very randomly(i.e. sometimes 2 times a day, other times once in two weeks) the network stops responding.  I can't ping the server and the server cannot ping out, as if the network has gone down.  Restarting the ubuntu server sometimes fixes this, but other times I also have to issues the command: 
> sudo /etc/init.d/networking restart

I have checked the logs and see nothing obvious that is causing this to happen.  The only things installed are:
gnome-desktop
samba
openvpn
abiword
gnumeric

I can tell when the network stopped working as the openvpn starts getting lots of errors in the syslog.  Has anyone else seen problems like this?

---

