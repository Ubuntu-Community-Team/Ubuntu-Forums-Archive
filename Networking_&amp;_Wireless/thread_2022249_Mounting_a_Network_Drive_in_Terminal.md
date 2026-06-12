---
title: "Mounting a Network Drive in Terminal"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by akkarris on 2012-07-10
How would I mount and access a network drive through the terminal?
any tips would be helpful
Thanks!

---

### Post by Kirk Schnable on 2012-07-10
What sort of network drive are you attempting to mount?  NFS, SSHFS, Samba, etc?  

Do you want to automatically mount the volume at boot time, or are you attempting to do a one-time mount from the terminal?

Kirk

---

### Post by akkarris on 2012-07-10
The network drive I want to map to is smb, and I want to write a shell script to mount this drive.

---

### Post by papibe on 2012-07-10
Hi akkarris.

First thing you need to do is to install a library:
```
sudo apt-get install cifs-utils
```
Then create a mount point:
```
mkdir  ~/mnt
```
Finally to actually mount the share
```
sudo mount -t cifs  //servername/sharename  ~/mnt/
```
Replace 'servername' and 'sharename' for the actual names of the server and the share respectively.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by akkarris on 2012-07-10
Hi Papibe, 
thanks for the help however when I try to install cifs-utils it gives me an error
Code:
> sudo apt-get install cifs-utils
E: couldnt find package cifs-utils

so i assumed that i have it already, and when i tried to mount to the network drive
code:
>  :~$ sudo mount -t cifs //BOONENAS/demoshare ~/mnt/
mount error: could not resolve address for BOONENAS: No address associated with hostname
no ip address specified and hostname not found
yet when I go into my network folder under places it shows BOONENAS server...am i getting my syntax wrong maybe?

---

### Post by papibe on 2012-07-10
It looks like you are on 10.04.

The package name changed on newer versions. This should work on previous versions:
```
sudo apt-get install smbfs
```
Tell us how it goes.
Regards.

---

### Post by akkarris on 2012-07-10
I already had that library it seems so that issue is done however i'm still having the mounting issue :(

---

### Post by papibe on 2012-07-10
It looks like either a name resolution problem, or a incorrect sharename.

Try using the server's IP address.

If that don't work, could you post the result of this command?
```
sudo smbtree
```
(press enter when for root password)

Tell us how it goes.
Regards.

---

### Post by akkarris on 2012-07-12
I tried the ip address for the server and it still didnt work. here is my syntax
sudo mount -t cifs //BOONENAS/ipaddress ~/mnt/
i get this error, 
> mount error: could not resolve address for BOONENAS no address associated with hostname no ip address specified and hostname not found. here is what the sudo smbtree showed. 
> WORKGROUP
//BOONENAS 
          //BOONENAS/commshare
          //BOONENAS/demoshare
          //BOONENAS/IPC$

---

### Post by bab1 on 2012-07-12
> **akkarris said:**
> I tried the ip address for the server and it still didnt work. here is my syntax
sudo mount -t cifs //BOONENAS/ipaddress ~/mnt/
i get this error, 
...

This should be ```
sudo mount -t cifs //IPADDRESS/demoshare ~/mnt/
```

The SMB resource is always //COMPUTERNAME/share_name or //IPADDRESS/share_name.

[COLOR="Blue"]You have some name resolution problem if you can't use BOONENAS from the CLI.[/COLOR]

---

### Post by akkarris on 2012-07-12
Thank you for all the help, its kinda working now. The command does not give me any errors except a list of commands for mount. Here is what im typing in.

> sudo mount -t cifs //Ipaddress/demoshare ~/mnt/ -o username=xxxx, password=xxxxxxx, domain=xxxxit is not mounting the image and 

it is giving me a list of commands to use with mount.

> Usage: mount -V                 : print version
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
all of this is quite frustrating....

---

### Post by papibe on 2012-07-12
There should be no spaces between the list of options:
```
-o username=xxxx,password=xxxxxxx,domain=xxxx 
```
Tell us how it goes.
Regards.

---

### Post by The Linuxist on 2012-07-13
You can always test name resolution with:

```
nmblookup BOONEAS
```

which should say something like:


```
querying BOONEAS on x.x.x.x
querying BOONEAS on x.x.x.x
x.x.x.x BOONEAS <00>
```

---

### Post by akkarris on 2012-07-17
It worked. Thanks everyone for your help!

---

### Post by papibe on 2012-07-17
Great! :)

Please mark the thread solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")) when you have the chance.

Regards.

---

