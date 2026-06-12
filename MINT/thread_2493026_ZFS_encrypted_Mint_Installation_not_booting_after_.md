---
title: "ZFS encrypted Mint Installation not booting after a few updates"
date: 2023-11-30
forum: MINT
---

### Post by stump199 on 2023-11-30
Extremely  fresh installation, only about a day old. Yesterday when installing  from a live USB I had the single target drive encrypted using ZFS as  well as encrypting the home folder of the install. When booting into  mint today, it immediately thows "Error: checksum verification failed",  then prints the error shown. I have both passwords, and all I'm  concerned with is getting my files back. Any help is appreciated!

[IMG]https://i.redd.it/0ufz51p4283c1.jpeg[/IMG]

---

### Post by MAFoElffen on 2023-12-01
Being you are not Ubuntu, this will probable get moved from here to an "Other OS" (Mint) Section. This is a dedicated support section for Ubuntu & it's flavors. If it does, PM me with the link where it gets moved, so I can continue to help you.

Question: Did you just have an update involving 'zfs-dkms'?

Please run the system0info script in my signature line. When you go to run it do
```

./system-info --details

```
So it shows the ZFS details. Post the URL of where it uploads the report.

Boot from a recent installer LiveUSB... Open a terminal session.

This is from my notes for my contributions for boot-repair & boot-info
```

sudo su -
zpool export -a
zpool import -N -R /mnt rpool  # If this errors, and says it was previously used by another system, add "-f" right before "-N"
zpool import -N -R /mnt bpool  # If this errors, and says it was previously used by another system, add "-f" right before "-N"

# This unlocks the native encrypted zfs zpool
cryptsetup open /dev/zvol/rpool/keystore zfskey # this is where the keyfile is hidden and locked away
# Enter your passphrase for /dev/zvol/rpool/keystore: 

lsblk -e7 -o name,label,size,fstype
#NAME     LABEL                   SIZE FSTYPE
#sr0      Ubuntu 22.04 LTS amd64  3.4G iso9660
#zd0                              500M crypto_LUKS
#&#9492;&#9472;zfskey keystore-rpool          484M ext4
#vda                               30G 
#&#9500;&#9472;vda1                           512M vfat
#&#9500;&#9472;vda2                           1.4G crypto_LUKS
#&#9500;&#9472;vda3   bpool                   1.5G zfs_member
#&#9492;&#9472;vda4   rpool                  26.7G zfs_member

ls /dev/mapper
# control  zfskey

mount /dev/mapper/zfskey /media
ls /media
# lost+found  system.key

cat /media/system.key | zfs load-key -L prompt rpool
# <No output indicates that it unlocked without an error>

zfs list
# adapt this to the output from 'zfs list'
zfs mount $(zfs list | awk '/rpool\/ROOT\/ubuntu_...... / {print $1}' )
zfs mount $(zfs list | awk '/bpool\/BOOT\/ubuntu_...... / {print $1}' )
zfs mount -a

zfs list
#NAME                                               USED  AVAIL     REFER  MOUNTPOINT
#bpool                                              270M  1010M       96K  /mnt/boot
#bpool/BOOT                                         269M  1010M       96K  none
#bpool/BOOT/ubuntu_5ylu87                           269M  1010M      269M  /mnt/boot
#rpool                                             9.65G  16.0G      192K  /mnt
#rpool/ROOT                                        9.00G  16.0G      192K  none
#rpool/ROOT/ubuntu_5ylu87                          9.00G  16.0G     5.35G  /mnt
#rpool/ROOT/ubuntu_5ylu87/srv                       192K  16.0G      192K  /mnt/srv
#rpool/ROOT/ubuntu_5ylu87/usr                       580K  16.0G      192K  /mnt/usr
#rpool/ROOT/ubuntu_5ylu87/usr/local                 388K  16.0G      388K  /mnt/usr/local
#rpool/ROOT/ubuntu_5ylu87/var                      3.65G  16.0G      192K  /mnt/var
#rpool/ROOT/ubuntu_5ylu87/var/games                 192K  16.0G      192K  /mnt/var/games
#rpool/ROOT/ubuntu_5ylu87/var/lib                  3.64G  16.0G     3.48G  /mnt/var/lib
#rpool/ROOT/ubuntu_5ylu87/var/lib/AccountsService   212K  16.0G      212K  /mnt/var/lib/#AccountsService
#rpool/ROOT/ubuntu_5ylu87/var/lib/NetworkManager    260K  16.0G      260K  /mnt/var/lib/NetworkManager
#rpool/ROOT/ubuntu_5ylu87/var/lib/apt              98.2M  16.0G     98.2M  /mnt/var/lib/apt
#rpool/ROOT/ubuntu_5ylu87/var/lib/dpkg             61.3M  16.0G     61.3M  /mnt/var/lib/dpkg
#rpool/ROOT/ubuntu_5ylu87/var/log                  10.4M  16.0G     10.4M  /mnt/var/log
#rpool/ROOT/ubuntu_5ylu87/var/mail                  192K  16.0G      192K  /mnt/var/mail
#rpool/ROOT/ubuntu_5ylu87/var/snap                 2.64M  16.0G     2.64M  /mnt/var/snap
#rpool/ROOT/ubuntu_5ylu87/var/spool                 276K  16.0G      276K  /mnt/var/spool
#rpool/ROOT/ubuntu_5ylu87/var/www                   192K  16.0G      192K  /mnt/var/www
#rpool/USERDATA                                     142M  16.0G      192K  /mnt
#rpool/USERDATA/mikeferreira_hsfoy4                 142M  16.0G      142M  /mnt/home/mikeferreira
#rpool/USERDATA/root_hsfoy4                         360K  16.0G      360K  /mnt/root
#rpool/keystore                                     518M  16.5G     63.4M  -

mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run

cd /mnt
chroot /mnt /bin/bash --login
mount -a

```
Do what you need to do...

