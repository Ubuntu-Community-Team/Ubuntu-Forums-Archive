---
title: "Supposed to cross-mount multiple Backends?"
date: 2011-10-01
forum: Mythbuntu
---

### Post by AbMagFab on 2011-10-01
If you have a set up with multiple backends, each with local storage, is the correct way to configure things to cross-mount the backends?

So:
BE1 - /media/myth1, nfs:/media/myth2
BE2 - /media/myth2, nfs:/media/myth1

And then in the BE configuration for storage groups, have:
/media/myth1
/media/myth2

On the primary BE only, and nothing defined in the secondary back-end?

In MythWeb, it's showing me both drives, but it looks a little weird:
- Disk 1 - BE1:/media/myth1, BE2:/media/myth1 - total 2TB (correct total for BE1:/media/myth1)
- Disk 2 - BE1:/media/myth2, BE2:/media/myth2 - total 2TB (correct total for BE2:/media/myth2)

Before I cross-mounted, it would only show the local disk for each backend, but nothing would record on BE2 (perhaps because BE1 wasn't quite half-full yet).

I searched all over for proper configuration of multiple Myth back ends, in terms of local disks and local tuners, but no luck.

Thanks in advance for any help!

---

### Post by newlinux on 2011-10-03
It depends on what you want to do, and partially on how you have your storage groups setup.

Do you want to record to storage on a remote backend? Sounds like yes. Myth won't record to non mounted non local disk so you'd have to mount it if you want a backend to record to remote disk, even if it is in a storage group on a remote machine. And you'd have to have the mounted directory path as in the storage group. 

It's been a while since I setup all my storage groups, but your backend configuration and setup looks fine for what you want to do, and the mythweb output looks right. It's just showing you all the locations it knows for the same disk for each listing. Mine does that too.


> **AbMagFab said:**
> If you have a set up with multiple backends, each with local storage, is the correct way to configure things to cross-mount the backends?

So:
BE1 - /media/myth1, nfs:/media/myth2
BE2 - /media/myth2, nfs:/media/myth1

And then in the BE configuration for storage groups, have:
/media/myth1
/media/myth2

On the primary BE only, and nothing defined in the secondary back-end?

In MythWeb, it's showing me both drives, but it looks a little weird:
- Disk 1 - BE1:/media/myth1, BE2:/media/myth1 - total 2TB (correct total for BE1:/media/myth1)
- Disk 2 - BE1:/media/myth2, BE2:/media/myth2 - total 2TB (correct total for BE2:/media/myth2)

Before I cross-mounted, it would only show the local disk for each backend, but nothing would record on BE2 (perhaps because BE1 wasn't quite half-full yet).

I searched all over for proper configuration of multiple Myth back ends, in terms of local disks and local tuners, but no luck.

Thanks in advance for any help!

---

### Post by nickrout on 2011-10-03
The documentation is here

[http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)

Read it carefully. You do not need to cross mount, or mount at all.

---

### Post by newlinux on 2011-10-03
> **nickrout said:**
> The documentation is here

[http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)

Read it carefully. You do not need to cross mount, or mount at all.

I've read it very carefully. I've had this discussion here (or on some other forum) before.

Tell me, nickrout, if you have a tuner on one backend that you want to record shows on a remote disk, how do you do that without mounts? The documentation specifically mentions mounts for a reason...

---

### Post by tgm4883 on 2011-10-04
> **newlinux said:**
> I've read it very carefully. I've had this discussion here (or on some other forum) before.

Tell me, nickrout, if you have a tuner on one backend that you want to record shows on a remote disk, how do you do that without mounts? The documentation specifically mentions mounts for a reason...

You don't. Recording files doesn't take place over the myth protocol. If you want to do that, then yes, you need to mount it locally.

---

### Post by newlinux on 2011-10-04
> **tgm4883 said:**
> You don't. Recording files doesn't take place over the myth protocol. If you want to do that, then yes, you need to mount it locally.

exactly my point :)

---

### Post by nickrout on 2011-10-04
> **newlinux said:**
> exactly my point :)

Why would you bother. You move the cards to another machine to reduce load. Why increase it with cifs/nfs ?

---

### Post by newlinux on 2011-10-04
> **nickrout said:**
> Why would you bother. You move the cards to another machine to reduce load. Why increase it with cifs/nfs ?

Some of the reasons I bother are:

1. One of my "cards" is an HD-PVR that needs to be co-located with the set top box it is recording from. Simply moving it doesn't work, I move the storage to it. There is local storage, but I have remote storage for when the recordings go over. . 

2. A fair amount of my overall storage is a NAS I built.

3.  I do have the tuners distributed across 3 machines. But not all my machines have slots available for tuner cards. But they do have extra hard drive space not otherwise being used, and extra processing power not in use that utilize for commercial flagging.

4. The CIFS/NFS and network loads are minimal and work fine for me. The primary user file storage I use from all my machines comes from my NAS.

5. Not all my machines are near places my tuners can get a signal from. But they do all have hard drives that can be used.

There are many other reasons one might. My guess the common ones would be NAS setups and utilizing unused disk space on other machines.

---

