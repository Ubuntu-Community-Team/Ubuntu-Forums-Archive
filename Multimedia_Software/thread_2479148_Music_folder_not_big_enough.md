---
title: "Music folder not big enough??"
date: 2022-09-15
forum: Multimedia Software
---

### Post by drumone on 2022-09-15
I have a music library that is close to 200GB and growing. My current Music folder isn't big enough to hold my library. It's currently 27.7 GB, according to the Properties. When I tried downloading most of my music from my iPod, it wouldn't let me do any more once the folder was full. Is there a way to increase the size of my music folder to accommodate my ever growing music collection? Also, what software is recommended for managing my library and iPod (160 GB Classic, Model A1238)? Thanks!

Specs:
1 TB Samsung 980 Pro NMVe SSD
Partition 1 (Filesystem) - 537 MB FAT
Partition 2 (Swap) - 66 GB Swap
Partition 3 (Filesystem) - 883 GB Ext4
Partition 4 (Filesystem) - 51 GB Ext4

---

### Post by SeijiSensei on 2022-09-15
Where is the Music folder located? You have two partitions. Is the folder in the 883 GB partition or the 51 GB one?

One option is to get of that big swap partitions. It's certainly large enough to house Music and other stuff. How much physical memory is on the machine? Usually swap is set to twice the size of the physical memory.

You don't need a dedicated swap partition to enable swapping. Linux can use a regular file instead. 

