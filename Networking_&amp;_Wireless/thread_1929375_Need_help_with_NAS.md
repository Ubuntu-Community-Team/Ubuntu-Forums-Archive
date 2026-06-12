---
title: "Need help with NAS"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by jrad4 on 2012-02-21
I'm new to linux, but installed Ubuntu on my laptop after the hard drive crashed and I replaced it.  I've been able to figure out everything so far, but I just bought a Seagate NAS to hold my media and can't figure out how to view it on my laptop.  It's connected to the network, and I configured it by going to the IP on my laptop, but I don't know where to view the drive so I can start moving things to it.  

When I go to Network, I have an entry for Windows Network - clicking that, I get:  SEAGATEGROUP and WORKGROUP.  Within SEAGATEGROUP is GOFLEX_HOME, which is the type of NAS I have, but everything past that is confusing me.  There are multiple folders in there (Public share, backup, external share, etc..) and the only folder that I can open is external share and it's listed as 64mb in size (the NAS is 1TB).  Opening any other folder asks for a login (using the one I configured the NAS with) and then says "unable to mount windows share".

Am I doing something wrong?  I'm used to just going to Network in Windows and having my networked drives show up.  I'd like to have the NAS mounted somewhere at all times so I can use it as it was the hard drive in my laptop.  

Any guidance is appreciated.

---

### Post by jrad4 on 2012-02-22
Update - 

I rebooted the external drive tonight, and went back into Network on my laptop and the structure has changed.  Now, there's an entry for Goflexhome, but I can't write any data to it - I get a read only error.

Any advice?

---

### Post by jacob.david on 2012-02-22
If your NAS supports samba then you can mount it using the following command.

nautilus smb://<IP of of your NAS>/<share name>

---