After you are through, to exit gracefully
```

exit
mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | \
    xargs -i{} umount -lf {}
zpool export -a
reboot

```
I would do first, before doing anything, connect and mount to an external drive and rsync all the data you need to backup off it, so you can rstore it if something goes more wrong. 

Fortunately, ZFS is farely flexible, and resilient. I just blew out this laptop (ZFS-On-Root, with 6 pools) earlier today. It's been a bit since my last snapshots. Back up and running now. But I am not a usual user.

---

### Post by deadflowr on 2023-12-01
Moved to Mint

---

### Post by MAFoElffen on 2023-12-01
I found it. Looking for your system-info report URL, and how it's going...

---

### Post by stump199 on 2023-12-01
First, thank you for your help. I'll try to clear up some things mentioned that I was unsure of before getting too specific with anything. 

> Did you just have an update involving 'zfs-dkms'?

I don't know the answer to this unfortunately. if it means anything, I only ran the automatic security updates from the built-in update manager. Everything else was left untouched since the install.


> Please run the system0info script in my signature line.

Where exactly should I run the script? Since I was probably a bit too vague on the exact setup, I should clarify that there is only one drive involved that is refusing to boot and is encrypted both with ZFS and the home folder encryption option (something I now understand as a mistake). 


> I would do first, before doing anything, connect and mount to an  external drive and rsync all the data you need to backup off it, so you  can rstore it if something goes more wrong. 

would I run into any issues doing this from a live-USB? If not, is this still possible given the added context of the setup?

---

### Post by stump199 on 2023-12-01
Another concerning issue is that when mounting through a live-USB the LUKS partition refuses to decrypt when entering the password I know to be correct, not sure how to prioritize this though. Or if it matters depending on where the data is.

---

### Post by MAFoElffen on 2023-12-01
From a LiveUSB... I was thinking, since you are encrypted, you can just run it normally from a LiveCD. It's not going to show much until unlocked.

---

