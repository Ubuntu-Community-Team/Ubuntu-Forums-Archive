---
title: "Quick questions SSH, SSL, FTP,VNC"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by wkmcclintock on 2011-01-28
Oh boy, I have what I feel are simple questions

VSFTPD w/SSL - Went here, works great on intranet, but found everyone elses problem with the port being unreadable, so I left an anon account open, and the SSL on. Should I just disable the locals's, dump the ssl, and leave the anon on (grab bag)? I feel as others do and don't want to have an array of ports open.

SSH (SFTP) - Traveled this path and found it did what I needed, but users can browse everything. Can they be jailed? I know I can 0750 on the other users folders, but that doesn't keep them out of the rest of the file system, and if I change EVERYTHING to xxx0 I figure its going to make EVERYTHING stop working for the users. I have the same problem (obviously) in cli, users can roam.

VNC - Are these connections secure? When logging on are the user/pass encrypted?

Please excuse me for being a noob. I've been trying for years tinkering with *nix, and in the past 4 weeks I have made more happen than in the past 10 years. I'm managing six machines, all personal, its driving me crazy. I go to bed thinking about it, and pickup where I left off when I awake. Is there a support group, I feel this is going to be a problem.

---

### Post by SeijiSensei on 2011-01-28
> **wkmcclintock said:**
> SSH (SFTP) - Traveled this path and found it did what I needed, but users can browse everything. Can they be jailed? I know I can 0750 on the other users folders, but that doesn't keep them out of the rest of the file system, and if I change EVERYTHING to xxx0 I figure its going to make EVERYTHING stop working for the users. I have the same problem (obviously) in cli, users can roam.

That's the way the system is designed.  Things that ordinary users shouldn't see are already blocked (e.g., /var/lib/mysql).  Otherwise users can list most directories and execute programs that have the execute bit enabled for all users.  However only root can really muck around in any of these locations; ordinary users can't really modify or insert files outside their home directories and /tmp without special permissions.

The one thing you might want to change is the DIR_MODE setting in /etc/adduser.conf.  0755 is way too permissive by my standards; I prefer 0700 as a default, so access to the user's files is limited to the user herself.

Many times users don't get to have shell on a server; they use scp or sftp to move files in and out of specified directories.  Secure FTP servers often "chroot" the users into their home directories, so they can't wander around on the system using this protocol.  If you want to create a user without login privileges, just replace "/bin/bash" in the corresponding entry in /etc/passwd with "/bin/false".

> VNC - Are these connections secure? When logging on are the user/pass encrypted?

You might want to look into tunnelling, either via SSH or OpenVPN, if you want to enforce encryption over connections.

---

