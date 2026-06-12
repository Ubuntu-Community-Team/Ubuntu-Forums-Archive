---
title: "NFS permissions management has changed in Maverick 10.10 (2.6.35)"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by spade on 2010-10-25
I recently upgraded from Lucid to Maverick, and I noticed that a new error message caused by a "cp" command call, including the hard links option. Fortunately, I kept the last Lucid kernel (2.6.32-25), so I could check the different behavior with booting successively on each kernel.

Here are my configuration files:

On the server (192.168.1.2):
/etc/fstab :
UUID=... /mnt/Backup ext4 defaults,errors=remount-ro,relatime,async 0 2
/etc/exports :
/mnt/Backup/ 192.168.1.3(rw,async)
"msu" : main server user
msu id = 1000
<msu> belongs to the group "users"
users id = 100

On the client (192.168.1.3):
/etc/auto.nfs :
Backup -fstype=nfs,rw,intr,async 192.168.1.2:/mnt/Backup
"mcu" : main client user
mcu id = 1000
<mcu> belongs to the group "users"
users id = 100

from the server:
sudo chown -R <msu>:users /mnt/Backup
sudo chmod -R 770 /mnt/Backup

from the client:
mkdir /net/Backup/Folder2
If I check permissions of /net/Backup/Folder2 from the client, I get :
owner = nobody (Create and Delete files), users (Access files), others (Access files)

cp -alR /net/Backup/Folder1/* /net/Backup/Folder2
- under kernel 2.6.32-25: no problem
- under kernel 2.6.35-22: all the subdirectories are created, but all empty; moreover, I get as many messages as number of files from the source:
"cp: cannot create the link ...: operation not allowed"

I can copy manually any file to /net/Backup/Folder2 from the client.

Why the behavior has changed from kernel 2.6.32-25 to kernel 2.6.35-22 ?
Should I modify the permissions or the way the mount is exported with options like "(no_)root_squash", "all_squash", or "anonuid", "anongid" ?

Regards.

---

### Post by haihovu on 2010-11-13
Do you use IDMAPD to map the user IDs and group IDs between the clients and the server? If so check to see if idmapd is running. I find that with slow wireless network cards (or network cards with slow drivers such as the b43 driver for broadcom 43XX chipset) I had to restart idmapd after booting up for some as yet unexplained reason.

---

### Post by spade on 2010-11-26
update :
the last working kernel is 2.6.32-26
the problem is not fixed in 2.6.35-23.

Hi haihovu,

On both client and server, "idmapd" is unchecked in BUM and doesn't appear in system monitor.
but:
$ sudo service idmapd status
idmapd start/running, process 2936
So I run on both client and server :
$ sudo service idmapd restart
Then I run the "cp" command and the result is the same.
Moreover the network is not particularly slow.

Any other idea ?

---

### Post by haihovu on 2010-11-26
Actually restarting idmapd is not enough, I had to do this:
sudo service idmapd stop

wait for a second

sudo service idmapd start

Looks like there is a race condition of some sort. So I eventually put this into /etc/rc.local (which gets invoked after all the rcX.d stuff get run, including autofs):

stop idmapd
sleep 2
start idmapd

That seems to do the trick for me but is clearly a bug. I was going to try to debug it further but lost interest for now.

---

### Post by spade on 2010-11-27
OK I tried your thing and the result is exactly the same.
Any other idea ?

---

### Post by haihovu on 2010-11-27
I'm stumped as well, how  about   checking /etc/default/nfs-common on both the client and server sides to verify that this is set:

NEED_IDMAPD=yes

---

### Post by spade on 2010-11-28
Hi haihovu,

I checked on the server and the parameter is set to empty, so I shall do the modifications you recommend.
Sorry, it is a bit obscure to me, but you have a reason in mind to explain that this option has become necessary since the kernel update from 2.6.32 to 2.6.35 (or the update of another package from Lucid to Maverick) ?

Regards.

---

### Post by haihovu on 2010-11-28
No idea, perhaps the files get updated and over-written, the default is blank. 

Not even close to being an expert on Ubuntu or NFS I don't know if there is some underlying default that have changed in the version of NFS that caused the problem for you. I just started to use NIS, autofs, and NFS recently, after having already upgraded to Maverick so I don't have any comparison between the old behaviour and the new one.

Good luck,

---

### Post by spade on 2010-12-15
OK.
What is the best forum in which I should post ? How to report this problem to experts in kernel and NFS ?

Regards.

---

### Post by spade on 2011-01-20
Hello ?!

Nobody to help me with the very very very simple comand:
cp -alR /net/Backup/Folder1/* /net/Backup/Folder2

????

---

### Post by spade on 2011-02-03
Finally I found a workaround.
For some reason (see below "idmapd.conf") the server folder is now seen from the client as owned by nobody:users. So I did :
sudo chmod -R 770 /mnt/Backup/Folder1
and now the following command works fine:
cp -alR /net/Backup/Folder1/* /net/Backup/Folder2

The situation is not totally satisfying regarding security (I'd rather have 750 or 700 rights), but at least I can carry on working now. My overall feeling about NFS is not very good because the meaning of "right" is not very clear: either I can write files (regular ones) either I can't (hard links).

My actual config:
1/ server /etc/exports:
/mnt/Backup 192.168.1.3(rw,no_all_squash,no_subtree_check,async)
2/ server and client /etc/default/nfs-common:
NEED_IDMAPD=yes
3/ server and client /etc/idmapd.conf
Domain = <server_hostname>
4/ client /etc/auto.nfs:
Backup -fstype=nfs,rw,intr,async 192.168.1.2:/mnt/Backup

---

### Post by hansheijmans on 2011-03-27
Hi, I experienced  something similar using NFS version 3. Suddenly my files, as seen from the client, had "User # -2" as owner.
Now I "upgraded" to NFS4 and my problems are gone.

Check Ubuntu man pages for NFS4 how-to. A bit more complicated than NFS3, but it works.

---

