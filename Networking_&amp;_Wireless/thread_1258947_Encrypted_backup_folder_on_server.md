---
title: "Encrypted backup folder on server?"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by melat0nin on 2009-09-05
Hello all

I would like to use a redundant disk I have sitting in my media server as a backup disc for my documents and photos.

Because the media server is public, in the sense that the people I live with can see what's on it, I'd like to encrypt this disk (or the folder on it) so that only I can see and browse my backups.

I also want the folder/disk to be shared on the network so that I can access it from my desktop and move stuff over to it (and, potentially, set up synchronisation so that it keeps an up-to-date backup of my desktop.)

Is this possible? I looked at ecryptfs but the instructions seem to relate only to creating a /Private folder in /home.  Also, there's no mention that I can see of networking this folder/drive.

I'm running 9.04 Server on the media server, and XP/9.04 Desktop on the desktop.  The empty disc in the server is ~110gb and is formatted with ext4.

Any suggestions would be much appreciated!

-Laurence

---

### Post by DFlame on 2009-09-05
You've already got sharing set up, so that's the hard part out of the way.

What I would do, is install [Truecrypt](http://www.truecrypt.org/) on your client system. The website provides Ubuntu packages.

From here, I'd open Truecrypt and create an encrypted file container, making sure to use a strong password or key on it. This file can then be moved to your network share. As long as the share is mounted, you should be able to browse to it within Truecrypt. When opened, TC will mount this file as a filesystem on your local machine.

It's a long way of doing it but all I can think of for now. I don't know a lot about automated backups though, sorry!

---

### Post by melat0nin on 2009-09-06
> **DFlame said:**
> You've already got sharing set up, so that's the hard part out of the way.

What I would do, is install [Truecrypt](http://www.truecrypt.org/) on your client system. The website provides Ubuntu packages.

From here, I'd open Truecrypt and create an encrypted file container, making sure to use a strong password or key on it. This file can then be moved to your network share. As long as the share is mounted, you should be able to browse to it within Truecrypt. When opened, TC will mount this file as a filesystem on your local machine.

It's a long way of doing it but all I can think of for now. I don't know a lot about automated backups though, sorry!

Thanks for the suggestion.  I must admit I thought this would be doable without any third party software, so that I wouldn't have to install anything on the client machines (it would be nice to just browse the network, open the shared disk, enter a password and there we go).

---

