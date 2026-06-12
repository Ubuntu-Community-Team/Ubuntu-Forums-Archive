---
title: "Mount subversion repository as home folder?"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by miggl on 2009-01-17
Hi all,

We are attempting to set up a subversion repository as a main location for all our users' home folders. To do this best, we thought we would mount the specific repository in /etc/fstab as /home/username.

Any ideas on how to do this? I've seen plenty of examples mounting network drives, so that's not really the problem. My main question here would be what mount type we should use.

Alternatively, is there a better system for making a file server that supports file versioning?

Thanks!
Mike

---

### Post by nixscripter on 2009-01-18
Uh, what problem are you trying to solve exactly?

Subversion means that you **don't** have to mount network devices, but keep things in sync with commits and updates.

Network mounts (such as NFS) also don't have versioning or the facilities of change management and tracking subversion has.

In short, these are two entirely different things for entirely different purposes. If you just want all home directories in one location, use NFS. If you want to track changes for some reason, use Subversion with local working directories.

---

### Post by miggl on 2009-01-18
Hi nixscripter,

But that's exactly the point: since NFS doesn't provide file versioning, and Subversion requires manual commits and updates, I was hoping to combine the two to get the best of both worlds.

Since subversion can be accessed via webdav protocol, and webdav can also be mounted, I thouth this would be the perfect solution to provide a centralized storage mechanism that also provides versioning.

The reason I don't want to have "working folders" on the users' workstations is that it should be transparent to them: any changes they make in their home folder should automatically be committed.

---

### Post by nixscripter on 2009-01-19
Hmm, didn't know that...

In that case, I would suggest skipping NFS and using [davfs]("http://dav.sourceforge.net/"), a WebDAV filesystem.

---

