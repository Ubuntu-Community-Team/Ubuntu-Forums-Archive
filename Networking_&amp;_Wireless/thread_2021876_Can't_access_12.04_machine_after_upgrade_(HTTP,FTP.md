---
title: "Can't access 12.04 machine after upgrade (HTTP,FTP,VNC,etc)"
date: 2012-07-09
forum: Networking &amp; Wireless
---

### Post by copan on 2012-07-09
Hello peers.

Title says it all.  Recently upgraded from Ubuntu 10.04 to 12.04-server package.  Looks great, good job.  Everything works, including my internet.  I know my local IP address: 192.168.1.135

For some reason I can no longer (as I did before) connect to my 12.04 server machine via HTTP, FTP, VNC, or anything.  It's like the new OS blocks all incoming connections.

I can use terminal fair enough so if you need me to use nix commands thats fine.  Apache/MYSQL are running at localhost on the server, but my **main focus right now is the VNC server as that is used primarily from my mac to control all Ubuntu operations.  No need to fix all problems at once.  Vnc4Server is installed, I checked.**  I changed the settings in the VNC preferences window to allow connections, no pass, etc..

Thank you for your help.

---

### Post by copan on 2012-07-09
For some reasons ports I used before on my LAN were blocked after the upgrade.  Possibly because I installed server package.  I don't know.  Anyway, fix is easy:

sudo ufw allow 80
sudo ufw allow 4900


etc..

Thanks for reading.

---

