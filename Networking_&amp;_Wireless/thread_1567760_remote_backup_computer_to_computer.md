---
title: "remote backup computer to computer"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by t_virus on 2010-09-04
hello guys,

can someone help me on how to bacupup a remote computer to my own computer?

i tried reading but i've found nothing i want.

the other pc is in the same wan.

any help?

thankx

---

### Post by melbert on 2010-09-04
I thinks we have a same problem..
my problem is i want to back up {remotely} 24 ubuntu user in our office. . in one computer. .

please help us. .how. .

---

### Post by BkkBonanza on 2010-09-04
If you have ssh server running on the remote then the simplest tool to use is rsync. 

rsync -vzptr user@server:/path/to/files /path/to/local/dest

See **man rsync**. 

If you don't have ssh available then you'll need to install it or figure out how else you will access the remote machine.

---

### Post by t_virus on 2010-09-04
> **BkkBonaza said:**
> If you have ssh server running on the remote then the simplest tool to use is rsync. 

rsync -vzptr user@server:/path/to/files /path/to/local/dest

See **man rsync**. 

If you don't have ssh available then you'll need to install it or figure out how else you will access the remote machine.
thankx BkkBonaza

how about HDD cloning? clonezilla?

---

### Post by BkkBonanza on 2010-09-04
I used clonezilla once (long ago) and it worked ok. It's not for remote backup though.
If you need to image a whole drive locally it is good. I think it would be very slow remotely though but it depends how much data there is and your link speed.

---

### Post by t_virus on 2010-09-04
ok...
than the best is to prsonaly clone the disk (in case of virus) and make remote backups once a day.
if i'm wrong, correct me, if not thanks for your help ;)

OR...

if i make full backups even better?

---

### Post by BkkBonanza on 2010-09-04
If you have a full backup that is accessible (not compressed) then using rsync to do a differential remotely would be pretty fast. It only scans the files at each end and transfers the changes, which usually is a very small amount. This would make remote backups to be less time consuming.

How far you take this depends on space and how important the data is. You might keep a weekly compressed "tar" archive of the full system, an uncompressed local image of the remote system, and daily rsync updates to the image.

This can all be automated with cron, a script and using ssh keys for access.

---

### Post by t_virus on 2010-09-04
is this the best way to correct human or viruses error of possible clients?

i'm thinking of adding this to my company (not so much knowlege of this metter)

---

### Post by BkkBonanza on 2010-09-04
It's a good way to have a backup so if a system is "broken" it can be recovered. 
There are problems though.

If you are primarily worried about systems being hacked then your problem is that you have to be sure the backup is from _before_ the hack and not _after_. Otherwise you just re-install the corrupt system. If you don't have system monitoring then it's often hard to know if a system was hacked and when.

On Linux systems viruses aren't currently a serious threat. The threat is more from poorly secured access controls and vulnerable services (daemons) and probably most of all from "social engineering" attacks, ie. poor user behaviour.

There is little need to backup entire systems. Re-installing the OS is fairly trivial anyway and after a system corruption you really have no choice but a fresh install.

Using rsync to backup users home directories is a good idea. This is where any transient important user data should be stored and is the data that cannot be easily recovered during a fresh install. It's not as likely to be corrupted by hackers in a way that compromises the system binaries.

You are better off keeping more copies of user home directories at multiple ages then wasting space storing OS files. You can store a "package inventory" of each system in the backup so that you know what packages need to be re-installed after a recovery. This can be generated automatically during backup by the dpkg program.

In summary I think I'd look at something like this:

A local shadow backup of users home directories updated daily with rsync, and a copy of each system's package list.

A three day old tar archive of each home.

A week old tar archive of each home, perhaps stored off site or at least on a second hard disk.

This gives you three recovery points and a small amount of redundancy to backup system failure.

But really, what you do depends on your needs and your company's needs. And I know very little about that so I'm just hand waving here.

---

### Post by Dustout on 2010-09-30
I would like to do the same thing with my home computers, does anyone know of a way to do this with a windows machine. I was thinking of running WHS in a virtual machine for backups

---

