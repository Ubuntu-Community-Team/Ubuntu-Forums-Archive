---
title: "Setting up shared folders on D-link DNS-321 NAS"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by ratdog on 2011-03-06
I'm trying to set up a media server on a D-Link DNS-321 network attached storage device with two 1.5TB drives in RAID1 configuration.

I think I want to set it up with NFS access because I will only be accessing it with 2 Ubuntu laptops and I've read it is faster than Samba.

I want to set up the laptops so the media server mounts automatically on startup and I want Rhythmbox to use it as the music library.

I've tried using [this]("https://help.ubuntu.com/community/SettingUpNFSHowTo") guide and following the instructions for the client, but don't know how to get the DNS-321 setup properly as the instructions on the guide are for using an ubuntu server.

Anyone have any suggestions for an easy way to set this up?  I'm using Ubuntu 10.04.
I'm no linux expert and not up on my networking terminology, so be easy on me.:)

Thanks!

---

### Post by ratdog on 2011-03-06
Also, I'm not even sure if I want to use RAID1.  Is there an advantage to using RAID1 over just using one drive and backing it up on to the other once in a while.  Will the drives last longer without using RAID?

---

### Post by ratdog on 2011-03-10
Bump bump...

I could really use a little guidance.

Thanks

---

### Post by ratdog on 2011-04-26
So after much searching on the forums, I set up the NAS on a Windows Network using a CIFS protocol.  For simplicity and to minimize wear and tear on the drives, I decided not to use RAID and just backup one drive to the other once in a while.  I got it to automount a couple of times, but now my computer is not happy with my fstab entry.  I can still browse to the NAS in Network, but I need it to automount in the same place so that Rhythmbox can find and play the music.  

My fstab entry looks like this:
```
//192.168.1.67/Volume_1/Media/ /home/photon/MediaStorage cifs _netdev,nounix,uid=photon,gid=photon,file_mode=0777,dir_mode=0777 0 0
```

I also added this code to /etc/network/if-up.d/fstabmount and made it executable:
```
#!/bin/sh
mount -a
```

It worked at first, but now when I type #sudo mount -a in terminal, I get this error:
mount error(113): No route to host
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Any help would be appreciated...
Thanks

---

### Post by ratdog on 2011-05-15
I can't figure this out!

Maybe one more bump will do the trick?

Thanks

---

### Post by Houchy on 2011-08-26
Hello,

I have the same problem.

Could somebody help please.

Thank you.
Houchy

---

