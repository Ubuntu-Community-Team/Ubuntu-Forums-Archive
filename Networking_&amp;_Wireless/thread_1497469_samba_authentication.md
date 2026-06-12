---
title: "samba authentication"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2010-05-30
Hi
I would like to set up samba to share files between my *nix machines.I know it's usually done with NFS but i want to investigate and learn about samba for a few reasons:I would like to learn about samba so then i know more than just one way of sharing files, also i want to investigate the security possibilities that samba has because i was not happy with NFS security(i don't think linux can have secure RPC like Solaris).
So my question is:during authentication does Samba default to sending plaintext passwords over the network?.If so how do you change the default behaviour in a simple and secure way?.Does samba use the NT LM dialect by default, after the netbios session has been established, if you install the latest version of smbfs, for your client, from the repos?(i want a client that will use the securest dialect to talk to a mac SMB server).
Sorry to keep posting things before i try them out on my network, it's just that i want to understand how to make samba as secure as possible before trying it out.
Thank you for replies

---

### Post by methodtwo on 2010-05-30
Sorry the title of the thread should have been SAMBA authentication and dialects quesitons

---

### Post by methodtwo on 2010-05-30
Hi
I've just read about the security options in the smb.conf file.The only question from my original questions of this thread that still needs answering is: what protocol dialect does nautilus-share or smbfs default to?(which value should i have for the min protocol directive on the server, in smb.conf)?
Thank you for your replies

---

