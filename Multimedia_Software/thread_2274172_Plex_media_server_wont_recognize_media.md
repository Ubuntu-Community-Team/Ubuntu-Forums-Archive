---
title: "Plex media server wont recognize media"
date: 2015-04-18
forum: Multimedia Software
---

### Post by joshua.stilwell on 2015-04-18
I'll start off by saying that i've ran Plex media server on a dedicated windows machine for several years.  I decided recently that i was going to void my home of any/all Microsoft based software.

After installing Ubuntu and Plex media server the UI for Plex seems to act perfectly normal.  You can navigate and add content to the server just like you can on the windows based version.

The issue you run into (and i've found this reoccuring across many, MANY posts) is that once you add content to the server, it doesn't actually recognize the content and gives a status of "Library scan complete: Extra information may still be downloading from the Internet".

couple things that you must do.  - Open your terminal

Add plex to the plugdev and root goups
```
sudo gpasswd -a plex plugdev
```
```
sudo gpasswd -a plex root
```

Verify the groups that Plex is associated with

```
groups plex
```

Output:
```
plex : plex **root plugdev**
```

Next you find the local of your media HDD..  This can be a little bit difficult to figure out.  Mine happened to be a dedicated 2TB drive, which made it easier.  If your media is located on a partition of your main drive, you will need to go by size, start/end sector (if you know your partition table) and what the file system is (NTFS/FAT)

```
sudo fdisk -l
```

Output:
```
josh@Plex:~$ sudo fdisk -l
[sudo] password for josh: 

Disk /dev/sda: 301.7 GiB, 323928170496 bytes, 632672208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x230e8900

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 628479999 628477952 299.7G 83 Linux
/dev/sda2       628482046 632670207   4188162     2G  5 Extended
/dev/sda5       628482048 632670207   4188160     2G 82 Linux swap / Solaris

Disk /dev/sdb: 1.8 TiB, 2000396746752 bytes, 3907024896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000b4704

Device     Boot Start        End    Sectors  Size Id Type
**/dev/sdb1        2048 3907024895 3907022848  1.8T  7 HPFS/NTFS/exFAT**

Disk /dev/sdc: 1.9 GiB, 2048728064 bytes, 4001422 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start     End Sectors  Size Id Type
/dev/sdc1         245 3999743 3999499  1.9G  c W95 FAT32 (LBA)


```

Next, Mount the partition into your file system by opening fstab as Root.  (This will open fstab with the permissions to save.)

```
sudo gedit /etc/fstab
```

At the very bottom of the file you need to add another line that includes the information for your media partition.  This is what i added. Note that i mounted mine in the standard 'videos' folder.  The Hard drive has always been called "Elements".  It is a NTFS drive.  You can also use "auto" instead.

```
/dev/sdb1 /home/josh/Videos/Elements ntfs rw,user,noauto,exec,utf8 0 0
```


restart your machine and you should be able to add media to your Plex server as normal.

---

