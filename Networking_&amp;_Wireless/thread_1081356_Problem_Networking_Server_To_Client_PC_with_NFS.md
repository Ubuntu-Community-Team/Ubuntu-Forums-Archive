---
title: "Problem Networking Server To Client PC with NFS"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by DeepLake21 on 2009-02-26
I have a problem getting my client laptop to browse files in the desktop PC. Both have Ubuntu 8.10. The files reside in a folder called my_files in a fat32 partition. This partition is mounted in the desktop PC, and I export the mounted folder to the client PC. I would like both machines to boot up such that the desktop mounts the fat32 partition automatically on login, and the client to automatically load & mount the my_files directory from the server on boot as well.

I followed the tutorial by (czarism.com/easy...nfs-file-sharing). Here's my setup:

Desktop PC: I installed nfs-kernel-server and portmap. I use /etc/fstab to mount the fat32 partition:
/dev/sda9 /media/fat32 vfat defaults 0 0
and I use /etc/exports to export the following folder:
/media/fat32/my_files 192.168.1.0/24(rw,no_root_squash,asunc)

Client laptop: I installed nfs-common and portmap, I defined mount directory:
mkdir /mnt/shared/my_file
and I define in /etc/fstab:
192.168.1.100:/media/fat32/my_files /mnt/shared/my_files defaults 0 0

Problem: when the desktop boots, I boot the client. Now if I use Nautilus to browse /mnt/shared/my_files in the client laptop, I don't see any file, I get the busy mouse pointer, and in the desktop the /media/fat32 is hung. Furthermore, if :mad:I re-start the desktop, the pc would hang 2/3 of the way through.

The only work-around to get this to work is to browse the /media/fat32/my_files on the desktop BEFORE I try to first browse my_files in the client machine; with this workaround both PCs are happy.

WHat do I need to do to get the set-up to work as intended? I appreciate any help.

---

### Post by nixscripter on 2009-02-27
The problem sounds like the fat32 filesystem isn't mounted before the client tries to browse it, which makes it mount, and then NFS kick in.

Try adding the fat32 filesystem to **/etc/fstab** on the desktop and have it mounted at boot time.

---

### Post by miegiel on 2009-02-27
> **DeepLake21 said:**
> 
Client laptop: I installed nfs-common and portmap, I defined mount directory:
mkdir /mnt/shared/my_file
and I define in /etc/fstab:
192.168.1.100:/media/fat32/my_files /mnt/shared/my_files defaults 0 0


you made a typo in "/mnt/shared/my_file**S**"

also to check if /etc/fstab works as intended

```
sudo mount -av
```

-a option : mount all stuff from /etc/fstab 
-v option : tells you what is being done

---

### Post by DeepLake21 on 2009-02-27
Thanks for your responses.

I agree; it does sound like the desktop server is exporting the file-system for my_files of the fat32 system to the client *before* it is mounted from the partition! This is terrible. I would have anticipated that Linux developers would have anticipated this scenario. 

I am curious why browsing the my_file folder in Nautilus of the server desktop before I boot my laptop does the trick; but it is awkward to constantly manually do that each tome I log-in to the two PCs (unless someone can tell me how to do that using a script) .

---

### Post by AlFrugal on 2009-03-17
I'm having a problem similar to the OP. Here is my setup:

NFS Server: 

1. Running Fedora 9
2. Static IP: 192.168.1.150
3. /etc/exports:  
	/mnt   192.168.1.0/255.255.255.0(rw)
	/mnt/windows   192.168.1.0/255.255.255.0(rw)
	/mnt/large_downloads   192.168.1.0/255.255.255.0(rw)
4. /mnt has two files systems mounted on it:  /windows (FAT32)  and /large_downloads (ext3)
5. /etc/fstab entries for the two subdirectories of /mnt:
   UUID=768B-E069  /mnt/windows  vfat  uid=1000,gid=1000,umask=0000 0 0
   UUID=4f26a47f-28c3-4e5e-b6d0-6817891af123 /mnt/large_downloads ext3 defaults 1 2
   (I changed the uid, gid from 500 to 1000 to match my client)
6. My user account has UID=500,GID=500



NFS Client:

1. Running Ubuntu 8.04
2. Dynamic IP  (set by DHCP)
3. I manually issue: sudo mount -t nfs 192.168.1.150:/mnt/windows  /mnt/nfs
4. My user account has UID=1000,GID=1000


I can mount and access /mnt/large_downloads (which is ext3) OK on the NFS client. I can mount /mnt/windows (which is FAT32) on the NFS client. Both "df" and "/proc/mounts" show that /mnt/windows is mounted. I try to access /mnt/windows on the client via GNOME -> Places -> Computer -> Filesystem -> /Mnt -> NFS. I too get the busy mouse pointer, and nothing is displayed. The file manager on my NFS server hangs. When I try to reboot my NFS server, the shutdown hangs.

My NFS server is capable of running NFS Version 2,3, and 4. According to /proc/mounts, apparently my client is running NFS Version 3.

Unlike the OP, my target file system (/mnt/windows) is premounted via /etc/fstab. I've not found any way to get this NFS share of the fat32 partition to work.

---

### Post by punx45 on 2009-03-17
is it absolutely necessary that the drive is FAT32?   From a quick google, i get the impression that NFS and FAT don't really play nice.   it does seem ridiculous, but you could try exporting the FAT with samba instead.

---

### Post by AlFrugal on 2009-03-18
No, it isn't absolutely necessary that the partition is FAT32 but it would make things a lot easier for me if I could make the FAT32 NFS share work.

NFS and FAT32 might not get along well, but according to the NFS FAQ, NFS does have limited support for FAT32. I only need to have read access to the FAT32 partition so that I can make a copy. According to the FAQ, read access is supported.

The FAT32 partition contains tens of thousands of files and its size is 11 GB. I have an ext3 data partition on my HDD, and I could migrate the FAT32 partition into the ext3 partition and then use NFS to access the ext3. But I'd much rather just get NFS to access the FAT32 partition.

If I absolutely can't get NFS to access the FAT32 partition, then migrating that partition to ext3 would be easier for me than getting involved with samba. I already have linux learning overload.

The FAT32 partition is a holdover from when I used to run Windows ME. I now have Windows XP on my multiboot PC but I rarely run it.

---

### Post by punx45 on 2009-03-18
hmm..   looks like from your first post you are exporting the FAT partition read/write

```
/media/fat32/my_files 192.168.1.0/24([COLOR="Red"]rw[/COLOR],no_root_squash,asunc
```

you could try changing that to ro and see if that makes a difference.

---

### Post by AlFrugal on 2009-03-18
punx45: I gave your suggestion a try.

I edited /etc/exports to export my FAT partition as ro

On the client, I mounted the FAT partition -r

As before, the mount was successful. /proc/mounts confirmed the partition was mounted readonly.

However, when I tried to view the files of the mounted filesystem, I got the same result as before, the busy mouse pointer.

---

