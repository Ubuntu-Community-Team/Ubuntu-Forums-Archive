---
title: "HOW-TO mount NFS on WiFi Laptop on Jaunty"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by neorg on 2009-06-26
Here a small HOW-TO automatically mount a nfs (Network File System) on a Jaunty WiFi connection.

Why this HOW-TO.
---------------------------------------------------------
I was struggling with the nfs mount on a laptop. I red all post over jaunty nfs mount but non give me the solution.   

On Hardy and on Jaunty you can't mount nfs before the network connection is up and running. Unfortunately the network connection comes up after the user login on the desktop. If the desktop is visible it take 10 to 20 seconds before the NetworkManager is ready to serve the connection.

As far as I know all (auto)mount instructions are past now.


HOW-TO mount NFS on an Jounty WiFi connection (laptop)
----------------------------------------------------------
1. install nfs-common on the laptop
```
sudo apt-get install nfs-common
```

2. Create a mount point somewhere on the system. Let's suppose you want a nfs mount on /media/TEST . Create a dir named TEST
```
mkdir /media/TEST
```

3. Create mount in /etc/fstab. Using youf favorite editor ant open de file /etc/fstab (you have to be root to edit this file)

```
REMOTE_HOST:/DIR_ON_REMOTE_HOST /media/TEST nfs rsize=8192,wsize=8192,timeo=14,intr                 0       0

```

On a system without wifi this is all you need to do. Maybe you need to add mount -a to the tile /etc/rc.local This when the network is.n up before the system wants to mount the nfs disk.

But....on a laptop with WiFi this ain't gonna work. On al laptop the network connection comes up after the gdm login. That's much to late for the mount. I solved this with a script that starts at boot.

4. Copy, edit and save the script under here to /home/USER/bin/mount.REMOTE_HOST.sh where USER is your system username.

NOTE:
-replace REMOTE_HOST with the name of your remote host
-replace /media/TEST with the name of your local dir (see #2)

```

#!/bin/bash

# This script mount the partitions on machine
# REMOTE_HOST. Because of the fact that in Intrepid
# the network manager start so late that it's  
# to late for the mount.


# Number of times we are goning to try is we can ping the host.
COUNTER=50

# A loop
while [ $COUNTER -gt  0 ]
do
 # Ping the remote host (REMOTE_HOST in this case)	
 ping -c 5 REMOTE_HOST

 # See is we got a "0" as result from the ping command.
 if [ $? != 0 ]; then
	 # If it is 0 than it's not OK. 
	date '+%Y-%m-%d %H:%M:%S Connection Unavailable'
 else
	# If we got something other than 0 than the host is reachable
	# let's mount the thinks we want

	mount /media/TEST

	# set counter to zero to quit the while loop	
	let COUNTER=0
	#date '+%Y-%m-%d %H:%M:%S Connection Available' 
 fi

 # Subtract one from the counter so the number
 # of times the while loop has to go is one less
 let COUNTER=COUNTER-1
 sleep 10


done 
 

```

5. Create a cron entry in crontab

```
sudo -s crontab -e
```
  
add in crontab:

Note: replace USER with your system user.
```
@reboot sh /home/USER/bin/mount.robox.sh;
```

save the contab file.


-------------------------------
Now on the remote machine:
-------------------------------

6. install nfs packages

```
sudo apt-get install nfs-kernel-server nfs-common
```


7. Edit the file /etc/exports. Add al line like this. Where you have to replace "PATH/TO/EXPORT/DIR" with the path to your export directory. (sa. /home/rob/shared_files or someting like that) 
```
/PATH/TO/EXPORT/DIR 192.168.1.1/24(rw,root_squash,sync,no_subtree_check)
```

EDIT
7(a). Export the filesystem
```

exportfs

```

8. Restart the nfs-kernel deamon
```
sudo /etc/init.d/nfs-kernel-server
```

-------------------------------
Now on the laptop machine:
-------------------------------

9. Reboot the laptop.


10 You should now have the nfs mounted automaticaly. Take al look in /media/TEST where you should see the remote files.

The remote disk sould also be visible in nautilus. (places)


Ready!!

---------------------------------------------------------
.

Problem? Don't hesitate to contact me for help.

---

### Post by jjlido on 2009-06-29
hi,
i followed all your instruction, but when I try to mount the nfs share I got the following error:
mount.nfs: Protocol not supported

I am working with linux4one based on ubuntu 8.04.
I checked all the packages and seems I have everything installed as you write.
Any suggestions?
thanks 
Ivan

---

### Post by neorg on 2009-06-29
jjlido: Sorry I forgot one command on the server. I added it in item 7(a). ```
 exportfs
```

Can you please post the output from the remote server command:
```

showmount -e

```
There should be something like:
```

/home/USERNAME       192.168.1.1/24
/home/USERNAME/Pictures
                *home.local
/extra/musiclib
                *home.local

```

---

