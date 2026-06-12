---
title: "Adding Freenas to Ubuntu"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by jetinder on 2009-06-17
A few days ago built a freenas server, on Freenas's webgui added permission so any linux machine (on my network) can access it.

On my Ubuntu PC when i type in the freenas IP address firefox can see it and i can control the server from firefox.

But how can add or delete files from freenas via my Ubuntu desktop ?

How can i add freenas to my network on Ubuntu ?

---

### Post by Iowan on 2009-06-18
What filesystem have you set up on FreeNAS, NFS, SMB, etc?  It's been awhile since I tried FreeNAS - perhaps their options have changed.

---

### Post by jetinder on 2009-06-19
Hi Iowan

On Freenas disks are formatted in UFS.

But in the services tab NFS has been used so any Linux server can "see it".

However on Ubuntu i can't add freenas to it, i can't load or save files to it.


************ Its now 2.49am - 20 June 2009 UK time **********

Just found the following webpage 
:-

[https://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=49&t=2664&p=12836#p12836]("https://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=49&t=2664&p=12836#p12836")

That has the fixed the problem and ubuntu can "see" freenas.

---

### Post by jetinder on 2009-06-21
The above link needs a user-id and password for that forum  but below is what was said on there 
:-

showmount -e (Ip address of Freenas server)<CR>

Ubuntu gave the following reply.
:-

Export list for (Ip address of Freenas server)

/mnt/Disk1/ (Ip address of Freenas server)

= 1 hard drive Ubuntu can access on FreeNAS.

To mount drive on Ubuntu (login as root and goto / directory).
            
Type 
:-

mkdir /mnt/FreeNAS1 <CR>

sudo mount -t nfs   192.168.1.250:/mnt/NAS1 /mnt/FreeNAS1 -o rsize=65536,wsize=65536,timeo=14,intr,nolock,soft,udp ls /mnt/FreeNAS1 <CR>

That will work.

---

