---
title: "NFS share: write problems"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by TeKniKal on 2010-06-03
I am having troubles with a mounted nfs share. I cannot copy any files to it as all programs say the operation is not permitted. But actually the file IS created (and empty) and afterwards I can write to the file without any problem. Has anyone encountered this before or any tips to solve this?

On the **server** (Gentoo Linux), it concerns 2 NTFS(-3G) mounted partitions:

relevant part of /etc/fstab :
```
LABEL=Aldebaran /media/Aldebaran ntfs-3g user,uid=egon,gid=users,umask=002     0    0
LABEL=Betelgeuse /media/Betelgeuse ntfs-3g user,uid=egon,gid=users,umask=002    0    0

```relevant part of ls -l /media:
```
drwxrwxr-x 1 egon users 4096 Jun  4 00:56 Aldebaran
drwxrwxr-x 1 egon users 4096 Jun  4 00:57 Betelgeuse
```/etc/exports
```
/media/Aldebaran 192.168.1.0/16(async,rw,no_subtree_check)
/media/Betelgeuse 192.168.1.0/16(async,rw,no_subtree_check)
```GID for users is 100, UID for egon is 1000.

Using my user account (egon), on the server, I can without a problem run following commands:
```
egon@server /media/Aldebaran/Movies $ cp movies.txt movies.txt2
egon@server /media/Aldebaran/Movies $ touch movies.txt3
egon@server /media/Aldebaran/Movies $ echo foo > movies.txt3
```On the **client** side (Ubuntu Lucid Lynx 10.04):
relevant part from /etc/fstab
```
192.168.1.10:/media/Aldebaran /media/Aldebaran nfs rsize=8192,wsize=8192,timeo=14,intr,user 0 0
192.168.1.10:/media/Betelgeuse /media/Betelgeuse nfs rsize=8192,wsize=8192,timeo=14,intr 0 0

```relevant part from running ls /media
```
drwxrwxr-x 1 egon users 4096 2010-06-04 00:56 Aldebaran
drwxr-xr-x 2 root root  4096 2010-05-30 01:06 Betelgeuse
```UID for egon is 1000, GID for users is 100 (and GID for egon is 1000)

When running the same commands as my regular user (egon) or local root, I get:
```
egon@Egon-PCx:/media/Aldebaran/Movies$ cp movies.txt movies.txt2
cp: cannot create regular file `movies.txt2': Operation not permitted
egon@Egon-PCx:/media/Aldebaran/Movies$ touch movies.txt3
egon@Egon-PCx:/media/Aldebaran/Movies$ echo bar > movies.txt3
```So that is the actual error is the first command: I can both create files and write to files, but not the two operations combined.

At the moment, I don't see what the problem is; so I could really use any advice from anyone who has more experience with NFS (I have virtually none).

---

### Post by sgosnell on 2010-06-03
Sounds like a permissions problem.  Who is actually the owner of the folder, and the files in it?  You can find out with Nautilus.  My NFS shares show the owner as 0, and I have to use sudo to make any file changes from the client.  I have to do that on the server, too, and that may be because I don't have the permissions set properly.  I'm still learning NFS too.

---

### Post by TeKniKal on 2010-06-04
> **sgosnell said:**
> Sounds like a permissions problem.  Who is actually the owner of the folder, and the files in it?  You can find out with Nautilus.  My NFS shares show the owner as 0, and I have to use sudo to make any file changes from the client.  I have to do that on the server, too, and that may be because I don't have the permissions set properly.  I'm still learning NFS too.

Indeed, sounds like a permission problem; but as you can see from my listings (ls -l at server and client), the mount points are owned by egon:users. All files inside it are also owned egon:users.

Currently, I have also tried to disable ACL usage (as I've read similar problems exist on vfat partitions due to absence of ACL on vfat) over NFS with the noacl option in fstab on the client, but without result. As it might be a problem on vfat, perhaps ntfs is also problematic (although ntfs works with ACLs on Windows, perhaps there is no direct support for Linux ACLs on NTFS?). From what I read, it could possibly be solved by reformatting to a proper Linux file system; but I only want to use that as a last resort (it's about 1.1 TiB of data).

---

### Post by sgosnell on 2010-06-04
I think the permission problems are in the server settings, and I have never used Gentoo, so I don't know where to start there.  I'm using Ubuntu server, and haven't really gotten deeply into the technical details.  I do agree that you shouldn't need to reformat the drive, and I don't think the file format has anything to do with the permissions.

---

### Post by TeKniKal on 2010-06-04
> **sgosnell said:**
> I think the permission problems are in the server settings, and I have never used Gentoo, so I don't know where to start there.  I'm using Ubuntu server, and haven't really gotten deeply into the technical details.  I do agree that you shouldn't need to reformat the drive, and I don't think the file format has anything to do with the permissions.

I don't think the different distributions are a great problem; I chose Gentoo as that has a few advantages (or differences I found interesting):

[LIST]
[*]More basic than Ubuntu Server (can run with lower resources, doesn't run unneeded services, ...)
[*]Allows me to learn more of the technical details of Linux, while in Ubuntu you don't have to; I've learned a lot from this experience.
[*]Also has a package management system with repositories (like dpkg/apt on Ubuntu), but it needs you to compile everything from source (portage/emerge)
[/LIST]
But in essence, when working on the command line, both feel very similar. In any case: don't worry about the Gentoo part, I will 'translate' all Ubuntu specific things to Gentoo specific terms.

---

