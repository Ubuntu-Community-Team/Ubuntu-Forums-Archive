---
title: "problems with preserving file modification times with NAS drive"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by alanh on 2009-02-27
I'm having problems with using a DNS-323 network drive, which, I think, is due to an issue with preserving file modification times.  This has been happening since I "upgraded" from 7.10 to 8.10 (I skipped 8.04).  The 8.10 upgrade was a clean installation.

The DNS-323 is in a mixed Windows-Linux environment, but I am using it within a Windows network.   The problem manifests in 2 ways.

1. When I use rsync to create a back-up of files from my USB drive to the DNS-323, it continually complains of "failed to set times on 'directory_name': Not a directory (20)" When I look at the properties of the backed-up files, they show a modification date of the back-up time, not that of the source file.   I have set rsync to preserve file modification times.  If I run rsync again it wants to update these files again, even though they haven't been modified on the USB drive.

2. When I locate my TB mailboxes on the DNS-323, TB continually downloads the same emails over and over, it fails to recognise that the email has already been downloaded from the POP server.

Both of these worked just fine under Gutsy.

Also, if I copy files to the DNS-323, using Nautilus "drag & drop", the file modification time is not preserved.

I'm aware of the problems since 8.04  with gvfs and Windows shares with passwords (patch now released and installed)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

 and the outdated authentication (LANManager) used by the DNS-323 (which I've fixed as advised in the following post)

[http://ubuntuforums.org/showpost.php?p=6238553&postcount=5](http://ubuntuforums.org/showpost.php?p=6238553&postcount=5)

 both of which had previously prevented me from even mounting the shares on the DNS-323.  

Now these are fixed, and the shares mount just fine, I'm stuck with this problem.  Any ideas, is it related to one of these issues, or completely seperate?

---

