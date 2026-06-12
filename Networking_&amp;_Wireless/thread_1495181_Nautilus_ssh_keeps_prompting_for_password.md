---
title: "Nautilus ssh keeps prompting for password"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by rabideau on 2010-05-27
I have 4 machines running 10.04 32 bit Intel--- all use SSH to connect to a remote server drive (disk).  All except one of the machines work just fine when accessing the remote drives.  The fourth PC keeps asking for a password with every directory change.

If I select cancel three times (on the troublesome unit), the desired directory opens but then the same routine occurs with the next directory change.

Any ideas what might be amiss????  What can be done to fix the problem???

---

### Post by steamboatsailor on 2010-06-08
I was in the same problem and did the trail'n'error-method... When I have created an ssh-key in Seahorse the problem suddenly disappeared. :-)
If you don't want to create a ssh-key try uninstall Seahorse. But I recommend to use Seahorse and create ssh-keys (at last I got "thumbs out" and did something I have planed for years when I created the ssh-key).

---

### Post by lien_meat on 2010-07-01
ok, I need this problem resolved.  I have the same issue in lucid.  It not only affects nautilus, it also affects bzr+ssh...  it seems to be an issue with ssh-askpass-gnome or gnome-keyring or something.  If anyone figures this out I need to know.  This is a serious issue for me, as I can't make certificates every time...it's not always possible.

---

### Post by lien_meat on 2010-07-01
actually, even when I do make a certificate, it still prompts me for a password, and then it works, until I try navigating to a new dir, then it asks AGAIN.  This is just stupid.

---

### Post by claytronic on 2010-08-23
Any update on this thread?  I started having this same prompting problem last Thursday for any Nautilus connections to SSH servers.

---

### Post by steamboatsailor on 2010-09-04
I found this [thread at launchpad]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/540280/comments/12") ([https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/540280/comments/12](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/540280/comments/12))

I uninstalled nautilus-bzr and tried to install it again. It's seams to work for me...  If not I can live without nautilus-bzr as I use Olive as GUI for bzr.

Steam on!

---

### Post by trideceth12 on 2012-02-14
Is this resolved yet... I am getting prompted every dir change using nautilus + openSSH (accessing my Nokia N9)

---

### Post by Perkins on 2012-02-21
It's not exactly a fix, but I generally use the sshfs fuse module instead of the Nautilus/Gnome system.  It's more reliable and more configurable.  Install the sshfs package from the repository, add yourself to the fuse group, and then just do

```
sshfs user@host:directory mountpoint
```

You can use ssh options with it to do things like enable compression.
Unmount with fusermount.
It has the advantage of being mounted on the filesystem in the place you specify without any of the Gnome VFS stuff so the files can be used and accessed even by programs that don't get along with VFS.

---

