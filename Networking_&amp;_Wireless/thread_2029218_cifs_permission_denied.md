---
title: "cifs permission denied"
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by jldoll on 2012-07-19
I'm working with 3 computers. 1. laptop/client 2. desktop old server 3. desktop new server.  I originally had samba shares between 1 & 2.  The files being shared on 2 were on a 1TB external usb drive. Everything worked well.  I came into some new hardware 3, and thought it would be better to migrate my shared files to one of its internal drives. Here's what I perceive to be the major sections:

1. mount of local volume at server
2. smb.conf at server
3. samba user account at server
4. credentials file at client
5. mount point of shares at client
5. mount entry of shares as cifs in fstab at client

The local volume at server seems to mount fine. I copied smb.conf from computer 2 to computer 3 and modified the share paths for new locations on the internal drive.  I added the samba user to 3 same as 2.  Didn't change the user file because I used the same samba username/password.  In fstab of client I changed only the name of the server (the entry uses the same credentials file).

If I open my file manager and navigate to a share in smb context (smb:\\), I'm prompted for samba username/password. Once entered I can see all the files, add files/directories, modify files.  If I open my file manager and navigate to a share by mount point (media\share), I can see all the files, I can copy a file to the location, I can copy an empty file to that location. If I try to copy a file with contents, the top level folder gets copied; but all the files in that folder generate permission denied errors.  The properties on the top level folder show my user suid and guid rather than my username and group as text.

I would appreciate any suggestions anyone would have.

---

### Post by jldoll on 2012-07-19
Solved with thanks to this link which concisely explains the client credentials [http://opensuse.swerdna.org/susesambacifs.html](http://opensuse.swerdna.org/susesambacifs.html)

Apparently the user accounts were coincidentally identical between PCs 1 and 2 so not having the client credentials explicitly defined wasn't an issue.  They weren't between 1 and 3, so adding the credentials in fstab resolved the issue.

---

### Post by jldoll on 2012-07-19
One additional note.  I was wrong about the uid and gid being mine in the original post.  It was an assumption I made because the folder was copied from my home folder.

---

