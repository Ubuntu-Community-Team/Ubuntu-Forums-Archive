---
title: "samba share permission confusion"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by chris_tikva on 2009-04-11
Hi,

I have a ubuntu based machine and a xp machine on a LAN. The xp machine has a shared directory which I want to access from ubuntu.

So far I can use smbclient to read and write files but when I try to mount to a local directory I can only get read access. I can't see what is restricting the write access. Presumably not the windows side since smbclient works.

The script I'm using to do the mount is this:

#!/bin/bash
nmblookup neon_win > neon.txt
IP_ADDRESS=`awk '/neon_win</ {print $1}' neon.txt`
smbmount //$IP_ADDRESS/shareddocs /home/chris/neon -o rw
rm neon.txt


What am I doing wrong?

As an aside, if I try to run:

 smbmount //neon_win/shareddocs /home/chris/neon -o rw

I get a "can't find target" error. How come nmblookup and smbclient can find it but smbmount can't? Is there an easier way to do this?

Thanks,

Chris

---

### Post by bryanl on 2009-04-11
One of the easiest ways I have seen recently is to install autofs. Then edit /etc/auto.master to enable the smb line. It also helps to put the windows machine in your hosts file so you can refer to it by name rather than IP address. You can create a credentials file as /etc/auto.smb.servername with ID and password if needed to access the server shares.

Or, tf you use nautilus to open the share, you can find it in your home directory under .gvfs

or, to mount in a script try
```
mount.cifs //server/share localmountpoint -o user=workgroup/user%password,noperm,file_mode=0666,dir_mode=0777,nounix
```

You can use the same options in an fstab line. Make sure you have the samba package installed (it includes the CIFS filesystem). The noperm, nounix options are there to help avoid permissions mismatching if needed.

---

### Post by Iowan on 2009-04-12
Probably more information than you want/need, but [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To covers many of the CIFS-mounting problems.

---

