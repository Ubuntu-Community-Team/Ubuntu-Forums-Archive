---
title: "Reach NFS-shared folder on ubuntu fron N900"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by FSMaximeH on 2012-10-14
Ladies and gents,
I am having trouble to reach a NFS-shared directory on my ubuntu netbook  from my N900
It say either nothing or the "the Device or Resource is busy" and I have noticed that the owner of the direcotry on the N900 change during mount operation. 
I can't resolve his even after googling a lot

So this is my configuration

**On the netbook side (ubuntu 12.04)**

install nfs and check that it starts
```

sudo apt-get install nfs-kernel-server nfs-common
/etc/init.d/nfs-kernel-server start

```I allow the ip of my n900
```

more /etc/hosts.allow
                        rpcbind mountd nfsd statd lockd rquotad : 192.168.0.23

```I check that nothing is denied
```

more /etc/hosts.deny
                        #empty

```I defined my exports
```

more/etc/exports
                        /home/max/ 192.168.0.0/255.255.255.0(rw)

```Reload the nfs server and check that the definition of my export workde well
```

sudo service nfs-kernel-server reload
showmount -e
Export list for netbook:
/home/max 192.168.0.0/255.255.255.0

```[B]
On the N900 side now[/B]
Install nfs client
```

root 
apt-get install nfs-common portmap

```Start the portmap demon
```

/etc/init.d/portmap start   
Starting portmap daemon...Already running..

```Create the directory where the shareshould be mounted
```

cd /home/user/MyDocs/
mkdir -p Netbook

```Check it is there
```

ls Net*
drwxrwxrwx    2 user     root        65536 Oct 14 15:08 Netbook

```Ping the netbook to ensure I can reach him
```

ping 192.168.0.16
PING 192.168.0.16 (192.168.0.16): 56 data bytes
64 bytes from 192.168.0.16: seq=0 ttl=64 time=4.731 ms

```And mount it
```

mount 192.168.0.16:/home/max /home/user/MyDocs/Netbook2
no output

```And ther is my problem
```

cd ./Netbook2/
-sh: cd: can't cd to ./Netbook2/

```Now look at the usernumber that owns the directory: it has changed. Is that the root of the problem?
```

ls Net*
drwx------   57 1000     1000         4096 Oct 14 16:09 Netbook

```[B]
Ubuntu side:[/B]
Linux netbook 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:32:50 UTC 2012 i686 i686 i386 GNU/Linux
Qt: 4.8.2
KDE: 4.9.2
Kontact: 4.9.2
Qt: 4.8.2
KDE: 4.9.2
Amarok: 2.5-GIT
[B]
N900 side[/B]
Linux Nokia-N900 2.6.28-omap1 #1 PREEMPT Fri Aug 6 11:50:00 EEST 2010 armv7l unknown

---

### Post by FSMaximeH on 2012-10-19
Up ?

---

### Post by LewisTM on 2012-10-20
A few things to mention about your setup.

1) The basic setup looks fine. It's nice that you did all those checkups and reported them. Thumbs up!

2) I'm confused about you mount point nomenclature. You create the 'Netbook' mount point on the N900 yet you try to mount the share and cd to 'Netbook2'. A typo?

3) When you mount something, the mount folder inherits the permissions of the mounted filesystem. So it's now owned by UID 1000 which corresponds to the Ubuntu primary user i.e. you. I don't know what your UID on the N900 (find out with [FONT="Courier New"]id[/FONT]) but chances are it's not 1000. Since only the owner (1000) is set to have access to the directory (from the permissions listed), you cannot enter it. You will have to grant 'others' access to your exported directory or play around with group permissions, if possible.

Alternatively, you can modify you export entry to grant everyone access as if they were user 1000
```
/home/max/ 192.168.0.0/255.255.255.0(rw,all_squash,anonuid=1000,anongid=1000)
```
Cheers!

---

### Post by FSMaximeH on 2012-10-20
EXACT !
yes it was a typo (I had trial several folder, so Netbook2 comes from anoter try)

this was indeed the problem of owner. I did not know about that it was the first time a set up an NFS

THANKS a LOT

so for those who would have the same problem:
what i have done
**ON THE DESKTOP SIDE**
```
sudo kate /etc/exports
```
change
```
/home/max/ 192.168.0.0/255.255.255.0(rw)
```
to 
```
/home/max/ 192.168.0.0 *(rw,all_squash,anonuid=1000,anongid=1000)
```
restart nfs-kernel server
```
sudo  /etc/init.d/nfs-kernel-server restart
```

**ON THE N900 SIDE **
Ensure that the nfs module is loaded inside the kernel( don't know why but this morning it was not inside)
```
modprobe -l nfs
```
if it says
```
/lib/modules/2.6.28-omap1/nfs.ko
```
it is okay, if not then
```
modprobe nfs
```
to load the nfs inside the kernel. On mine I had to do this one time for all apprently (it is still there even after reboot)


Then I mount the share to the folder (that is now /home/user/MyDocs/Netbook) like that
**mount -t nfs -o nolock,udp 192.168.0.16:/home/max /home/user/MyDocs/Netbook/**

[B]AND THERE IT WORKS WOOOOOOHHOOOO
[/B]

---

