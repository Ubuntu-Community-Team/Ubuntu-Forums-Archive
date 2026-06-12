---
title: "Smaba help"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by stumped_guy on 2010-02-06
sorry if this doesn't go here, but i'm having issues mounting a samba share from my university. the closest i've gotten is to do a "connect to server" using the windows share setting, but i'd like to make the mount pretty much permanent.

[here]("http://engr.oregonstate.edu/computing/gettingstarted/224#files") is the site that give the smbclient command, but i'm lost as to how to mount in on my computer.

---

### Post by Iowan on 2010-02-06
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To for CIFS mounting.

---

### Post by johnson.d on 2010-02-11
You can make the samba mount permanent by adding the following line to the /etc/fstab file

//<server>/<share> /<mount point> cifs user=<username>,password=<password> 0 0

---

