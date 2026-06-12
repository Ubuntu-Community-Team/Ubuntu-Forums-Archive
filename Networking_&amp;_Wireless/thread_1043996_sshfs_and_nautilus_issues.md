---
title: "sshfs and nautilus issues"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by emarkd on 2009-01-19
hello again friendly helpful people,

i'm working through my list of issues after upgrading my laptop to 8.10 and here's my latest problem:

i'm using sshfs to mount a remote directory on my laptop, and it seems to mount fine. from nautilus, i can then see the directory and it's contents and read the files, but i can't write to the directory tree. nautilus reports that there isn't enough free space, but there's plenty of space on the remote disk. nautilus can, however, delete and rename files. on top of that, if i use a shell and simply cp a file into the directory, it works fine. why would it work from the shell and not from nautilus? it all worked fine in 8.04.

thanks!

---

### Post by blackened on 2009-01-19
That's really weird. What is the filesystem on the network drive?

Are you mounting it to a location in the root file system or in your home directory?

---

### Post by emarkd on 2009-01-19
It's ext3 - another linux box.  And I'm mounting it under my home directory at ~/Documents/media.

---

### Post by blackened on 2009-01-19
On the remote machine, is the directory in a home directory or mounted to a subdirectory of root?

As an example: I have a secondary fat32 hd mounted to /mnt/data on my server, remotely mounted to a folder in my home directory on my laptop. It doesn't display any of the behavior you've mentioned.

My first guess would be some sort of permissions issue.

---

### Post by vanadium on 2009-01-19
You are probably also a victim of this bug. [https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/100116](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/100116)

[edit]Installing a newer version from jaunty appears to be easy and working: [http://ubuntuforums.org/showpost.php?p=6148532&postcount=8](http://ubuntuforums.org/showpost.php?p=6148532&postcount=8)

---

### Post by blackened on 2009-01-19
> **vanadium said:**
> You are probably also a victim of this bug. [https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/100116](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/100116)

[edit]Installing a newer version from jaunty appears to be easy and working: [http://ubuntuforums.org/showpost.php?p=6148532&postcount=8](http://ubuntuforums.org/showpost.php?p=6148532&postcount=8)

Good catch, that's probably it. I hadn't thought to search launchpad as it didn't look like a bug to me at first glance.

---

### Post by emarkd on 2009-01-19
The bug's the issue.  I see now that Nautilus reports the drive as having no free space in the bottom bar and it used to show 1000 GB - always.  I didn't think to check launchpad either.  Thanks for the help.

---

### Post by albinootje on 2009-01-19
> **emarkd said:**
> I see now that Nautilus reports the drive as having no free space in the bottom bar and it used to show 1000 GB - always.

Check the sshfs FAQ :

[http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq#Why_do_permissions_in_nautilus_not_work.3F](http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq#Why_do_permissions_in_nautilus_not_work.3F)

[http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq#In_Nautilus.2C_all_folders_are_reported_as_having_1TB_.281000.0_GB.29_free._Nice_but_not_at_the_same_time](http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq#In_Nautilus.2C_all_folders_are_reported_as_having_1TB_.281000.0_GB.29_free._Nice_but_not_at_the_same_time)...

[http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq#Why_does_df_return_strange_values_on_partitions_mounted_via_sshfs.3F](http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq#Why_does_df_return_strange_values_on_partitions_mounted_via_sshfs.3F)

---

### Post by emarkd on 2009-01-19
For anyone else having this issue that may stumble upon this thread, this bug goes away when you upgrade sshfs.  As of this writing, sshfs v2.0 is in the repositiories, but v2.2 has been released. If you can't wait for Ubuntu to get the newer version packaged, you can download and build it yourself from [http://fuse.sourceforge.net/sshfs.html]("http://fuse.sourceforge.net/sshfs.html").  Everything works fine after the upgrade.  Nautilus and df report the proper amount of free space and Nautilus happily writes new files into the directory.

Thanks again!

---

### Post by simonz on 2009-02-06
> **emarkd said:**
> For anyone else having this issue that may stumble upon this thread, this bug goes away when you upgrade sshfs.  As of this writing, sshfs v2.0 is in the repositiories, but v2.2 has been released. If you can't wait for Ubuntu to get the newer version packaged, you can download and build it yourself from [http://fuse.sourceforge.net/sshfs.html]("http://fuse.sourceforge.net/sshfs.html").  Everything works fine after the upgrade.  Nautilus and df report the proper amount of free space and Nautilus happily writes new files into the directory.

Thanks again!

I am having the same problem with sshfs. Sourceforge just has a tarball, I don't know how to build from that.  Where can I find a .deb file for the sshfs v2.2?

---

### Post by vanadium on 2009-02-06
See the edit to my post.

---