### Post by stump199 on 2023-12-01
[https://paste.ubuntu.com/p/HYwwDsRyNn/](https://paste.ubuntu.com/p/HYwwDsRyNn/)

Here is the output of the script, very helpful stuff. How exactly would I back up the encrypted partitions? If necessary I have the disk space to do so, but the data I'm hoping to recover is only about 2GB and are nearly the only files on the install.

---

### Post by stump199 on 2023-12-01
I see now you meant backing up the data after decryption, I'll try the instructions you sent and report back.

---

### Post by stump199 on 2023-12-01
Tried the commands, got through it seemingly without errors but the drive still wasn't mounted. In the likely case that I'm missing something obvious I'll leave the commands/output of the terminal here: 

> mint@mint:~$ sudo su -
root@mint:~# zpool export -a
root@mint:~# zpool import -N -R /mnt rpool
root@mint:~# zpool import -N -R /mnt bpool
root@mint:~# cryptsetup open /dev/zvol/rpool/keystore zfskey
Enter passphrase for /dev/zvol/rpool/keystore: 
root@mint:~# lsblk -e7 -o name,label,size,fstype
NAME     LABEL                             SIZE FSTYPE
sda                                      465.8G 
&#9500;&#9472;sda1                                     512M vfat
&#9500;&#9472;sda2                                       2G crypto_LUKS
&#9500;&#9472;sda3   bpool                               2G zfs_member
&#9492;&#9472;sda4   rpool                           461.3G zfs_member
sdb      Linux Mint 21.2 Cinnamon 64-bit  28.9G iso9660
&#9500;&#9472;sdb1   Linux Mint 21.2 Cinnamon 64-bit   2.8G iso9660
&#9500;&#9472;sdb2   ESP                               4.1M vfat
&#9492;&#9472;sdb3   writable                         26.1G ext4
zd0                                        500M crypto_LUKS
&#9492;&#9472;zfskey keystore-rpool                    484M ext4
root@mint:~# ls /dev/mapper
control  zfskey
root@mint:~# mount /dev/mapper/zfskey /media
root@mint:~# ls /media
lost+found  system.key
root@mint:~# 
cat /media/system.key | zfs load-key -L prompt rpool
root@mint:~# zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              134M  1.62G       96K  /mnt/boot
bpool/BOOT                                         134M  1.62G       96K  none
bpool/BOOT/ubuntu_eeb9r4                           134M  1.62G      134M  /mnt/boot
rpool                                             40.3G   405G      192K  /mnt
rpool/ROOT                                        39.8G   405G      192K  none
rpool/ROOT/ubuntu_eeb9r4                          39.8G   405G     39.4G  /mnt
rpool/ROOT/ubuntu_eeb9r4/srv                       192K   405G      192K  /mnt/srv
rpool/ROOT/ubuntu_eeb9r4/usr                       632K   405G      192K  /mnt/usr
rpool/ROOT/ubuntu_eeb9r4/usr/local                 440K   405G      440K  /mnt/usr/local
rpool/ROOT/ubuntu_eeb9r4/var                       350M   405G      192K  /mnt/var
rpool/ROOT/ubuntu_eeb9r4/var/games                 192K   405G      192K  /mnt/var/games
rpool/ROOT/ubuntu_eeb9r4/var/lib                   347M   405G     99.9M  /mnt/var/lib
rpool/ROOT/ubuntu_eeb9r4/var/lib/AccountsService   244K   405G      244K  /mnt/var/lib/AccountsService
rpool/ROOT/ubuntu_eeb9r4/var/lib/NetworkManager    288K   405G      288K  /mnt/var/lib/NetworkManager
rpool/ROOT/ubuntu_eeb9r4/var/lib/apt               170M   405G      170M  /mnt/var/lib/apt
rpool/ROOT/ubuntu_eeb9r4/var/lib/dpkg             76.2M   405G     76.2M  /mnt/var/lib/dpkg
rpool/ROOT/ubuntu_eeb9r4/var/log                  1.83M   405G     1.83M  /mnt/var/log
rpool/ROOT/ubuntu_eeb9r4/var/mail                  192K   405G      192K  /mnt/var/mail
rpool/ROOT/ubuntu_eeb9r4/var/snap                  192K   405G      192K  /mnt/var/snap
rpool/ROOT/ubuntu_eeb9r4/var/spool                 276K   405G      276K  /mnt/var/spool
rpool/ROOT/ubuntu_eeb9r4/var/www                   192K   405G      192K  /mnt/var/www
rpool/USERDATA                                    2.96M   405G      192K  /mnt
rpool/USERDATA/root_267fvj                        1.23M   405G     1.23M  /mnt/root
rpool/USERDATA/stump_267fvj                       1.54M   405G     1.54M  /mnt/home/stump
rpool/keystore                                     518M   406G     63.4M  -
root@mint:~# zfs mount $(zfs list | awk '/rpool\/ROOT\/ubuntu_eeb9r4 / {print $1}' )
root@mint:~# zfs mount $(zfs list | awk '/bpool\/BOOT\/ubuntu_eeb9r4 / {print $1}' )
root@mint:~# zfs mount -a
root@mint:~# zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              134M  1.62G       96K  /mnt/boot
bpool/BOOT                                         134M  1.62G       96K  none
bpool/BOOT/ubuntu_eeb9r4                           134M  1.62G      134M  /mnt/boot
rpool                                             40.3G   405G      192K  /mnt
rpool/ROOT                                        39.8G   405G      192K  none
rpool/ROOT/ubuntu_eeb9r4                          39.8G   405G     39.4G  /mnt
rpool/ROOT/ubuntu_eeb9r4/srv                       192K   405G      192K  /mnt/srv
rpool/ROOT/ubuntu_eeb9r4/usr                       632K   405G      192K  /mnt/usr
rpool/ROOT/ubuntu_eeb9r4/usr/local                 440K   405G      440K  /mnt/usr/local
rpool/ROOT/ubuntu_eeb9r4/var                       350M   405G      192K  /mnt/var
rpool/ROOT/ubuntu_eeb9r4/var/games                 192K   405G      192K  /mnt/var/games
rpool/ROOT/ubuntu_eeb9r4/var/lib                   347M   405G     99.9M  /mnt/var/lib
rpool/ROOT/ubuntu_eeb9r4/var/lib/AccountsService   244K   405G      244K  /mnt/var/lib/AccountsService
rpool/ROOT/ubuntu_eeb9r4/var/lib/NetworkManager    288K   405G      288K  /mnt/var/lib/NetworkManager
rpool/ROOT/ubuntu_eeb9r4/var/lib/apt               170M   405G      170M  /mnt/var/lib/apt
rpool/ROOT/ubuntu_eeb9r4/var/lib/dpkg             76.2M   405G     76.2M  /mnt/var/lib/dpkg
rpool/ROOT/ubuntu_eeb9r4/var/log                  1.83M   405G     1.83M  /mnt/var/log
rpool/ROOT/ubuntu_eeb9r4/var/mail                  192K   405G      192K  /mnt/var/mail
rpool/ROOT/ubuntu_eeb9r4/var/snap                  192K   405G      192K  /mnt/var/snap
rpool/ROOT/ubuntu_eeb9r4/var/spool                 276K   405G      276K  /mnt/var/spool
rpool/ROOT/ubuntu_eeb9r4/var/www                   192K   405G      192K  /mnt/var/www
rpool/USERDATA                                    2.96M   405G      192K  /mnt
rpool/USERDATA/root_267fvj                        1.23M   405G     1.23M  /mnt/root
rpool/USERDATA/stump_267fvj                       1.54M   405G     1.54M  /mnt/home/stump
rpool/keystore                                     518M   406G     63.4M  -
root@mint:~# mount --make-private --rbind /dev  /mnt/dev
root@mint:~# mount --make-private --rbind /proc /mnt/proc
root@mint:~# mount --make-private --rbind /sys  /mnt/sys
root@mint:~# mount --make-private --rbind /run  /mnt/run
root@mint:~# cd /mnt
root@mint:/mnt# chroot /mnt /bin/bash --login
root@mint:/# mount -a


if something is off here, let me know and I'll try again.

---

### Post by MAFoElffen on 2023-12-02
That looks good... I didn't see anything that reached out ad grabbed me.

Can you see everything there?

---

### Post by MAFoElffen on 2023-12-03
Hello? Is your silence, because this is fixed? Or did life reset your priorities?

---

### Post by MAFoElffen on 2023-12-03
::crickets::

PM me if you need more help...

---

