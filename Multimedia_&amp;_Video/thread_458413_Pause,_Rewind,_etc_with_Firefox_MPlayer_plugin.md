---
title: "Pause, Rewind, etc with Firefox MPlayer plugin"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-05-29
I'm using an Apache web server so that I can share video files on my LAN without having to transfer them all over the place.  Right now I am using the MPlayer plugin for Firefox to play them, but I can't pause, rewind or fastforward.  Also, even if I watch in full screen mode, I have the firefox panels on the top and bottom.  Is there a better way to play these files?
Thanks

---

### Post by josesanders on 2007-06-04
Problem solved!

I decided to try file sharing with Samba again.  Previously, I couldn't connect to the server from any remote machines, it just kept repeating the login screen, even if I put in the correct user name and password.  What I did, then was the following:

Create the Samba share on the server:
[http://www.go2linux.org/node/98](http://www.go2linux.org/node/98)

Then mount the share on the remote system:
[http://starkos.industriousone.com/mounting-windows-shares-ubuntu](http://starkos.industriousone.com/mounting-windows-shares-ubuntu)

---

