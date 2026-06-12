---
title: "Samba and Encrypted Homes"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by Derek Karpinski on 2011-05-11
I've spent the last few days getting Samba up and running.  We just bought a new laptop, and I've already been told it's not mine, and Ubuntu will NOT be going on it. :rolleyes: She's happy with Windows 7.

Anyways, she does use the desktop, and she does have documents stored on her /home dir.

I can successfully access my /home from the laptop('client') using Samba if I'm logged in to Ubuntu on the desktop 'server'.  But when she logs into her laptop, she cannot see her /home from the desktop.  If I log out and let her log in the desktop, she can access her /home on the laptop.  Confused? :confused:

Basically, it seems to access our own /home directories on the client, you have to be logged in on the server.

Is there a way around this? :KS

---

### Post by sweetleaf on 2011-05-11
> **Derek Karpinski said:**
> Basically, it seems to access our own /home directories on the client, you have to be logged in on the server.

Correct. Your encrypted data are stored in /home/.ecryptfs/username/. When you log in, it's transparently mounted in /home/username/. But when you aren't logged in, /home/username/ doesn't contain anything for Samba to share. Try sudo ls -a /home/some-other-username-with-encrypted-home/, and you'll see what I mean.

One idea would be to create a new unencrypted directory for shared files, say /home/Public/username/. For easy access, create a link: ln -s /home/Public/username /home/username/shared-files. Of course, if you had some good reason to encrypt your home directories, you might not want to do this. 

Alternatively, maybe there's a way to get Samba to invoke ecryptfs to decrypt your data on the fly. That's beyond me.

---

### Post by Derek Karpinski on 2011-05-11
> **sweetleaf said:**
> Try sudo ls -a /home/some-other-username-with-encrypted-home/, and you'll see what I mean.

Alternatively, maybe there's a way to get Samba to invoke ecryptfs to decrypt your data on the fly. That's beyond me.

Yep..........when I tried your code, I saw exactly what I saw on the laptop network share.

I was hoping there was a way to decrypt directories.  I don't know much, hell, it took me 3 days to get Samba to even work this far.  LOL.

---

### Post by Derek Karpinski on 2011-05-12
Bump..........:guitar:

---

### Post by daniel karlsson on 2011-06-18
Dear Everyone,

I think I got the same issue with an Ubtuntu 10.04 server. The encrypted directory is not decrypted/mounted when accessing through Samba. This is the log output from Samba:

[2011/06/18 14:28:05,  1] smbd/service.c:676(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
[2011/06/18 14:28:11,  1] smbd/service.c:1063(make_connection_snum)
  oin (192.168.1.199) connect to service XXX initially as user XXX (uid=1002, gid=1002) (pid 3043)

This used to work earlier, but not anymore. Since the server has mostly been working fine, I have not made any changes apart from updates.

/Daniel

---

