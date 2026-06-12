---
title: "Remote Boot"
date: 2007-11-06
forum: Mythbuntu
---

### Post by bon_the_one on 2007-11-06
Hi All,

I'm new to Mythbuntu having used Myth on FC7 before. I downloaded 7.10 Desktop to give it a try out, and have been so impressed I had to check out Mythbuntu. Superb is the best word I can think of. Well executed and produced and a pleasure to install even in my tediously annoying "Because I want to do it like that" enviroment!

A quick question. I'm now looking to add basic Mythfrontend boxes around the house, and would ideally like to ditch the hard disks. This means I'd have to look at remote boot from the Mythbuntu server. Even for my home office PC, I'd quite like to have the bios boot from network after a powerfail, so the HD install of Ubuntu Studio isn't touched until I get home. I'll boot Studio if I need it kind of thing.

Can anyone point to any guides where I can A) study PXE Boot if thats the way to go, and B) a guide on network booting Mythbuntu. I have a dedicated Mythbuntu backend server with all my media on, so it would be my aim to have machines come up from an image on that and have access to all the media through a remote root I guess. 

I know someone might say "buy a hard disk, they're cheap", but this is something I'd like to study for my own entertainment. I like the idea of a Myth Server that distributes the OS around the house to any devices (PC's in this case) I have.

Any assistance on links I can look at would be greatly appreciated,

Ian

---

### Post by superm1 on 2007-11-15
I do something very similar on my setup here at home with a PXE boot.  I don't believe I can refer you to an entire "follow" this guide that will "Just Work" (TM).

When I set things up it was a large number of guides to get things going.

If you want to be the first to author a guide on how to do this for a mythbuntu setup, i'm sure there are plenty that will be very appreciative to see an entire walk through on it.

Looking through my notes, I don't have any older links to get you started.  There were some on the wiki.ubuntu.com and help.ubuntu.com, but they aren't coming up with quick searches from what I can find.

The jist of it is that you need to do an install into a chroot or install on a machine and then copy the directory structure over to your backend.

Share that NFS root.

Setup a DHCP server with PXE boot options.

Setup a TFTP server.

Chroot into the install and reconfigure the initrd to include NFS root support.

Setup the TFTP to point to the proper NFS root.

Profit.

---

