---
title: "NX Client can't see launcher icons etc"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by deBoogle on 2012-11-25
Hi All,

Just started my first delve into the realms of Linux and ubuntu today and all has gone well until..

I am using Ubuntu 12.04, and have installed NX Server (free edition) and I have also installed open ssh and firestarter.

I am pretty certain I have set up the SSH server and NX server correctly and forwarded the port in firestarter correctly. I have set the client to Unix - Gnome.

When I log into the server from my Win7 machine using the NX client and I connect ok (I can see the logon in firestarter's active connections) and I get the nice big red M when the connection is made but i see the desktop background and nothing else, no launcher icons nothing. I can however do right click on the screen and get the dialog and I can draw selection boxes using the left mouse press. And I can get to 'all settings' if I right click->change background->click all settings.

The server side resolution is 1024x768 and I run it on the client side in a 1024x768 window on a higher res screen. So that should be OK.

I am running on a LAN at the moment before I go across the interweb.

Can anyone offer any help?!?
deBoogle

---

### Post by personalpc on 2012-11-25
[https://help.ubuntu.com/community/VNC]("https://help.ubuntu.com/community/VNC")

NX has lots of bugs. Try switching to vnc the localhost through a compressed ssh tunnel. In windows there is Remote Desktop Manager that would be a solution for the client login. If you would like to go web based then tomcat server with guacamole is your answer. Cheers! 

Also make sure whatever vnc port is open on your firewall. That could be why NX is having trouble displaying

[www.remotedesktopmanager.com]("http://www.remotedesktopmanager.com")
[guac-dev.org/]("http://guac-dev.org/")

---

