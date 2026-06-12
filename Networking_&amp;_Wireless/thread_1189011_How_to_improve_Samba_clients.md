---
title: "How to improve Samba clients"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by oldtappan on 2009-06-16
Hello:

I'm using 9.04 as a home file server and I'm finding my Samba file sharing  performance to be very slow.  My files are stored on an external USB drive.  The entire drive is encrypted using TrueCrypt.  I'm accessing the Samba shares using Vista clients.  When I'm browsing files, such as photos from Vista, it seems to take forever to view the 1-2MB jpg files.  At first, I thought the Truecrypt encryption might be slowing things down.  So I made the photos directory on the Truecrypt encrypted Samba drive available via Apache.  Using a web browser to view these files was fast and very acceptable experience.  So my slow performance doesn't seem to be a TrueCrypt problem but rather a Samba problem.

So, how can I improve Samba performance?  Given that I'm using Vista clients, which support the higher perf [SMB2 ]("http://www.tomshardware.com/reviews/WINDOWS-SERVER-2008-REVIEWED,1710-8.html")protocol,  is there any way I can use SMB2 with the current stable version of Samba?  Are there other Samba tweaks that could improve performance? 

Are there other high performance file systems I should consider?  I would like to have encryption support to protect my data in case my drive gets stolen.

---

### Post by nazgulord on 2010-02-03
I know this is an old thread, but I thought I'd reply anyway in case someone had the same issue and was searching for it (similar to how I found it).

The reason for this problem is that samba doesn't support caching thumbnails in a Thumbs.db file by default. In order to accomplish this, go into /etc/samba/smb.conf, and under the section for the share (marked with [SHARE_NAME], possibly at the bottom of the config file), add the following line:

nt acl support = no

That should make the thumbnail viewing quicker.

---

