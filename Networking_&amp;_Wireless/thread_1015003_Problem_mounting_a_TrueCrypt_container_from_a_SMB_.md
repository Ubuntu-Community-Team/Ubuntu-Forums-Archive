---
title: "Problem mounting a TrueCrypt container from a SMB share"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by mshadmehr on 2008-12-18
I have reformatted my laptop with Ubuntu 8.10, and installed TrueCrypt which I use since my old Windows to store my files in it. I have no problem with TrueCrypt when I try to mount my locally available file containers, or from a USB flash, etc. The problem is when I want to mount a file container that is on my desktop computer which runs Windows I keep getting this error:

Permission denied:
/home/shadmehr/.gvfs/public on desktop-pc/Test.tc

I know this is not a permission issue, because I can read and copy that file using Nautilus using the same credentials without problem.

Am I done anything wrong?

---

### Post by nixscripter on 2008-12-18
My shot in the dark suggestion: execute permission. If TrueCrypt -- for some reason -- requires it, then SMB might not give the file that. It would also explain why you could read and write.

Try opening a terminal and running: ```
chmod +x /home/shadmehr/.gvfs/public on desktop-pc/Test.tc
```

and then open it. Hopefully, SMB will allow you to edit the permissions of a shared file (I don't know almost anything about it).

---

### Post by 0dB on 2009-04-05
To get TrueCrypt to work over a network, you need the mount option "allow_other" (and also setting "user_allow_other" in /etc/fuse.conf). I had the same problem when trying to access a TrueCrypt volume on a USB stick attached to a thin client (LTSP = Linux Terminal Server Project, often associated with Edubuntu). In my case the network file system is "ltspfs", for others it is sshfs or nfs. Check what it is for you.

This is how I restarted ltspfs with the "allow_other" option (which mtab showed was missing):

```
sudo ltspfs 192.168.1.24:/var/run/drives/usbdisk-sdb1 /media/myusername/usbdisk-sdb1 -oallow_other
```

(The IP address was assigned to the thin client by the DHCP server.) Now TrueCrypt can open the .tc file, and "mount" shows:

```
ltspfs on /media/myusername/usbdisk-sdb1 type fuse.ltspfs (rw,nosuid,nodev,allow_other)
```

I have not figured out how to have "allow_other" automatically be set when mounting the USB stick over the network.

---

### Post by bit78 on 2010-07-23
> **0dB said:**
> I have not figured out how to have "allow_other" automatically be set when mounting the USB stick over the network.

You've to put the "user_allow_other" line into the file /etc/fuse.conf and edit /usr/sbin/ltspfsmounter on the LTSP server to use the allow_root option for ltspfs mounts. I've described all the details in the following blog post: [http://muzso.hu/node/4659](http://muzso.hu/node/4659)

You'll also find there instructions on how to set up TrueCrypt for use by normal users.

---

