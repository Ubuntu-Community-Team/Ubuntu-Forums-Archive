---
title: "Questions about SWAT (Samba Web Administration Tool)"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by northd_tech on 2011-09-05
I've been playing with Samba a little, trying to get a Samba server set up to share/transfer files to/from my Ubuntu 10.04.3 setup.  Reading the following page, I tried to use SWAT to make a few optimizations:

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-)

When I go into the SWAT web admin port:

[http://localhost:901/](http://localhost:901/)

I only see the Home, Status, View, and Password buttons (not the group of buttons seen here):

[http://cdn.unixmen.com/images/stories/thumbnails/images-stories-remote-http--i671.photobucket.com-albums-vv77-ZINOVSKY-unixmen-1-400x278.png](http://cdn.unixmen.com/images/stories/thumbnails/images-stories-remote-http--i671.photobucket.com-albums-vv77-ZINOVSKY-unixmen-1-400x278.png)

it shows me as logged in with my Ubuntu username, and trying to update SWAT told me this:

> **sudo apt-get install swat**
[sudo] password for *use*r: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
swat is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Any suggestions?

EDIT:  I may have found a fix on this old thread:

SWAT- buttons fell off?
[http://ubuntuforums.org/showthread.php?t=1536123](http://ubuntuforums.org/showthread.php?t=1536123)

---

### Post by northd_tech on 2011-09-05
> **northd_tech said:**
> 
EDIT:  I may have found a fix on this old thread:

SWAT- buttons fell off?
[http://ubuntuforums.org/showthread.php?t=1536123](http://ubuntuforums.org/showthread.php?t=1536123)

Posts #2 & 3 from that old thread seem to have fixed it for me- I went into System > Admnistration > Users & Groups  and clicked "Manage Groups" then added my username to the group specified in post #2.  I also executed the following terminal command and now the SWAT page gives me the additional buttons:

```
sudo chmod 774 /etc/samba/smb.conf

```

I think I'll leave this thread open for more questions (rather than SOLVED) for now though.

---

