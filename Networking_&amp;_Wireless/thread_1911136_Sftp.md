---
title: "Sftp"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by Warthaug on 2012-01-18
I have setup a file server at my work (a university) which acts both as the central repository for all of the data my lab generates, but also acts as an access point for outside access to the data.

For myself and other lab members, connecting to the server from outside of campus is achieved via a VPN.  I set it up so that there was a share accessible to collaborators - i.e.people who need access to some of these files, but are not members of my uni.  When I began setting up the server, our IT department said that providing access to these individuals would not be an issue.  They have since changed their mind.

As such I need to setup access to the server using what few options are left to me.  Port 22 (SSL) is open to the outside world, and SFTP appears to run just fine over it from both within and without the university (as connected to useing filezilla).  But while the connection works, I have an issue I hope someone can help me with.

When I log-in using the UID and password I assigned to one of my collaborators, sftp loads in the root directory.  Moreover, the user seems to have all of the rights associated with root, rather than the rights assigned to their user account.  Is there a way to configure the server such that a connection via sftp will be directed and restricted to the share/directories I assign?

If it helps, I'm running turnkey linux file server.  Usual sharing is via samba, and the setup there works properly (i.e. restricts the user to specific directories).  Ideally I'd like to somehow apply the samba users/groups/permissions to the sftp system, although I'm more than willing to manage it separately if needed.

Any and all help is greatly appreciated!

Bryan

---

