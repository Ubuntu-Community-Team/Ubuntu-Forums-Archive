---
title: "write protected samba shares with mounted disks"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by jero3n on 2009-03-15
I have a problem with permissions on samba shares and I am totally confused.

I have a file server with Ubuntu 8.10 and an internal IDE disk which is mounted as (fstab):

UUID=d9b340b2-c840-4f1b-8f65-e918823d5bb4 /disks/public ext3 relatime 0 2

Permissions of /disks/public folder: drwxrwxr-x

and it is shared as (smb.conf) :
[public]
    path = /disks/public
    browseable = yes
    read only = no
    writable = yes
    guest ok = no
    create mask = 0744
    directory mask = 0755
    force user = john
    force group = john

Now, I test it by connecting from a client as
smbclient //server.local/public -U john
and when I try to write anything like:
smb: \> mkdir  test
I get:
NT_STATUS_MEDIA_WRITE_PROTECTED making remote directory \test

After a few hours of trying meaningless things, I managed to make it work *only* with this series of actions:

1. Create a new folder
2. Edit smb.conf to share it.
3. Restart samba server
4. Connect from samba client
5. Mount disk to that folder
6. Disconnect and reconnect samba client

and now I have write permissions to the samba share, but of course it does not work after restart.

Needless to say that any other samba share just works.

Am I doing something totally wrong? Any ideas?

---

### Post by jero3n on 2009-03-16
I found an obvious workaround on this, I made a share on the folder "disks" (which contains the mountpoint) and I am able to write in folder "public" 

However is not an accepted way to solve it. Since the user "john" is the owner of the mountpoint /disks/public I cannot understand why samba server denies write access to this folder only after mounting the ext3 partition.

Has anyone else see this? Is it a bug? Have I misunderstood anything?

---

### Post by capscrew on 2009-03-16
> **jero3n said:**
> I found an obvious workaround on this, I made a share on the folder "disks" (which contains the mountpoint) and I am able to write in folder "public" 

However is not an accepted way to solve it. Since the user "john" is the owner of the mountpoint /disks/public I cannot understand why samba server denies write access to this folder only after mounting the ext3 partition.

Has anyone else see this? Is it a bug? Have I misunderstood anything?

You can't use the folder (directory) as a place to create files and other directories when you use it as the mountpoint.  All files and folders are in that directory (the mountpoint are unavailable to you.

---

### Post by jero3n on 2009-03-16
> **capscrew said:**
> You can't use the folder (directory) as a place to create files and other directories when you use it as the mountpoint.  All files and folders are in that directory (the mountpoint are unavailable to you.

I dont use this folder for any other purpose than a mountpoint for the partition.

Let me clear this out:
- When the partition is not mounted to folder "public" I have write access through samba to this folder (I tried just for testing)
- If the partition is mounted, I have read-only access through samba to the mountpoint

---

