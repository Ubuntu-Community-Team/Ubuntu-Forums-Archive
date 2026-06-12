---
title: "mounting NAS via smb-cifs"
date: 2009-01-23
forum: Mythbuntu
---

### Post by saxmaniac on 2009-01-23
Hi
I have a really annoying problem on my newly installed mythbuntu 8.10 htpc.
I have a Synology NAS (ntfs/smb)where I store all video and music files, and I want to access this NAS from mythtv.
I mount the NAS directory via /etc/fstab and a sudo mount -a command in /etc/rc.local.
Everything is working perfect exept for that it takes very long time to start mythbuntu and to shut down (about 5 minutes!)and both jobs shows errors.
At startup it hangs with "waiting for <mountpoint>......, and after 4-5 minutes it results in a FAIL and the booting proceeds.
At shutdown it hangs for 4-5 minutes with this text:
"some numbers" CIFS VFS: server not responding
"some numbers" CIFS VFS: No respons for CMD 50 mid 59

I hope someone in here have a solution for this annoying problem.

THANKS in advance.

---

### Post by ian dobson on 2009-01-23
Hi,

I also mount my network storage using cifs. I just added the command

mount -t cifs -o username=NAME,password=PASSWORD //192.168.0.2/Data /mnt/video

Are you sure the password is correct?
What happens when you got to the terminal and try mounting the share from there (without trying to mount it through fstab)?

Regards
Ian Dobson

---

### Post by maxim99 on 2009-01-23
That message appears because of the networking configuration in Ubuntu. By default it's set up to use NetworkManager which doesn't start until after the startup run level.

Personally I disable NetworkManager since I hate it with a passion anyway. This can be done through the Services dialog off of the menu.

This will disable the NetworkManager from starting up and taking over your interfaces. In order to get your mount to work at boot time you'll have to configure your NICs for the networking service.

The file in question is /etc/network/interfaces

This page here describes how to do it in many different scenarios:

[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)

After saving your changes you can test them by starting the networking service using the command line:

/etc/init.d/networking start

This should be the only change that is needed, the networking service should already be setup to start before the netfs service mounts your network shares in fstab. If you'll look you'll see a message saying "Configuring interfaces" or something similar, that is /etc/init.d/networking starting up, but by default it doesn't have a config so it doesn't turn on your interfaces.

It baffles me why NetworkManager doesn't reflect the settings that are chosen into the 
/etc/network/interfaces file, it is a useless application to me, so I choose not to use it.

---

### Post by newlinux on 2009-01-23
The fix I used for this is here:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently#System%20Hangs%20on%20Shutdown](https://help.ubuntu.com/community/MountWindowsSharesPermanently#System%20Hangs%20on%20Shutdown)

---

