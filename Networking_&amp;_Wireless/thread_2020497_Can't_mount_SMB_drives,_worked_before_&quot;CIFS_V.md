---
title: "Can't mount SMB drives, worked before /&quot;CIFS VFS: Error connecting to socket&quot; RC -115"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by skinnersbane on 2012-07-08
I have a machine running Precise (12.04 x64), and I cannot mount my SMB drives (I have 3).  It used to work (a week or two ago), and I didn't touch fstab!  The machine hosting the shares is a commercial NAS, and I'm not seeing anything that would indicate it's an issue with the NAS.

I have an older machine which I updated to Precise at the same time (both fresh installed, not dist-upgrade), so should have a very similar configuration.  It is not having any problems.  Some packages are out of date on the working machine and the machine with the issue is up-to-date. I am not having problems on windows machines/partitions either, only one of my Precise machines.

The two machines are using identical entries in fstab and identical /etc/samba/smb.conf files.  I don't think I've ever changed smb.conf (has never mattered before).

My fstab entries all basically look like this:

```
//10.1.1.111/public       /media/public        cifs  credentials=/home/skinnersbane/.credentials,iocharset=utf8,uid=skinnersbane,gid=skinnersbane,file_mode=0644,dir_mode=0755 0 0
```

Here's the dmesg output on boot:

```
[   51.162198] CIFS VFS: Error connecting to socket. Aborting operation
[   51.162369] CIFS VFS: cifs_mount failed w/return code = -115
[   51.194106] CIFS VFS: Error connecting to socket. Aborting operation
[   51.194250] CIFS VFS: cifs_mount failed w/return code = -115
[   51.198120] CIFS VFS: Error connecting to socket. Aborting operation
[   51.198243] CIFS VFS: cifs_mount failed w/return code = -115
```

There are no other errors I see in the dmesg output.

Originally when I ran 'testparm -s', the output contained these lines

```
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
```

Here's the samba related programs I have installed:

```
$ dpkg --list|grep -i samba
ii  libpam-winbind                                2:3.6.3-2ubuntu2.3                      Samba nameservice and authentication integration plugins
ii  libwbclient0                                  2:3.6.3-2ubuntu2.3                      Samba winbind client library
ii  nautilus-share                                0.7.3-1ubuntu2                          Nautilus extension to share folder using Samba
ii  python-smbc                                   1.0.13-0ubuntu1                         Python bindings for Samba clients (libsmbclient)
ii  samba-common                                  2:3.6.3-2ubuntu2.3                      common files used by both the Samba server and client
ii  samba-common-bin                              2:3.6.3-2ubuntu2.3                      common files used by both the Samba server and client
ii  winbind                                       2:3.6.3-2ubuntu2.3                      Samba nameservice integration server

$ dpkg --list|grep -i smb
ii  dmidecode                                     2.11-4                                  SMBIOS/DMI table decoder
ii  libsmbclient                                  2:3.6.3-2ubuntu2.3                      shared library for communication with SMB/CIFS servers
ii  python-smbc                                   1.0.13-0ubuntu1                         Python bindings for Samba clients (libsmbclient)
ii  smbclient                                     2:3.6.3-2ubuntu2.3                      command-line SMB/CIFS clients for Unix
ii  smbfs                                         2:5.1-1ubuntu1                          Common Internet File System utilities - compatibility package

$ dpkg --list|grep -i cifs
ii  cifs-utils                                    2:5.1-1ubuntu1                          Common Internet File System utilities
ii  libsmbclient                                  2:3.6.3-2ubuntu2.3                      shared library for communication with SMB/CIFS servers
ii  smbclient                                     2:3.6.3-2ubuntu2.3                      command-line SMB/CIFS clients for Unix
```

I originally noticed that my other machine had "libpam-winbind" and "nautilus-share" installed and the machine with the issue did not.  Installing those two packages solved my errors with 'testparm -s', but did not fix my issue.

Finally, I tried to purge and reinstall these packages

[LIST]
[*]smbclient
[*]smbfs
[*]cifs-utils
[*]samba-common
[*]samba-common-bin
[/LIST]

Still no luck.  Again, it used to work; now it doesn't.  Very similarly configured machine works (but some packages are out of date on the working machine).  The NAS has only one interface/IP address, nmblookup works to find it's IP from it's hostname (from the machine with the issue) and it responds to a ping.  Please any help would be great.  I've been searching on AskUbuntu, SuperUser, ubuntuforums and plain old search engines for a week now and it's driving me crazy!

I have also posted this question on AskUbuntu.com (hopefully that's not a decision which will be met with hostility!)  Thanks!

---

### Post by skinnersbane on 2012-07-15
:(

---

### Post by skinnersbane on 2012-08-13
The problem was timeouts.  I somehow got my internal IP on the NAS's blocklist (which I have configured to never expire).  Problem fixed.

---

