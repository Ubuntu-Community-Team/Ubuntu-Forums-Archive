---
title: "Mounting a Windows Sub-Directory (not the whole shared folder)"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by matrim33 on 2009-02-02
Does anybody know if there is a way to mount only a sub-directory of a Windows shared drive?  For example:

I can currently mount a Windows network drive with the following command:

    sudo mount -t cifs -ouser=<user>,password='<passwd>',uid=<user>,gid=<user>,rw //150.150.150.1/shared /media/NetDrive/

This mounts the entire shared drive to /media/NetDrive/


For security reasons, I would like to mount only a specific directory in the shared drive (i.e. /directory/to/folder/ - so that a user can not access anything in /directory/ or /directory/to/ ).  I have tried this:

    sudo mount -t cifs -ouser=<user>,password='<passwd>',uid=<user>,gid=<user>,rw //150.150.150.1/shared/directory/to/folder /media/NetDrive/

But this does not work.


Is it possible to do what I am asking?  Or does Windows require that you mount the entire drive?

Thank you very much for your help.

-matrim

---

### Post by kidders on 2009-02-03
Hi there,

Technically, what you're describing isn't possible, but there might be a way to make it *seem* as though that's what you've done. Imagine you have a share called //windows-box/Shared, but you only want people to see one subdirectory of it (eg "/Public"). See if this works ...```
# Become root
sudo su

# Create a directory & mount your share there
mkdir -p /mnt/.private/windows-box
mount -o username=whatever //windows-box/Shared /mnt/.private/windows-box

# Create another directory & remount a subdirectory of the share
mkdir -p /mnt/windows-box
mount -o bind /mnt/.private/windows-box/Public /mnt/windows-box

# Lock everyone out of the directory tree where the share is mounted
chmod o-rwx /mnt/.private

# Give up root privs
exit
```

Assuming that works to your satisfaction (or at all, for that matter!), don't forget to unmount in reverse order ...```
sudo umount /mnt/windows-box /mnt/.private/windows-box
```

Is that any help?

---

### Post by matrim33 on 2009-02-04
Thank you for your response.  This looks promising - I will try it today and let you know if it works for me.  

Another thought I had was to mount the windows share on a separate, private, Ubuntu machine (that does not have the same security constraints) and then use sshfs to mount only the desired directory on the machine that is public.  This is a round about way, but it might work.

Thanks again for your help.  I'll update this thread once I've tried these methods.

---

### Post by kidders on 2009-02-04
No problem.

> **matrim33 said:**
> Another thought I had was to mount the windows share on a separate, private, Ubuntu machine (that does not have the same security constraints) and then use sshfs to mount only the desired directory on the machine that is public.I wouldn't recommend that option. It would greatly increase network traffic, and the differing feature sets of SFTP & Windows file sharing could create some very nasty quirks. The last time I tried anything like it with Ubuntu, I re-shared a Samba filesystem over AFP, and it resulted in kernel panics.

---

### Post by matrim33 on 2009-02-04
Ok, thanks for the heads up.  

I have tried your suggestion to use "mount -o bind" and it works like a charm.  Thanks once more for your help.:D

---

### Post by matrim33 on 2009-02-04
One more thing I found that was interesting.  I unmounted the windows share and I was still able to access the directory I mounted with bind!  Any idea if this mounted dir will persist until I unmount it as well?

Thanks

---

### Post by kidders on 2009-02-04
I'm not sure. It seems like the public subdirectory *ought* to continue working just fine.

That said, I don't know enough about what happens between the time a filesystem is detached from the hierarchy, and the all the references to it are cleaned up. That interval is normally less than a second, so I can't help wondering what might happen if it were stretched out for hours/days. At some point, the kernel might get tired of waiting for the locks on the half-unmounted share to be released, and bad things might start to happen.

Sorry I can't offer a proper answer ... my knowledge of the kernel isn't that detailed. :(

---

### Post by matrim33 on 2009-02-05
No worries.  I appreciate the help you have been able to give so far.

Last night I went ahead and used bind to mount a few directories from a number of different shared drives and they are working fine as of now (I unmounted each of these different shares and only have the binded directories mounted now).  I will let you know if I do run into any issues with this.

This seems like a simple question, but 5-10 minutes of googling and a quick look at the man page didn't get me the answer and I thought I'd see if you happened to know this off-hand - how do I unbind a directory?  No problem if you don't already know the answer - I know can figure it out, just fellin a bit lazy :D.

Thanks

---

### Post by kidders on 2009-02-05
> **matrim33 said:**
> how do I unbind a directory?Use **umount**.

---

### Post by matrim33 on 2009-02-06
Well, now I feel stupid.  I had tried before but got a "directory is busy" error.  Guess I should have tried again...


Thanks for all your help on this.  I think this will be a very nice solution to my problem.

---

### Post by kidders on 2009-02-06
Hehe... No problem.

---

