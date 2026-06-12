---
title: "Better remote file management for Samba shares?"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by tsunamikitsune on 2011-04-16
I've been shifting files around on my samba server for a few months now, and it's a slow and painful process on Windows 7. I guess I didn't really think much of it at first, but now, I have to wonder: why the hell does it take Windows Explorer so long to move/copy files from one Samba share to another when they're all on the same hard drive?

I opened an SSH window and moved a 300MB file from one folder to another (the same operation that takes Windows 60+ seconds to complete) and it was instantaneous. Obviously, this process could be quicker. The only problem is, typing everything out can get tedious with how much I move files around.

How can I work around Windows 7's slow transfers? Is there a file manager I can run through SSH or something so that I could still work with a GUI but not have the issue of it thinking the shares are separate drives?

---

### Post by espressobeanie on 2011-04-16
That's a Windows problem. I'm a penguin.

In all honesty, I think it's slower because Win7 has some error-correction in the file transfer setting that uses more data during a transfer that makes it slow, automatically. I used to know, but I forgot. You could also do things that would boost performance, like turn off Aero and remove background pictures with a solid color instead.

It's possible that it may run faster if you use a program like 'Filezilla' to remote sftp into your Ubuntu computer and transfer there. 

Lastly, it could simply be that your disk speed isn't fast enough to what you want. If you use IDE, it's slower than say a 'SATA2'.

---

### Post by tsunamikitsune on 2011-04-16
> **espressobeanie said:**
> That's a Windows problem. I'm a penguin.

In all honesty, I think it's slower because Win7 has some error-correction in the file transfer setting that uses more data during a transfer that makes it slow, automatically. I used to know, but I forgot. You could also do things that would boost performance, like turn off Aero and remove background pictures with a solid color instead.

It's possible that it may run faster if you use a program like 'Filezilla' to remote sftp into your Ubuntu computer and transfer there. 

Lastly, it could simply be that your disk speed isn't fast enough to what you want. If you use IDE, it's slower than say a 'SATA2'.

I'll give FTP a shot. I'm pretty sure the hard drives are fine (they're two fairly new SATA drives in RAID), considering file transfers that take five minutes when done through Windows are basically instant when done via SSH. Thanks for the suggestion!

---

### Post by espressobeanie on 2011-04-16
There might be another limitation to FTP that I just thought of. If you have new hardware on your server, you might have 1000BASE-T, but to get a 1Gb/s speed, you need CAT6 wire, a router that supports Cat6 (very expensive), and both computers have to have 1000BASE-T NIC (Network Ident. Cards). That's my setup, except instead of a router, I use DNS Masq and some crazy 'foo', but it's blazingly fast.

---

