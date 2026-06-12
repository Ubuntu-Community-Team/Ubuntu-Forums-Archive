---
title: "Login Required for Shared access"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by lightningrod66 on 2009-08-27
I have set up a ubuntu 9.04 server as a web server.  We have a Windows network.  I have installed samba so that I can share the /var/www folder in order to be able to work on files on MY computer, then stick them into the shared folder via the network(rather than ftp).  Right now, everyone on the network can see this shared folder, and has access to it (they must login the first time they access it, but unless they reboot their computer, they have access indefinitely after that one login).  Of course, unless they know the login info, they can't access it anyway, but if they get lucky...

Is there a way to make this shared folder visible on the network (or not), but require a login EVERY time it is accessed from ANY computer?  Basically, I wouldn't want someone to need to use MY computer for something and have access to the files because MY computer has already logged in.

What might be even better would be if there was a "secret" way to access this server (with a login every time, of course) and not be visible on the network so no one but ME even knows it's there =)

---

