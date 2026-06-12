---
title: "I set up a server, now how do I access it?"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by dishbert on 2009-01-28
I loaded the 8.04 server edition on an old P2, and also installed ebox.  

I can login to ebox from a browser with [https://192.168.1.5/ebox](https://192.168.1.5/ebox), and just going to [http://192.168.1.5](http://192.168.1.5) brings up the cheery greeting:  "IT WORKS", but I don't seem to be able to find a how-to on getting into the server to install software and run apps.

I've looked at System - Admin - Network and Networking.  I've looked at Nautilus file browser, Connect to Server too, with no luck.

All I really need is to able to get on a terminal in the server from my PC on the same router.

---

### Post by icheyne on 2009-01-28
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by dishbert on 2009-01-28
Thanks icheyn, that's what I was looking for. 

Unfortunately, 

ssh localhost
ssh: connect to host localhost port 22: Connection refused

I changed the firewall (Firestarter) to allow access into port 22, and then shut it down, but still the same message.

---

### Post by dishbert on 2009-01-28
Got it, thanks again icheyn, it was looking for an IP address, I'm in now.

---

### Post by dishbert on 2009-01-28
There is a 2nd hard drive on the server box, so I installed gparted and set up an ext3 partion to use as storage on the local network.

I can mount it with:

chris@server1:~/new$ sudo mount -t ext3 /dev/sdb1 /home/chris/new

but there is only this in the directory:
chris@server1:~/new$ ls
lost+found

I must be missing some step here.

---

### Post by Iowan on 2009-01-28
On a new partition, that doesn't seem strange.  Try copying/moving/saving something there... Or make a new directory.

---

### Post by dishbert on 2009-01-28
That makes perfect sense Iowan.

chris@server1:~$ sudo mount -t ext3 /dev/sdb1 /home/chris/new
[sudo] password for chris: 
mount: /dev/sdb1 already mounted or /home/chris/new busy
mount: according to mtab, /dev/sdb1 is already mounted on /home/chris/new

I can't get into lost+found unless as root, but I successfully copied a file there.

root@server1:/home/chris/new/lost+found# ls
newcamd.conf

I can access it with 
chris@server1:~$ sudo nautilus --browser

And I can see by the properties that the size of the free space means it must be the partition I created.

So I just renamed the lost+found folder to "40G Drive" and I'm good to go?

---

### Post by Yashiro on 2009-01-28
No, that was a bad idea.

---

### Post by dishbert on 2009-01-28
Why?

---

### Post by Yashiro on 2009-01-29
lost+found is a system folder used for ext3 filesystem management.
Leave it alone and make new folders.

---

### Post by dishbert on 2009-01-29
Thanks for pointing that out Yashiro, I knew it wasn't elegent, I didn't realize it was harmful, and I didn't realize my mount command made the directory "new" the name of the newly partitioned drive, I thought it was 1 directory deeper than that.

I've redone the partition with gparted and I'll leave the lost+found alone.

---

### Post by Yashiro on 2009-01-29
Check this out if you want to configure your server using another PC on the network. [http://www.webmin.com/](http://www.webmin.com/)

---

