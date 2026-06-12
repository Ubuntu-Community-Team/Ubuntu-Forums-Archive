---
title: "Configure SMB client for automatic mounting"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by jeffeb3 on 2009-02-15
I have a computer at home that I use as a shared file server.  It's dual boot, and it's either windows, or ubuntu.

I have several other machines with ubuntu on them, and one with Suse.

The smb server in Linux, and the parallel setup in windows is fine.  It requires a password, and so far, I haven't been able to tell any difference when the server is in windows or Linux.

But, right now, the best way I've found to connect to this server is with a script that explicitly forces the cifs mount.  The problem here is that if I forget to umount it, then my computer tries to umount it after the ifdown script runs, and my computer hangs for a minute or two at shutdown.

I've had trouble in the past adding it to the fstab.  When the server is shutdown, or the laptop isn't connected to the network, then there are problems.  

I'd like to be able to browse to /media/Server and then have it try to mount the drive.  I know autofs can do this, but the ubuntu help articles make it seem like it's out of date, and the auto LDAP thing looks like there is some server configuration (which I'm not sure can even be done in windows).  

My next thought was to mess with udev, or the HAL daemon.  I've even messed around with the init.d scripts, unsuccessfully,  but I'm probably going to screw something up there.

Someone out there must have an elegant solution to this.  I'm not looking for a quick fix either.  I want to fix this right, and be able to do it repeatably on the other computers here.  

Thanks in advance.  I know the information is in these forums already, but I think that my goal is unique enough that it should be it's own thread.

For the record, I'm using ubuntu 8.04, 8.10, and suse 10.3.

Jeff

---

