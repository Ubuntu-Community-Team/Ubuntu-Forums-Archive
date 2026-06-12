---
title: "My Mac can't see my Ubuntu"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by Muster Mark on 2009-10-25
**Background info -- **I have an old IBM laptop that I outfitted with Jaunty.  Everything was pretty much dandy at first, it was part of my home network, and I could screen-share from the macs (this was easy to set up, system->prefs->Remote Desktop).  I blew the hard drive, so I switched it out from another old laptop and reïnstalled Ubuntu.  The only difference is that I kept the windows xp partition (which I shrunk to 20% of the drive) just for the heck of it.

**The current issue -- **Now, everything works fine on the Ubuntu, but I can't use it as a server (I can only connect to shared folders, rather than the entire system).  In Finder if I click "connect to server" under the "go" menu, and type in the IP of the Ubuntu (the 192.168... one), I almost instantaneously get the error that the server doesn't exists or is not operational at this time.  Two icons for the computer appear in the "shared" section of the finder sidebar, one to connect to the shared folder I created on the Ubuntu, the other for screen sharing (it only works if I have it set to demand a password to screen-share, if not the mac just tries to connect for ever, for some reason).    On the Ubuntu, under "users and groups"  I have set user permissions to allow file sharing with the network (this is how I got it to work last time), but this has no effect on the situation.  I think the windows partition is effecting the situation, because when I tried to share a folder, ubuntu told me that a sharing service was not installed, and that I needed to install Windows networks sharing service to share folders, which I did.  Now I can share specific folders, but I can't log on to the computer from another computer, and access the entire system; I can only access the shared folder.

It seems to that if I wipe the drive and reïnstall with just Ubuntu, things will be fine.  But I'd rather not, because if delete the windows partition, I would need to actually buy windows if I ever wanted to run something that was windows-only.  After some internet searching I typed into Terminal "sudo apt-get install nfs-kernal-server nfs-common portmap", but got the error "E: Couldn't find package nfs-kernal-server".  Thank you for reading all this, any suggestion would be most appreciated.

---

### Post by dreamingdarkness on 2009-10-25
Are you sure it's "nfs-kernal-server" and not "nfs-kernel-server"?
I think its a typo, if that's not it make sure you have the repositories enabled. Synaptic finds nfs-kernel-server for me, so you could always try installing from Synaptic.

---

### Post by Muster Mark on 2009-10-31
Thanks for that.  The install worked now (one would think I would check for typos before starting an entire thread...).  Unfortunately it didn't change anything, but it's not really a problem any more, as I just share the home folder, and then get access to all user files.

Thanks for your help.

---

