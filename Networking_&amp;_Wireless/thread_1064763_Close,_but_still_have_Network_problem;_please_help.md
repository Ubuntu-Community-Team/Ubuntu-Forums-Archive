---
title: "Close, but still have Network problem; please help!"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by GARoss on 2009-02-09
This has been quite an experience setting up a network but I'm close, thanks to the help of the many participants of this forum.

I started yesterday with nothing! Today I have been able to network from an XP computer to my Ubuntu computer but not from the Ubuntu to the XP. Re-reading a helpful post from FishRCynic, I cannot find with the search function any reference to ***workgroup=*** in the **smb.conf (/etc/samba)-gedit** list. (See FishRCynic's post below.

[I]> **FishRCynic said:**
> go to terminal
click applications 
      accessories
      terminal

type in
sudo gedit /etc/samba/smb.conf


search for workgroup=

change to Ross or ROSS or whatever it is exactly on the xp machines

click exit and save file

type in 

sudo /etc/init.d/samba stop
sudo /etc/init.d/samba start

you now should be able to somewhat connect to the xp machines using samba[/I]

Here's a list under Networking;

[I]#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes[/I]

Should ***workgroup=Ross*** (Ross is the XP network name) be added in one of these lines? Should it be ***# workgroup=Ross**?* Where?

All suggestions are appreciated!
George

---

### Post by GARoss on 2009-02-09
Anyone?

---

### Post by Iowan on 2009-02-09
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=1064406") thread?
The **workgroup=** line should be near the top of the file.
> **GARoss said:**
> I changed the 2nd line in Global Settings to read;
#======================= Global Settings =======================

[global]

[I]## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	[COLOR="Red"]workgroup = Ross[/COLOR]
[/I]

...it was called WORKGROUP.
Still nothing.
Any ideas?
George

That'd be the line...

Not intended as permanent solution, but try smb://ip-address-of machine/sharename from ubuntu.

---

### Post by GARoss on 2009-02-09
> **Iowan said:**
> Have you seen [this]("http://ubuntuforums.org/showthread.php?t=1064406") thread?
The **workgroup=** line should be near the top of the file.


That'd be the line...

Not intended as permanent solution, but try smb://ip-address-of machine/sharename from ubuntu.

Thanks. It reads;
bash: smb://ip-address-of: No such file or directory
George

---

### Post by Iowan on 2009-02-10
Substitute the actual IP address for "ip-address-of machine", and actual share name for "sharename".

---

