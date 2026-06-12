---
title: "Where are the network folders mounted?"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by brallan on 2009-01-04
[SOLVED] Well, apparently, samba does not mount the remote filesystem anywhere on the local filesystem, for that one must use smbmount. Please have a look at [this guide to mounting a remote network drive using smbmount]("http://ubuntuforums.org/showthread.php?t=1032394")

***************************************************************************

I am using shared folders across a network, and when i go inside of Places>Network> I can see all of the shared folders on the network. There's even one called "windows network", though none of my 6 machines runs windows! Going inside of this folder, I can navigate (using nautilus) through:

network:///   > smb:///   > smb://workgroup/   > smb://mediateca/

and then when I go inside of smb://mediateca/public/, it apparently mounts the folder, since I get a nice icon on my desktop called 

"public on mediateca"

My question is, Where are all of these filesystems getting mounted on my filesystem? I cannot find anything in my fstab, inside /mnt or /media, or by typing mount. I should like to use something like (g)rsync to do backups across the network, but I need to know a mount point.

---

### Post by brallan on 2009-01-04
well I still don't know where samba mounts the remote drives, but I may have found a workaround. It seems that nautilus has a nifty "Connect to Server" option, which mounts the remote drive on an address something like this:

home/brallan/.gvfs/PUBLIC on 192.168.15.103/

might do the trick!

---

