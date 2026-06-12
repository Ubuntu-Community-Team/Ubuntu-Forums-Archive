---
title: "Network Sharing Issue"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by atmu5fear on 2009-01-30
OK, so I've just installed Xubuntu on my wifes eeePc. First I installed ubuntu, but it ran pretty slow most the time, so I figured I'd switch her to Xubuntu, which is, so far, faster. But now I've encountered an issue with file sharing. I have samba installed, and can access the eeePc's shared folders from other network computers (one XP, the other Beta Win7), but I cannot locate the shared folders on those Pc's from the eeePC. Because it is running on an 8GB SD card, it's easier for her to access her pictures and music off of our server (Windows 7). I could find these folders with Ubuntu, in the file manager, but not with Xubuntu's Thunar file manager. Am I looking in the wrong place. I know its connected to the network cuz like I said I can access it from other network computers. Any insight would be appreciated, thanks

---

### Post by RomanIvanov on 2009-01-30
===== MOUNTING WIN SHARED FOLDER=====

from Win to Ubuntu:
sudo mount -t smbfs -o username={YOUR USER NAME} //192.168.0.100/Temp /mnt/romanihome_share

from ubuntu to Win:
  [http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)
  do not forger to set Permisions for folder Properties Others=Read&Write
from linux to linux:
  sudo apt-get install nfs-common   (or open "Shared Folder" and check to install NFS)
  ([http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Linux_and_UNIX_Systems](http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Linux_and_UNIX_Systems))
[http://mybeni.rootzilla.de/mybeNi/2007/how_to_set_up_nfs_and_how_to_share_files_in_a_local_network_with_ubuntu_linux/](http://mybeni.rootzilla.de/mybeNi/2007/how_to_set_up_nfs_and_how_to_share_files_in_a_local_network_with_ubuntu_linux/)
  after each changes on source server do - sudo /etc/init.d/nfs-kernel-server restart
  on client do - sudo mount ubuntu2:/home/demo /home/demo/demo-folder
		sudo mount 192.168.0.101:/home/romani/Downloads /mnt/Downloads-Laptop

  for sharing for network I used "192.168.0.1/255.255.255.0"            my IPs was (xxx.100,xxx.101)


=== FIX FOR ERROR on shutdown with mounted folders - VFS server not responding
[http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/](http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/)
sudo ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
sudo ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

---

### Post by atmu5fear on 2009-01-30
whoa, whoa, whoa, thanks for a quick response, but thats far too complicated. first off you don't specify if that user name should be the one for ubuntu, or the one for windows, nor do you specify if that is just a generic ip, or a specific one. I just want my wife to be able to open file manager and see the network folders like she could with ubuntu, i don't want to get a phone call at work and try having to explain that whole terminal bit to her. i know for a fact you can access network folders on ubuntu without having to touch the terminal. i'll give it a go, but there's gotta be a simpler way.

---

### Post by atmu5fear on 2009-01-30
tried it and i get all this back, and still no access to network, anybody know about GUI access??

danielle@danielle-laptop:~$ sudo mount -t smbfs -o danielle//192.168.0.100/Temp /mnt/romanihome_share
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by rbc on 2009-01-30
As you have found out, and unless something has changed, Thunar does not have the capabilty to view network directories. There may be a better method, but I use Konqueror (Kubuntu's file manager) with my xubuntu computer to view network shares
sudo apt-get install konqueror
I will only use up about another 150MB

---

### Post by Denestria on 2009-01-30
Thunar does not have access to network shares unless they are mounted locally.  At boot I mount my Windows network shared directories and then I can use them in Thunar.

From my /etc/fstab
```

# network folders
//[COLOR="Red"]192.168.10.194[/COLOR][COLOR="RoyalBlue"]/Shared\040Media[/COLOR] [COLOR="Orange"]/media/warthog/shared[/COLOR] cifs credentials=/root.credentials,_netdev,rw,auto,uid=1000,users,noexec 0 0
//192.168.10.194/Public /media/warthog/public cifs credentials=/root.credentials,_netdev,rw,auto,users,uid=1000,noexec 0 0
//192.168.10.101/Shared /media/sulaco/shared cifs credentials=/root.credentials,_netdev,rw,auto,users,uid=1000,noexec 0 0
//192.168.10.101/Public /media/sulaco/public cifs credentials=/root.credentials,_netdev,rw,auto,users,uid=1000,noexec 0 0

```
[COLOR="Red"]The Windows machine IP[/COLOR][COLOR="RoyalBlue"]/Shared/Directory/Name[/COLOR] [COLOR="Orange"]/ubuntu/mount/point[/COLOR]
Once they are in fstab they can easily be unmounted/remounted with the mount devices plugin for the XFCE panel.

---

### Post by atmu5fear on 2009-01-30
> **rbc said:**
> As you have found out, and unless something has changed, Thunar does not have the capabilty to view network directories. There may be a better method, but I use Konqueror (Kubuntu's file manager) with my xubuntu computer to view network shares
sudo apt-get install konqueror
I will only use up about another 150MB
awesome, simple enough. thanks man

---

