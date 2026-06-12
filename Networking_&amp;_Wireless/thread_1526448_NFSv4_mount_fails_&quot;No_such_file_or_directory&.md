---
title: "NFSv4 mount fails: &quot;No such file or directory&quot;"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by bytbox on 2010-07-08
NFSv4, ubuntu 10.04 (both machines), no firewall. Server is 'ogodei', client is 'tolui'.

ogodei:/etc/exports:
```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

/var/lib/sysnews 10.4.49.0/24(ro,sync,insecure,no_subtree_check)
```I've tried several other variants, mounting other directories, the entire filesystem, removing insecure, removing sync, subtree_check - all yields:

Attempting mounting gives:

```
root@tolui:/var/lib# mount.nfs4 ogodei:/var/lib/sysnews sysnews/ -vr
mount.nfs4: timeout set for Thu Jul  8 02:50:06 2010
mount.nfs4: text-based options: 'clientaddr=10.4.49.193,addr=10.4.49.194'
mount.nfs4: mount(2): No such file or directory
mount.nfs4: mounting ogodei:/var/lib/sysnews failed, reason given by server:
  No such file or directory

```Same sort of thing if I try to mount ogodei:/ (with the relevant line added to /etc/exports).  Now I assure you - the root directory exists.

So... what did I miss? (And thanks in advance.)

---

### Post by bytbox on 2010-07-08
Bump? Or should I try again elsewhere...

---

### Post by trojanfoe on 2010-09-11
I have the same problem - did you find an answer?

-A

---

### Post by Metabaron on 2010-10-18
NFSv4 uses the option fsid=0 to state where to root all exports on the server. Please read /usr/share/doc/nfs-common/README.Debian.nfsv4.

---

### Post by kat_ams on 2011-07-07
Here is how I did it for my Synology Disk Station:

So this one turned out to be really easy to solve. Apparently Synology does secretly support NFS4.
Just not out of the box.

Warning this instruction is for power-users and expert users only. If you are not comfortable using the command line or vi then please just stick to the regular options on your diskstation.

Logon to the diskstation as root
```
ssh root@ds
<type in your root(admin) password when prompted>

```
backup the file /etc/exports
```
cp /etc/exports /etc/exports.orig
```
open the /etc/exports file in vi
```
vi /etc/exports
```
create a second blank line at the top and copy the first entry upwards
open a newline```
o
```
command mode ```
[esc]
```
```
[down arrow]
```
visual selection ```
v
```
[right arrow] until the entire line is selected
copy (yank) ```
y
```
[up arrow] to the blank line above
paste ```
p
```
append ```
a 
```
then modify the line so it looks like the code line below and contains "fsid=0" after the rw, and is all on one line. There is a [tab] between /volume1 and the ip address
In reality you are just telling nfs who the root of the shares is as NFS4 will automount all the shares under this root.
```
/volume1             192.168.1.0/24(rw,fsid=0,async,no_wdelay,no_root_squash,insecure_locks,anonuid=0,anongid=0) 
```
save the file and exit vi
```
[esc]:wq
```

Now reboot the NAS

On Ubuntu you need to change the following:

in /etc/default/nfs-common
```
sudo vim /etc/default/nfs-common
```

append yes to the end of the string NEED_IDMAPD=
```
[esc]
/NEED_IDMAPD
[enter]
[right arrow] 
``` stand on the = with your cursor and press
```
a
```
type
```
yes
```
then save the file
```
[esc]:wq
```

make a copy of your fstab (file system table)
```
sudo cp /etc/fstab /etc/fstab.orig
```
then edit your fstab to mount your nas
```
vim /etc/fstab
[shift]G
o
```
paste the following replacing the IP address with your NAS ip address
```
192.168.1.26:/  /media  nfs4    rw      0       0
```
save the file
```
[esc]:wq
```

Now test to make sure your fstab works.
```
sudo mount -a
```

[b]WARNING: IF YOU GET ANY ERROR AFTER TYPING THE sudo mount -a COMMAND STOP!
FIX YOUR FSTAB BEFORE CONTINUING OR RESTORE THE BACKUP FSTAB. NOT DOING SO WILL RENDER YOUR COMPUTER UNBOOTABLE! A LIVE USB-STICK CAN BE USED TO RECOVER THE FSTAB IF ALL GOES AWRY.[/b]

open your file browser (such as nautilus)
browse to:
File System
media

you should see all of your shares now under the media folder
they will have all permissions so this method is somewhat less secure than the NFS3 method. But much less hassel with user ID's and permissions.

The other thing you will notice is you don't have any seperate drives on your desktop anymore. The NAS is now integrated in your Ubuntu system.

 :D Enjoy

---

