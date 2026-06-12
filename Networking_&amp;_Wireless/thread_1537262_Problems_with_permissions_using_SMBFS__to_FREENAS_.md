---
title: "Problems with permissions using SMBFS  to FREENAS box"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by grunge09 on 2010-07-23
Ok I am having a problem that is drying me crazy.  I am trying to do 1 way backups of my data to a freenas box.  

My PC:
AMD 6000+
3 GB RAM
500 GB HD SATA II
1 Gbps NIC (using 1Gbps switch)
Ubuntu 9.04

Freenas Box:
3.06 ghz cpu
2 gb ram
5u Rackmount Server using freenas 0.7 on flash drive to boot.
have two 1.5tb raid 5 arrays, only using one for now.  

Freenas Box has SMB enabled, and nautilus can see it in the network box and can access it when I type user/password.  but want to use RSYNC and it dos not like that.

So I installed SMBFS.

I ran:

mkdir /mnt/freenasbox

chown -R myusername:myusername /mnt/freenasbox

sudo mount -t smbfs \\\\192.168.0.150\\backup /mnt/freenasbox -o username=myusername,password=mypassword,uid=1000

No errors so far....

I can use nautilus browser to goto filesystem, mnt, freenasbox and can see all my data there.  

Now here is where I run into permissions when I try to run rsync (yea I know freenas has a rsync daemon but I can't get it to work)

So I run this: 

rsync -avzp  --progress --log-file=/home/myusername/rlog/$(date +%Y%m%d)_rsync.log /home/myusername /mnt/freenasbox/backup

And it runs really fast and spits out a lot of permissions denied and when I check /mnt/freenasbox it only makes the directories and copies nothing.

*NOTE* last night I successfully ran rysnc to a 1tb external esata drive so I know rsync is doing its thing.  

I tried :

ubount -r /mnt/freenasbox 

sudo mount -t smbfs \\\\192.168.0.150\\backup /mnt/freenasbox -o username=myusername,password=mypassword,uid=myusername

And re-ran rysnc command.  Now some files get copied and others still give permission denied.  

So I checked permissions and got:

ls -l /mnt
total 4
drwxr-xr-x 2 myusername myusername 4096 2010-07-23 09:26 freenasbox

what am I doing wrong?

---

### Post by grunge09 on 2010-07-25
Bump?

---

