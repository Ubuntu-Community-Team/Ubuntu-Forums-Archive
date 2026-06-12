---
title: "AutoFS to mount SMB Shares"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by kamiller42 on 2011-11-19
I am trying to setup AutoFS using method 4 in [these instructions]("http://wiki.centos.org/TipsAndTricks/WindowsShares"). It seems to mount the machine, but not the shares.

Here is what dmesg | tail says
```

[31637.759932] CIFS: Unknown mount option gid
[31637.759938] CIFS VFS: No username specified
[31869.575875] CIFS VFS: No username specified
[32006.089474] CIFS VFS: No username specified
```Contents of auto.master
```
# Note that if there are entries for /net or /misc (as
# above) in the included master map any keys that are the
# same will not be seen as the first read key seen takes
# precedence.
#
#+auto.master
/mnt/smb /etc/auto.smb.top

```Contents of auto.smb.top
```
* -fstype=autofs,-Dhost=& file:/etc/auto.smb.sub
```[FONT=Courier New]
[/FONT]Contents of auto.smb.sub
```
* -fstype=cifs,rw,credentials=${HOME}/${host}.smbcredentials,uid=${UID},gid=${EUID} ://${host}/&
```Running autofs in verbose standalone mode produces the following when I try to access a share on the machine
sudo automount -f -v.
```

attempting to mount entry /mnt/smb/hs1/incoming
>> mount: wrong fs type, bad option, bad superblock on //hs1/incoming,
>>        missing codepage or helper program, or other error
>>        (for several filesystems (e.g. nfs, cifs) you might
>>        need a /sbin/mount.<type> helper program)
>>        In some cases useful info is found in syslog - try
>>        dmesg | tail  or so
mount(generic): failed to mount //hs1/incoming (type cifs) on /mnt/smb/hs1/incoming
failed to mount /mnt/smb/hs1/incoming
attempting to mount entry /mnt/smb/hs1/incoming
failed to mount /mnt/smb/hs1/incoming
attempting to mount entry /mnt/smb/hs1/incoming
failed to mount /mnt/smb/hs1/incoming

```I created a text file named hs1.smbcredentials in my home directory.
Here are the permission on the autofs files...
```

-rw-r--r-- 1 root root  688 2011-11-18 21:21 auto.master
-rw-r--r-- 1 root root  524 2011-07-14 07:11 auto.misc
-rwxr-xr-x 1 root root 1374 2011-07-14 07:11 auto.net
-rwxr-xr-x 1 root root  687 2011-07-14 07:11 auto.smb
-rw-r--r-- 1 root root   97 2011-11-18 23:22 auto.smb.sub
-rw-r--r-- 1 root root   49 2011-11-18 19:15 auto.smb.top

```
My machine is Ubuntu 11.10 64-bit. The other machine is Linux Mint 11 64-bit. I can browse the shares Nautilus.

Can someone give me direction? What am I doing wrong? Maybe my smb credentials file needs certain permissions?

---

