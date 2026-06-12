---
title: "FTP: Managing Access to My Folders..."
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by chome4 on 2010-01-19
Using gftp and want to allow a remote user access to a particular folder on my hard drive with a username/password.

How is this done?

All I know is that I'll need to ask the remote user to put in the url area something like this:

   [ftp://my ip address/folder]("ftp://66.223.34.55/")

---

### Post by Lars Noodén on 2010-01-20
> **chome4 said:**
> Using gftp and want to allow a remote user access to a particular folder on my hard drive with a username/password.

How is this done?

All I know is that I'll need to ask the remote user to put in the url area something like this:

   [ftp://my ip address/folder]("ftp://66.223.34.55/")

FTP is from the 1970's.  It's a well proven workhorse, but from an era when if you were on the net you were supposed to be there and if there was trouble it could usually be cleared up with a short phone call or an e-mail or two.  It sends the login name, password and all of the data unencrypted for anyone to intercept.  So it is most relevant now for Anonymous FTP, which is read-only with no login.  So if you want read-only data transfer then it's the way to go, as would be P2p. 

From your description, these may not be login credential or files that you wish to publish to the world.  If you want login access, then FTP and FTPS should be avoided for security.  Another reason to avoid them is to save work.

If you have the package [openssh-server](apt://openssh-server) already installed, no further configuration of the server is needed.  You can then use GUI-based SFTP clients like Nautilus, Filezilla,  Konqueror, Dolphin, Cyberduck, Fugu, or Fetch.  


```

   [sftp://my ip address/folder]("sftp://66.223.34.55/")

```

---

