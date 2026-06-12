---
title: "Mounting a Windows share permanently in Ubuntu"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by tallmantim on 2011-10-10
Hello

I have limited experience with Linux, but am having trouble with what I thought should be a simple enough task. Not sure at this stage what I am doing wrong, or whether it is environmental.

I can open a link to a network share to my Windows server using the "Connect to server" dialog without a problem, which should (LOL, in my mind at least!) mean that the system can connect and mound SMB shares.

However, when I get to trying to manually mount the share through the command prompt or through the fstab file, I get the following error:

```
mount: wrong fs type, bad option, bad superblock on //server/Stuff,
missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount. helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

from command:

```
mount -t cifs //server/Stuff /mnt/winshare
```

I have created the mount with mkdir, there is no security on the share requiring a user ID or password and the environment is running within a Hyper-V session trying to connect to the system that hosts it.

Any thoughts greatly appreciated - Googling the error pointed towards needing to download additional smbfs and other components - which are now not part of the Ubuntu distro.

Regards

Tim

---

### Post by tallmantim on 2011-10-10
Hello,

Thought I would respond that I have found a solution to this.

Apparently Ubuntu does not include the requisite CIFS management tools - it can connect to a folder through support in the kernel, but in mounting a share it is trying to use non-kernel programs.

So, to solve, I did the following:

```
sudo apt-get install cifs-utils
```

and the fstab entry is:

```
//server/test /mnt/winshare cifs guest,_netdev 0 0
```

Hope this helps someone else! I thought this would be a simple task to carry out, but apparently not.

---

### Post by collisionystm on 2011-10-10
I always install the package smbfs to get cifs support.

---

### Post by Morbius1 on 2011-10-10
Actually, when you install the "smbfs" package you also install "cifs-utils" so that it's compatible with the current way of mounting with cifs.

From [https://launchpad.net/ubuntu/+source/cifs-utils/2:4.5-1](https://launchpad.net/ubuntu/+source/cifs-utils/2:4.5-1)
> cifs-utils (2:4.0-1) unstable; urgency=low

  * Initial release, packaging imported from samba source. (Closes: #571969)
  * Rename binary package from smbfs to cifs-utils, but leave the "smbfs"
    tools under the smbfs name for later deprecation post-squeeze.
In earlier Ubuntu releases there was no cifs-utils package so you had to install smbfs but it really never made any sense to call it smbfs since smbfs ( the filetype not the package ) isn't used anymore.

---

### Post by capscrew on 2011-10-10
> **Morbius1 said:**
> Actually, when you install the "smbfs" package you also install "cifs-utils" so that it's compatible with the current way of mounting with cifs.

From [https://launchpad.net/ubuntu/+source/cifs-utils/2:4.5-1](https://launchpad.net/ubuntu/+source/cifs-utils/2:4.5-1)
In earlier Ubuntu releases there was no cifs-utils package so you had to install smbfs but it really never made any sense to call it smbfs since smbfs ( the filetype not the package ) isn't used anymore.

The naming of the *package *smbfs is unfortunate.  Don't confuse the *package name *with the protocol held in the package.  Originally this was smbfs and with later upgrades the protocol name changed to CIFS.  I wonder if SMB2 is incorporated into cifs-utils?

---

