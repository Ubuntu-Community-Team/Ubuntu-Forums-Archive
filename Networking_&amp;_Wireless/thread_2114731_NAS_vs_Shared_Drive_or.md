---
title: "NAS vs Shared Drive or ?"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by mark2741 on 2013-02-10
I simply need a place to store and serve up media (music, movies, etc.) via Plex server (which is currently installed on my Ubuntu-based desktop). I also need to have the ability for additional directories for my family members to read/write documents, etc. from. 

I've been drooling over the idea of a NAS for years but never got one because of the cost. But today I saw at my local Microcenter that I could get one of the Buffalo NAS setups for $99 - either a single 1TB version that's on sale, or a 2-bay, no hard-drives included version in which I'd have to supply the drives. But now that the cost has come down...I'm not so sure a NAS is a good solution vs simply sharing an external USB drive?

Backup in the form of a RAID system sounds fabulous until I think about having to learn and deal with that. I'm not sure I want to go that route.

Here's where it gets trickier:

I have so many different devices that would need to access/stream the data: Ubuntu, Windows, Macbook Pro, Xbox 360 (just for the DLNA media via Plex). Not to mention iPad and iPhones/iTouch....

So what do you guys do? Just an external USB drive and make it Shared via Ubuntu? The good thing is that I do presently leave my Ubuntu desktop on all the time, though it is set to dual-boot with Windows 7 and my son insists on going into that from time to time. But I guess I could just set the same external USB drive to shared from within Windows too?

What do you think, given my needs?

---

### Post by tgalati4 on 2013-02-10
You can set up a freenas or a nas4free server on an old machine.  Synology makes linux-based NAS units.  You will find that a lot of the cheaper NAS units have crappy interfaces.  But simply using an Ubuntu desktop with several services running is also a good way to go.

---

### Post by CharlesA on 2013-02-10
> **tgalati4 said:**
> You can set up a freenas or a nas4free server on an old machine.  Synology makes linux-based NAS units.  You will find that a lot of the cheaper NAS units have crappy interfaces.  But simply using an Ubuntu desktop with several services running is also a good way to go.

+1.

@OP: Please keep in mind that RAID isn't really a form of backup. Unless you have two different RAID boxes that are synced to each other, you will need to make sure you have some form of backup in addition to the RAID array/NAS box.

My file server is running Samba for the main potion of sharing because it works with Windows and *nix boxes. I could use NFS because Windows 7 and *nix support it, but I have found Samba to fit my needs.

I was thinking of running a DLNA server but I do not have any devices that would use it, so it is pointless for me to set it up, so I don't really have any experience with PLEX. You can install whatever services you want on your machine, even if it running the desktop version of Ubuntu. It doesn't need to be the server version to act as a server. ;)

If the machine you want to use is being rebooted often, it might be easier to get an older or low power PC and hook up an enclosure to it and use that as your file server. I have a dedicated server and it makes life so much easier. :)

If you wanted to use an external usb drive, it would need to be formatted as NTFS in order to work with both Windows and Linux, and this limits the things you can do on the Linux side of things.

---

### Post by Thee on 2013-02-11
I think "off the shelf" NAS is the simplest way to go. It's easy to setup, its small, it doesn't use too much power and its quiet. Plus with external USB drive you would have to have your computer turned on all the time in order for the HDD to be always accessible.

Edit: These new NAS devices have USB ports to which you can connect a USB hard drive, so you can upgrade at any time with a cheap USB drive and still have NAS, if 1TB is not enough after some time, for example.

---

