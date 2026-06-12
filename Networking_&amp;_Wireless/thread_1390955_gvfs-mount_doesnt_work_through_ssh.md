---
title: "gvfs-mount doesnt work through ssh"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by venturax on 2010-01-26
My setup consist of three machines: 2 servers (A and B)(ubuntu) and my local laptop

Server A is a company controlled server which holds project data
Server B is our office local server, which we use for development purposes.

The problem occurs when i ssh from my local laptop to server B. After loggin in, i execute a script to transfer data from A to B. This script mounts server A using gvfs-mount. It fails to mount completely and gives me the following error
```
Error mounting location: volume doesn't implement mount
```

However if i log onto server B, using the servers keyboard and monitor (using a gnome session) i can execute the line.

To verify that it's something related to the ssh login, i tried the following:
(My local laptop is also running ubuntu)
from laptop open a terminal. See the gvfs mount work as expected.
open another terminal and ssh localhost
tried to execute gvfs-mount from the local ssh session and i get the above mentioned error.

After googling a bit, i found that it might related to dbus (which i know _nothing_ about) and i tried ```
dbus-launch gvfs-mount
``` and then tried to gvfs-mount server A, but it fails again..

All out of ideas now :-)

---

### Post by venturax on 2010-01-26
After consulting a guru colleague, I got a working solution.
dbus-launch is your friend, but should be used a little bit different

The following works:
```
dbus-launch gvfs-mount smb://A/some_share
```
...but the dbus session terminates immediately after, so trying a gvfs-copy or another operation will result in gvfs complaining, that the location is not mounted.

So... ```
dbus-launch bash
``` will create a new bash instance and it will stay alive until you exit it, so in the meantime all the gvfs commands will work \\:D/

---

### Post by Nixblicker on 2010-05-07
Hey, 

thank you big time for this trick, this is exactly what i was searching for.

And it also did work a couple of times, but very frequently the mounts do not get linked to the ~/.gvfs directory where i expect them.

Do you encounter the same thing or have any solution?

If i test the mounts with ```
gvfs-mount -l
``` they are listed but still not linked.

Is there an alternative way or location to access them via terminal?

Thank you and goodbye,
Nix

---

### Post by venturax on 2010-07-09
> **Nixblicker said:**
> Hey, 

thank you big time for this trick, this is exactly what i was searching for.

And it also did work a couple of times, but very frequently the mounts do not get linked to the ~/.gvfs directory where i expect them.

Do you encounter the same thing or have any solution?

If i test the mounts with ```
gvfs-mount -l
``` they are listed but still not linked.

Is there an alternative way or location to access them via terminal?

Thank you and goodbye,
Nix

I have tried googling a bit, but no luck on this issue. The trick worked for me and its still working. Have you upgraded the ubuntu release. @work i only use 9.10. Havent tried it with 10.04

---

### Post by bobpaul on 2010-12-10
> **Nixblicker said:**
> Hey, 

but very frequently the mounts do not get linked to the ~/.gvfs directory where i expect them.



I'm experiencing this problem just in general on 10.10. Nothing I mount shows in ~/.gvfs. Some programs (ex: Open Office) are unable to access files from network shares. *gfs-mount -li* shows they're mounted, and nautilus let's me browse with some apps (file-roller) working normally. My mounts all show *is_shadowed=0*. Is that related?

---

### Post by msknight on 2010-12-27
Same here. Was working fine, then updated my 10.04 yesterday (hadn't updated for a few weeks though) it stopped mounting the folder in .gvfs

Shows in gvs-mount -l, just not mounting a link.

There has been a change, though. I did install ZFS. I'll uninstall and test.

---

### Post by Morbius1 on 2010-12-27
> **msknight said:**
> Same here. Was working fine, then updated my 10.04 yesterday (hadn't updated for a few weeks though) it stopped mounting the folder in .gvfs

Shows in gvs-mount -l, just not mounting a link.
Maybe something got discombobulated in the update. See if the following package is installed:
```
gvfs-fuse
```You may need to add yourself to the fuse group as well:
```
sudo gpasswd -a msknight fuse
```Then logoff and login again for the group change to take affect.

---

### Post by msknight on 2010-12-27
Yes, gvfs-fuse is there.

I de-installed zen-fuse and now, even though I can now open files from the share, it still isn't mounting.

...and the share is still showing in gvfs-mount -l

---

### Post by msknight on 2010-12-27
De-installed gvfs-fuse and gvfs-bin

Re-installed zfs-fuse

Re-installed gvfs-fuse and gvfs-bin.

Now everything seems to work, including the share mounting under .gvfs and also ZFS mounting (under 0.6.9) as well. Bonus!

Thanks Morbius!

---

### Post by bobpaul on 2010-12-27
Great! [I solved it slightly differently]("https://answers.launchpad.net/ubuntu/+source/gvfs/+question/137084"), I wonder if it was the same problem or just the same symptoms.

---

