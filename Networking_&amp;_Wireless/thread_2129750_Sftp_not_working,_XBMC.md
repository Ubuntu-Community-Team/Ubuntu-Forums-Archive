---
title: "Sftp not working, XBMC"
date: 2013-03-27
forum: Networking &amp; Wireless
---

### Post by vapor0 on 2013-03-27
Hi, I already posted this in "multimedia" because it involves XBMC, but it's really a networking problem, so maybe someone here can help me.

I have an Ubuntu box I'm using as an HTPC. It has Gnome 3, but it is set to automatically log in to XBMC.

But for some reason I can't ssh, ftp, or sftp in from my laptop. Hitting ctl-L in nautilus and entering "sftp://username:password@192.168.1.106" gives "Oops! Something went wrong." Same if I use gftp.

I tried using xbmc as the username, because that's the username for the webserver that allows me to control xbmc with my android phone. (Since xbmc supposedly has its own built-in sftp server.) Of course, that didn't work either.

Any ideas?

---

### Post by JRV on 2013-03-27
Try this from the command line, see what error messages you receive:

```

nautilus sftp://USERNAME@HOSTNAME/home/USERNAME

```

---

### Post by vapor0 on 2013-03-27
Nautilus gives me the error: Don't have permission to access the requested location.

Adding sudo gives: &#8220;sftp&#8221; locations are not supported

---

### Post by vapor0 on 2013-03-27
I get the same error if I try just "ftp" instead of sftp.

---

### Post by vapor0 on 2013-03-28
The tutorial I followed on the Ubuntu box is [http://www.ubuntu-tennessee.org/2012/tutorials/setting-up-an-sftp-ssh-server/](http://www.ubuntu-tennessee.org/2012/tutorials/setting-up-an-sftp-ssh-server/)

Apparently Xbmc has its own ftp/sftp abilities, but I haven't got that to work yet either. Yet I can control it easily over the local network using my Android phone!

---

### Post by vapor0 on 2013-03-28
I still haven't got it working with my laptop, but I sftp'ed in with my Android phone using AndFTP after commenting out the ListenAddress section, as opposed to the advice in the above tutorial.

Thanks to those who tried to help.

---

