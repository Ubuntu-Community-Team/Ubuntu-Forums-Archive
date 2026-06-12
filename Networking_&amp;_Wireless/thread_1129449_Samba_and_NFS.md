---
title: "Samba and NFS"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by zoomiest on 2009-04-18
I have been running Samba on a small network, and something stopped working, so my Ubuntu desktop could not longer connect to the Samba server, yet my windows machines could always connect to it.

**My Best/Common Practices Question - the reason for my post:**
Is it common or encouraged to run Samba and NFS together?

If I was to run one, which is the better network protocol? 

(I understand that Samba has been built to address windows to *nix network connectivity. So, NFS is *nix-only then?)

- zoomiest

---

### Post by Iowan on 2009-04-19
I haven't used NFS, so I'm probably not the best source of information... but your thread looked lonely.  Yes, NFS is for *nix systems. There's also [SSHFS]("https://help.ubuntu.com/community/SSHFS"), but Samba is kinda the default for sharing between *nix and Windows. 
Updates have been known to cause Samba problems. Have you tried entering **smb://<server-address>/sharename** in the location field on your Ubuntu box?

---

### Post by dmizer on 2009-04-20
> **zoomiest said:**
> I have been running Samba on a small network, and something stopped working, so my Ubuntu desktop could not longer connect to the Samba server, yet my windows machines could always connect to it.

**My Best/Common Practices Question - the reason for my post:**
Is it common or encouraged to run Samba and NFS together?

If I was to run one, which is the better network protocol? 

(I understand that Samba has been built to address windows to *nix network connectivity. So, NFS is *nix-only then?)

- zoomiest
Windows can access NFS with the appropriate additions: [http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)

I have run both NFS and SAMBA on the same share. There is usually no problem with this but I wouldn't suggest doing this on a production server in an office environment as the increased traffic and access may cause instability.

If you need 100% cross platform network filesharing (not WWW), I suggest taking a look at the FTP tutorial in the 5th link in my sig.

If your network is 100% Linux, I suggest using NFS according to the 4th howto in my sig.

If your Ubuntu computer is simply going to perform as a host to shares which only Windows computers will access, I suggest configuring a Samba server as outlined in the 1st link in my sig.

---