[https://linuxize.com/post/how-to-add-swap-space-on-ubuntu-20-04/](https://linuxize.com/post/how-to-add-swap-space-on-ubuntu-20-04/)

---

### Post by &amp;KyT$0P# on 2022-09-15
> **Neil_Harbel said:**
> Is there a way to increase the size of my music folder to accommodate my ever growing music collection?

Please post the output from running the following commands in Terminal -
```
findmnt
df -Th
```
(* oops, collided posting with SeijiSensei.  Posting these outputs will answer SeijiSensei's questions.)

> Also, what software is recommended for managing my ... iPod (160 GB Classic, Model A1238)? 

If you want to manage your iPod directly from Ubuntu you could try gtkpod, which is available in standard Ubuntu repositories.

---

### Post by drumone on 2022-09-15
Music is located in the /Home folder. I have no clue where that file is located in terms of partitions. I currently have 64 GB of RAM and will later upgrade it to 128 GB.

---

### Post by drumone on 2022-09-15
findmnt command output:

```
TARGET                               SOURCE           FSTYPE  OPTIONS
/                                    /dev/nvme1n1p4   ext4    rw,relatime,errors
&#9500;&#9472;/sys                               sysfs            sysfs   rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/kernel/security             securityfs       securit rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/fs/cgroup                   cgroup2          cgroup2 rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/fs/pstore                   pstore           pstore  rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/firmware/efi/efivars        efivarfs         efivarf rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/fs/bpf                      bpf              bpf     rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/kernel/debug                debugfs          debugfs rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/kernel/tracing              tracefs          tracefs rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/fs/fuse/connections         fusectl          fusectl rw,nosuid,nodev,no
&#9474; &#9492;&#9472;/sys/kernel/config               configfs         configf rw,nosuid,nodev,no
&#9500;&#9472;/proc                              proc             proc    rw,nosuid,nodev,no
&#9474; &#9492;&#9472;/proc/sys/fs/binfmt_misc         systemd-1        autofs  rw,relatime,fd=29,
&#9500;&#9472;/dev                               udev             devtmpf rw,nosuid,relatime
&#9474; &#9500;&#9472;/dev/pts                         devpts           devpts  rw,nosuid,noexec,r
&#9474; &#9500;&#9472;/dev/shm                         tmpfs            tmpfs   rw,nosuid,nodev,in
&#9474; &#9500;&#9472;/dev/mqueue                      mqueue           mqueue  rw,nosuid,nodev,no
&#9474; &#9492;&#9472;/dev/hugepages                   hugetlbfs        hugetlb rw,relatime,pagesi
&#9500;&#9472;/run                               tmpfs            tmpfs   rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/run/lock                        tmpfs            tmpfs   rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/run/credentials/systemd-sysusers.service
&#9474; &#9474;                                  none             ramfs   ro,nosuid,nodev,no
&#9474; &#9500;&#9472;/run/snapd/ns                    tmpfs[/snapd/ns] tmpfs   rw,nosuid,nodev,no
&#9474; &#9474; &#9500;&#9472;/run/snapd/ns/canonical-livepatch.mnt
&#9474; &#9474; &#9474;                                nsfs[mnt:[4026533619]]
&#9474; &#9474; &#9474;                                                 nsfs    rw
&#9474; &#9474; &#9500;&#9472;/run/snapd/ns/snapd-desktop-integration.mnt
&#9474; &#9474; &#9474;                                nsfs[mnt:[4026533620]]
&#9474; &#9474; &#9474;                                                 nsfs    rw
&#9474; &#9474; &#9492;&#9472;/run/snapd/ns/snap-store.mnt   nsfs[mnt:[4026533622]]
&#9474; &#9474;                                                   nsfs    rw
&#9474; &#9492;&#9472;/run/user/1000                   tmpfs            tmpfs   rw,nosuid,nodev,re
&#9474;   &#9500;&#9472;/run/user/1000/gvfs            gvfsd-fuse       fuse.gv rw,nosuid,nodev,re
&#9474;   &#9492;&#9472;/run/user/1000/doc             portal           fuse.po rw,nosuid,nodev,re
&#9500;&#9472;/snap/bare/5                       /dev/loop0       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/canonical-livepatch/146      /dev/loop1       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core/13425                   /dev/loop2       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core/13741                   /dev/loop3       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core18/2560                  /dev/loop4       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core18/2566                  /dev/loop5       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core20/1611                  /dev/loop6       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core20/1623                  /dev/loop7       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/gnome-3-38-2004/112          /dev/loop8       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/gnome-3-38-2004/115          /dev/loop9       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/gtk-common-themes/1535       /dev/loop10      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/snap-store/582               /dev/loop11      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/snap-store/592               /dev/loop12      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/snapd/16292                  /dev/loop13      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/snapd/16778                  /dev/loop14      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/snapd-desktop-integration/14 /dev/loop15      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/vlc/2344                     /dev/loop16      squashf ro,nodev,relatime,
&#9492;&#9472;/boot/efi                          /dev/nvme0n1p1   vfat    rw,relatime,fmask=
```

df -Th command output: 

```
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  6.3G  2.5M  6.3G   1% /run
/dev/nvme1n1p4 ext4    47G   19G   26G  42% /
tmpfs          tmpfs   32G   77M   32G   1% /dev/shm
tmpfs          tmpfs  5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p1 vfat    96M   33M   64M  34% /boot/efi
tmpfs          tmpfs  6.3G  8.2M  6.3G   1% /run/user/1000
```

---

### Post by &amp;KyT$0P# on 2022-09-15
> **Neil_Harbel said:**
> findmnt command output:
```

TARGET                               SOURCE           FSTYPE  OPTIONS
/                                    /dev/nvme1n1p4   ext4    rw,relatime,errors
&#9500;&#9472;/sys                               sysfs            sysfs   rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/kernel/security             securityfs       securit rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/fs/cgroup                   cgroup2          cgroup2 rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/fs/pstore                   pstore           pstore  rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/firmware/efi/efivars        efivarfs         efivarf rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/fs/bpf                      bpf              bpf     rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/kernel/debug                debugfs          debugfs rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/kernel/tracing              tracefs          tracefs rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/sys/fs/fuse/connections         fusectl          fusectl rw,nosuid,nodev,no
&#9474; &#9492;&#9472;/sys/kernel/config               configfs         configf rw,nosuid,nodev,no
&#9500;&#9472;/proc                              proc             proc    rw,nosuid,nodev,no
&#9474; &#9492;&#9472;/proc/sys/fs/binfmt_misc         systemd-1        autofs  rw,relatime,fd=29,
&#9500;&#9472;/dev                               udev             devtmpf rw,nosuid,relatime
&#9474; &#9500;&#9472;/dev/pts                         devpts           devpts  rw,nosuid,noexec,r
&#9474; &#9500;&#9472;/dev/shm                         tmpfs            tmpfs   rw,nosuid,nodev,in
&#9474; &#9500;&#9472;/dev/mqueue                      mqueue           mqueue  rw,nosuid,nodev,no
&#9474; &#9492;&#9472;/dev/hugepages                   hugetlbfs        hugetlb rw,relatime,pagesi
&#9500;&#9472;/run                               tmpfs            tmpfs   rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/run/lock                        tmpfs            tmpfs   rw,nosuid,nodev,no
&#9474; &#9500;&#9472;/run/credentials/systemd-sysusers.service
&#9474; &#9474;                                  none             ramfs   ro,nosuid,nodev,no
&#9474; &#9500;&#9472;/run/snapd/ns                    tmpfs[/snapd/ns] tmpfs   rw,nosuid,nodev,no
&#9474; &#9474; &#9500;&#9472;/run/snapd/ns/canonical-livepatch.mnt
&#9474; &#9474; &#9474;                                nsfs[mnt:[4026533619]]
&#9474; &#9474; &#9474;                                                 nsfs    rw
&#9474; &#9474; &#9500;&#9472;/run/snapd/ns/snapd-desktop-integration.mnt
&#9474; &#9474; &#9474;                                nsfs[mnt:[4026533620]]
&#9474; &#9474; &#9474;                                                 nsfs    rw
&#9474; &#9474; &#9492;&#9472;/run/snapd/ns/snap-store.mnt   nsfs[mnt:[4026533622]]
&#9474; &#9474;                                                   nsfs    rw
&#9474; &#9492;&#9472;/run/user/1000                   tmpfs            tmpfs   rw,nosuid,nodev,re
&#9474;   &#9500;&#9472;/run/user/1000/gvfs            gvfsd-fuse       fuse.gv rw,nosuid,nodev,re
&#9474;   &#9492;&#9472;/run/user/1000/doc             portal           fuse.po rw,nosuid,nodev,re
&#9500;&#9472;/snap/bare/5                       /dev/loop0       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/canonical-livepatch/146      /dev/loop1       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core/13425                   /dev/loop2       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core/13741                   /dev/loop3       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core18/2560                  /dev/loop4       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core18/2566                  /dev/loop5       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core20/1611                  /dev/loop6       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/core20/1623                  /dev/loop7       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/gnome-3-38-2004/112          /dev/loop8       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/gnome-3-38-2004/115          /dev/loop9       squashf ro,nodev,relatime,
&#9500;&#9472;/snap/gtk-common-themes/1535       /dev/loop10      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/snap-store/582               /dev/loop11      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/snap-store/592               /dev/loop12      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/snapd/16292                  /dev/loop13      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/snapd/16778                  /dev/loop14      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/snapd-desktop-integration/14 /dev/loop15      squashf ro,nodev,relatime,
&#9500;&#9472;/snap/vlc/2344                     /dev/loop16      squashf ro,nodev,relatime,
&#9492;&#9472;/boot/efi                          /dev/nvme0n1p1   vfat    rw,relatime,fmask=

```
df -Th command output: ```

Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  6.3G  2.5M  6.3G   1% /run
/dev/nvme1n1p4 ext4    47G   19G   26G  42% /
tmpfs          tmpfs   32G   77M   32G   1% /dev/shm
tmpfs          tmpfs  5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p1 vfat    96M   33M   64M  34% /boot/efi
tmpfs          tmpfs  6.3G  8.2M  6.3G   1% /run/user/1000
```

Please post terminal output in code tags to preserve spacing and make it more readable (put [noparse]```
 at the beginning and 
```[/noparse] at the end).  I added code tags to the quote of your post so that I could read your outputs.

So you have two SSDs, but everything of your entire OS installation - including your home folder and music - is contained in a single 51 GB partition.  What are you using the other partitions for?  Are you dual booting another Linux distro?  Can you move your music collection to one of the partitions that has more space, maybe the 883 GB ext4 partition you mentioned in the first post?

---

### Post by drumone on 2022-09-15
I do have 2 SSDs. Primary OS is Ubuntu (1n1). Secondary on the 2nd SSD is Windows (0n1). My other partition on the Linux drive are unused at the moment. I discovered earlier today that Partition 1 (537 MB) and Partition 3 (883 GB) are both unmounted. Does that mean they aren't available/recognized? I assume Part 1 is for the root system or booting? Any idea what I would need to do to make the 883 GB accessible? I'm very much a novice when it comes to all of this! Thanks for your help!!!

---

### Post by &amp;KyT$0P# on 2022-09-15
"Partition 1" is an unused EFI system partition and it is normal for it to be unmounted.  For "Partition 3" I would say the first step would be to mount it to see what's on it.

---

### Post by SeijiSensei on 2022-09-16
Mount the big partition into the file system like this:

First create a "mount point" (actually just an empty directory) where the filesystem will be mounted. Let's use /data for now.
```

cd /
sudo mkdir /data

```
Now give it a whirl:
```
sudo mount /dev/nvme1n1p3 /data
```
(The p3 at the end of the device name references partition 3.)

You should be able to see the empty directory either with "ls /data" at the command prompt, or via a file browser.

Now let's make this permanent by adding it to /etc/fstab which contains all the various mounts. Edit that file with "sudo nano /etc/fstab" and add this line at the bottom:
```

/dev/nvme1n1p3     /data       ext4     defaults     0 0

```

(The nano editor has a handy menu of commands at the bottom. All of them require that you hold down the Ctrl key and type a letter. For instance, "^X", the command for exit, is Ctrl+X.)

---

### Post by TheFu on 2022-09-16
Just to add to the mount instructions just above this post, if it really is a native linux file system, ext3/4, then after it is mounted, the permissions are almost 100% set to be root:root for the owner and group.  You'll probably want to change that  Use this exact command, once:

```
$ sudo chown $USER:$USER /data
```

The permission/owner change will be remembered and if you mount through the /etc/fstab, it will be mounted at boot going forward.
```
$ ls -la /data 
```
will show your username for the owner and group ... probably with 'drwxrwxr-x' permissions on the directory.
Next, you'll want to move all the ~/Music to /data/Music ... at least I would.  
First, let's see the size so we can compare the old location to the new location by size.  It is a simple way to assure the data was actually moved.

```
$ du -hs ~/Music
```
Note the size.
Do the move:
```
$ mv ~/Music    /data/
```
That will take a few minutes ... perhaps 5+ minutes to complete depending on the performance of the target storage.  It will move everything from the top directory down.  Don't have any music playing or have a file manager in ~/Music while this move is happening.  Get some coffee or lunch or go for a walk after you see there aren't any errors being thrown.
```
$ du -hs /data/Music
```
See that the size is about (or exactly) the same as it was above.  Small differences are fine. Different block sizes and other file system internals will make them just a little bit different.

If there were any errors along the way, STOP immediately. Don't go further. 

After the move completes.  You'll want to make a symbolic link from /data/Music to ~/Music so your players and everything else keep working without any changes.
```
$ ln -s /data/Music ~/Music
```
That's it.
Now you'll want to add /data to your backup script/process.

Of course, there are lots of alternate ways to use the storage, but having large media files outside the /home/ area is a smart thing.  Using symbolic links to make access easy is very common and has few negative effects, unlike other methods.  Lots of people use this symbolic link technique for their Photos, Documents, Videos, Music, and Games.  But it is your system.

For the /etc/fstab, I'd create a LABEL (say DATA) for the partition using **gparted**, then change the mount like to be this:
```
LABEL=DATA     /data       ext4     nofail,noatime,errors=remount-ro     0     2
```
If you don't put a LABEL on the PARTITION, this won't work.  

You can lookup what those options mean, if you are interested.  You could use a UUID instead of a LABEL too, but humans understand LABEL better than long, random, UUIDs. The last '2' tells the mount system to run fsck at a different priority than for the OS, but it will still be run from time to time. That is very good and useful.  The old '0' value would never run an fsck. That's not good for native Linux file systems, IMHO.  I have my file systems set to run an fsck every 30 days. Seems like a reasonable compromise. With ext3/4 file systems, since they are journaled, running an fsck is fast.
If the file system was NTFS or FAT-something, then I'd still use LABEL, but not run any fsck and would leave the last '0' in the fstab there.   Every field in the fstab is explained.  **man  fstab** has the explanations.

---

### Post by drumone on 2022-09-16
[[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")[COLOR=#000000] and TheFu - Thank you for all of the steps and directions! I followed all of the steps by copying and pasting. I created the /data directory and ALL of the things you recommended. All the links worked and it looked like everything was good. [COLOR=#000000]However, something went screwy and I can't quite figure out why. When I rebooted, the partition I mounted is now mounted somewhere completely different! It also has a UUID. I was able to find the drive this time by going into "Other Locations". This partition is now mounted at /media/drumone/52b7184e-9a58-43c5-b108-2572340a5533. Not at all what I thought was created. I'm not even sure where that came from. Now the links that were created don't work.

Everything was there as far as all the files I moved from the "Home" folder, plus duplicates and other things that I had previously deleted. A folder with my name was created and in that folder were all the subfolders previously found in the "Home" folder. It was a really weird combo of foiders and files, some current others not. Now, when I click on the usual Documents, Music, Pictures, Videos, or Downloads folders (on the left side of a Files window) I get this message: Unable to find "/home/neil/Downloads" (or whatever folder I'm trying to access). 

So now for my questions... 1. Do I change the mount point to /data somehow?  2. Do I need to change the mount point or is it better to leave it and change the links/references to it?  3. If not, how do I modify the above code to create the symbolic links?  4. When I go to do a back-up do I just add the main folder on the 883 GB volume?

Thank you again for your time and patience with a "programming illiterate" user. I appreciate your help!
[/COLOR][/COLOR]

---

### Post by TheFu on 2022-09-16
Please show the files we said to modify.
a) prove that a label was added.
b) prove the /etc/fstab is changed to match the label you added

If the label wasn't added or the fstab wasn't actually modified, then when you open a file manager, some of those will try to mount things in some "safe", but sucky place.  That's what happened.  You don't want that.

If you used the device name ... nvmexxyyzz ... then that can change from boot to boot, so mount instructions in the fstab don't work.  We have to use things that won't change between boots - LABEL or UUID are the normal methods.  Of course, if some other Linux file system was on the NVMe partition, say ZFS or btrfs or LVM, then all bets are off. There are other things necessary.

BTW, if you might have multiple DATA drives, it would be smart to LABEL  them as DATA01, DATA02, DATA03.

---

### Post by drumone on 2022-09-17
Due to other issues, that I've been chasing down in other threads, I ended up re-installing my entire system! Both OS were swapped on the SDDs. As a result, I let Ubuntu do all the work on the install. I now have a huge drive and all the room I could ask for. I ALMOST went with LVM, but decided against it for now. I don't have the time to research and learn about it properly right now. As it is, I'm struggling to learn C++ for my degree. Other stuff is just going to have to wait.

Thanks for all of your help! When I am able to branch out and expand my learning into these areas, I fully intend to come back to all of this to help me figure things out. Thanks again!!!

---

