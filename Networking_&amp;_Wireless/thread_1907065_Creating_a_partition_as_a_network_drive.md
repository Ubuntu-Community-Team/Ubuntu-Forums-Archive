---
title: "Creating a partition as a network drive"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by vezinadj on 2012-01-10
So here is what I am trying to accomplish, and I figured id ask someone with a little more knowledge on the topic before I start pounding away trying to figure this out.

I have a Linux box that is running Ubuntu 10.10 with a 500mb partition. 

What I am trying to do is to be able to access the 500mb partition as a network drive from a PC running Windows 7. The Windows 7 PC needs read write permissions to the network drive (partition on the linux box).

My reasoning for this is that the Windows PC and the Linux box need to share specific files for some applications Engineered, and instead of using samba (which was going to be my first option cause I hear is a great file sharing application), create a lone drive partition and make the rest of the Linux box partitions inaccessible (for security reasons). This seems like the most logical to me for security purposes.  

I guess the real question is, how would I go about's setting up the Linux partition so it can be accessed through the network and what permissions could I add to this drive (drive is partitioned as NTFS but can be changed if there is a better solution)? The drive will need to be mounted on boot (which I think you can edit in the fstab file and the exports file) and be all set to be connected to.

Anything to point me in the right direction or any tips in which would be a better way to accomplish this would be great! :)

Thank you in advance!

---

### Post by vezinadj on 2012-01-10
So here is what I am trying to accomplish, and I figured id ask someone  with a little more knowledge on the topic before I start pounding away  trying to figure this out.

I have a Linux box that is running Ubuntu 10.10 with a 500mb partition. 

What I am trying to do is to be able to access the 500mb partition as a  network drive from a PC running Windows 7. The Windows 7 PC needs read  write permissions to the network drive (partition on the linux box).

My reasoning for this is that the Windows PC and the Linux box need to  share specific files for some applications Engineered, and instead of  using samba (which was going to be my first option cause I hear is a  great file sharing application), create a lone drive partition and make  the rest of the Linux box partitions inaccessible (for security  reasons). This seems like the most logical to me for security purposes.   

I guess the real question is, how would I go about's setting up the  Linux partition so it can be accessed through the network and what  permissions could I add to this drive (drive is partitioned as NTFS but  can be changed if there is a better solution)? The drive will need to be  mounted on boot (which I think you can edit in the fstab file and the  exports file) and be all set to be connected to.

Anything to point me in the right direction or any tips in which would be a better way to accomplish this would be great! :smile:

Thank you in advance!

---

### Post by Morbius1 on 2012-01-10
* You don't necessarily have to share a separate partition in Samba to isolate it from the rest of the server. You create shares in samba and each share is separate entity.

* There is nothing wrong with sharing the NTFS partition. In fact it makes ownership and permissions somewhat easier since the permissions of all the files and directories that are currently there and all the files/folders that will be added will inherit the permissions and ownership of the mounted partition - defined through fstab. But that depends on how you want to use the share.

* If you go the NTFS route you can automount the partition by using a template. So let's say you want to have a partition that allows guest access:

```
UUID=66E4DC83E4DC56C1 /home/Shared ntfs defaults,nls=utf8,umask=000,windows_names 0 0
```You would have to create the mount point:
```
sudo mkdir /home/Shared
```Then find the correct UUID number:
```
sudo blkid -c /dev/null
```Then adjust the template for the correct mount point and UUID number and then mount the partition with the new fstab instructions:
```
sudo mount -a
```Everyone will have read / write access to that partition if you allow guest access in Samba. If you want to limit access to the partition to those that have credentials or to specific remote users you can always specify that in smb.conf when you create the share.

---

### Post by Mark Phelps on 2012-01-11
Windows doesn't understand Linux filesystems, so without using something like Samba, I don't believe you can do what you want.

If you want to share files between Linux and Windows, a much better solution is to have an NTFS partition.  Both Linux and Windows can read and write NTFS partitions.

---

### Post by Morbius1 on 2012-01-11
> What I am trying to do is to be able to access the 500mb partition as a  [COLOR=Blue]network drive[/COLOR] from a PC running Windows 7This isn't a dual boot question it's a Samba question so the filesystem on the "shared" partition really doesn't matter.

BTW, this is really a dual post. His original is here: [http://ubuntuforums.org/showthread.php?t=1907065](http://ubuntuforums.org/showthread.php?t=1907065)

---

### Post by oldfred on 2012-01-11
@vezinadj
Please do not create duplicate threads on the same topic. We are all volunteers here and some may waste time responding when you already have answers in the other thread.

Threads, merged.

---

