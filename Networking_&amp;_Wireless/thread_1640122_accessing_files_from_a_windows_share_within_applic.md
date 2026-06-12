---
title: "accessing files from a windows share within applications"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by boarder428 on 2010-12-07
I cannot access figure out how to access files stored on a windows share within an application.  I can access files on a windows share from places>network but if I am trying to access files from say audacitcy or gtkpod by means of file>open when the application brings up the "places" dialog there is no network Icon to choose from.

---

### Post by SlugSlug on 2010-12-07
you will want to mount it to a local point with smbfs 

[http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html)

---

### Post by boarder428 on 2010-12-07
Thanks for the link SlugSlug but I'm still not having any success.  I an using Ubuntu 10.10 distros and trying to mount my Windows home server which I beleive is running Windows Home Server 2003. I would also like this to automatically mount everytime I boot up. I tried the following: ```
Procedure to mount remote windows partition (NAS share)

1) Make sure you have following information:
==> Windows username and password to access share name
==> Sharename (such as //server/share) or IP address
==> root level access on Linux

2)[COLOR="Red"] Login to Linux as a root user (or use su command)[/COLOR]
 [COLOR="YellowGreen"]I used sudo[/COLOR]
[COLOR="Red"]3) Create the required mount point:[/COLOR]
# mkdir -p /mnt/BENDERSERVER1
4) [COLOR="Red"]Use the mount command as follows:[/COLOR]
# mount -t cifs //BENDERSERVER1 -o username=myUsername,password=myPassword /mnt/BENDERSERVER1

Use following command if you are using Old version such as RHEL <=4 or Debian <= 3:
# mount -t smbfs -o username=vivek,password=D1W4x9sw //ntserver/download /mnt/ntserver [COLOR="YellowGreen"](I did not do this as I figured I did not need to using Ubuntu 10.10?)[/COLOR]

5) Access Windows 2003/2000/NT share using cd and ls command:
# cd /mnt/ntserver; ls -l
[COLOR="YellowGreen"]I got the following...
corey@corey:~$ sudo cd /mnt/BENDERSERVER1; ls -l
sudo: cd: command not found
total 44
drwxr-xr-x 3 corey corey 4096 2010-11-29 18:15 audio-projects
drwxr-xr-x 8 corey corey 4096 2010-12-04 23:13 Corey
drwxr-xr-x 2 corey corey 4096 2010-11-29 18:21 Desktop
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Documents
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Downloads
drwxr-xr-x 2 corey corey 4096 2010-12-07 10:42 Incoming
drwxr-xr-x 2 corey corey 4096 2010-12-07 10:42 Music
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Pictures
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Public
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Templates
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Videos[/COLOR]

```

---

### Post by SlugSlug on 2010-12-08
```
drwxr-xr-x 3 corey corey 4096 2010-11-29 18:15 audio-projects
drwxr-xr-x 8 corey corey 4096 2010-12-04 23:13 Corey
drwxr-xr-x 2 corey corey 4096 2010-11-29 18:21 Desktop
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Documents
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Downloads
drwxr-xr-x 2 corey corey 4096 2010-12-07 10:42 Incoming
drwxr-xr-x 2 corey corey 4096 2010-12-07 10:42 Music
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Pictures
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Public
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Templates
drwxr-xr-x 2 corey corey 4096 2010-12-02 19:51 Videos
```

are they the files on the windows server?

the error you had was 'sudo cd'  you cnt use sudo before cd..

---

### Post by boarder428 on 2010-12-08
> **SlugSlug said:**
> 
are they the files on the windows server?

no those files are local on my Ubuntu PC!

---

### Post by SlugSlug on 2010-12-09
Hang about - just read what acctually hapened..
[COLOR=YellowGreen]sudo cd /mnt/BENDERSERVER1;

did not cd to the mount point (humm my text has gone green :( ) repeat all steps but when you get to
[/COLOR]5) Access Windows 2003/2000/NT share using cd and ls command:
# cd /mnt/ntserver; ls -l
[COLOR=YellowGreen]I got the following...


_##issue_ 
[/COLOR][COLOR=YellowGreen]cd /mnt/BENDERSERVER1; ls -l   ## (without the sudo)
[/COLOR]
[COLOR=YellowGreen]
[/COLOR]
[COLOR=YellowGreen]

[/COLOR]

---

### Post by boarder428 on 2010-12-10
started over, got the following...

```
corey-HP-Pavilion-dv7-Notebook-PC ~ # mkdir -p /mnt/BENDERSERVER1
corey-HP-Pavilion-dv7-Notebook-PC ~ # mount -t cifs //BENDERSERVER1 -o username=corey,password=***** /mnt/BENDERSERVER1
mount error: could not resolve address for BENDERSERVER1: No address associated with hostname

```

Not exactly sure what this means but I assume it cannot find the server.  Here is what I don't understand, when Rhythm box is open it can find my server, it shows it as HP MediaSmart Server. the path it shows is daap://192.168.0.187:9999/databases/1/items?session-id=21

When I use the "places" menu the path is Places>Network>Windows Network>BENDERSERVER1

so my question, Is it a naming issue? or an ip addressing issue.  Do I need to set a static ip on the server?

I tried changing the server name to HP MediaSmart Server and got the following...
```
corey-HP-Pavilion-dv7-Notebook-PC ~ # mkdir -p /mnt/HP MediaSmart Server
corey-HP-Pavilion-dv7-Notebook-PC ~ # mount -cifs //HP MediaSmart Server -o username=Administrator,password=DUKE_thedog /mnt/HP MediaSmart Server
mount: invalid option -- 'c'
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
corey-HP-Pavilion-dv7-Notebook-PC ~ # mkdir -p /mnt/ntserver
corey-HP-Pavilion-dv7-Notebook-PC ~ # mount -t ciffs //ntserver -o username=corey,password=CJB_428 /mnt/ntserver
mount: unknown filesystem type 'ciffs'
corey-HP-Pavilion-dv7-Notebook-PC ~ # mount -t cifs //ntserver -o username=corey,password=CJB_428 /mnt/ntserver
mount error: could not resolve address for ntserver: No address associated with hostname
corey-HP-Pavilion-dv7-Notebook-PC ~ # mkdir -p /mnt/192.168.0.187
corey-HP-Pavilion-dv7-Notebook-PC ~ # mount -t cifs //192.168.0.187 -o username=corey,password=CJB_428 /mnt/ntserver
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

---

### Post by boarder428 on 2010-12-26
ok, got it figured out, here's a link to the forum that helped me get it done.  Thanks magic30  [http://www.mediasmartserver.net/forums/viewtopic.php?f=5&t=9699&p=76635#p76635]("http://www.mediasmartserver.net/forums/viewtopic.php?f=5&t=9699&p=76635#p76635")

---

