---
title: "Need help with configuring up Samba."
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by khelben1979 on 2009-04-25
I need some help in configuring up Samba. I've never done this myself, although I have managed to get some documentation for it (of course), but this has not been enough to be able to fix this.

I need to be able to access my files from my Windows PC to my Powerbook with Linux (Debian Lenny). This is mainly movies which I want to run on the powerbook directly from the Windows system.

The GUI which I have installed is: Smb4k (SMB/CIFS share browser).

Do I need to have a Samba server install on Windows? Also, the Smb4k complains about that the network name on the Windows machine is bad, hmm...?

(The samba package has been installed on the powerbook)

---

### Post by Iowan on 2009-04-25
Windows should be able to share files without installing a server.  I haven't used "pure" Debian - Samba client comes pre-installed on Ubuntu, but that doesn't mean sharing is painless... 
May still need to edit smb.conf (/etc/samba/smb.conf?) to establish workgroup.

---

### Post by khelben1979 on 2009-04-25
Now I need a username and a account to be able to login to the windows machine. It did not work with any of the Windows accounts, how do I proceed?

---

