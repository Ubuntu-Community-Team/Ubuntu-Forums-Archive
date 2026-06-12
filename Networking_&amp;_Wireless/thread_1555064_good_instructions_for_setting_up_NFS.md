---
title: "good instructions for setting up NFS?"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by princeofnam on 2010-08-17
i'm trying to mount my music files from one ubuntu PC to the other. practically every set of instructions i've googled are wildly different.  the one i trust most is [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) but even then i can't get it to work.  in particular, when i'm setting up the client  and type
--
# mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/export/users /home/users
--
i get


mount.nfs4: mount system call failed

---

### Post by princeofnam on 2010-08-17
ag

---

### Post by lukeiamyourfather on 2010-08-17
Firewall on one of the machines? Does it show up on the router client list? Manual network configuration or DHCP?

---

### Post by princeofnam on 2010-08-17
i don't have a firewall on either machines.

how do i check my router client list. 

and i'm pretty sure i'm DHCP
--

the following is my if config

sushi@Tyrork:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:9c:d8:77  
          inet6 addr: fe80::21b:24ff:fe9c:d877/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3821 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2931549 (2.9 MB)  TX bytes:883257 (883.2 KB)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92402 (92.4 KB)  TX bytes:92402 (92.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:ce:59:2f  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fece:592f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17830 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17070398 (17.0 MB)  TX bytes:2929470 (2.9 MB)

---

### Post by princeofnam on 2010-08-18
bump :(

---

### Post by imbjr on 2010-08-18
> **princeofnam said:**
> i'm trying to mount my music files from one ubuntu PC to the other. practically every set of instructions i've googled are wildly different.  the one i trust most is [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) but even then i can't get it to work.  in particular, when i'm setting up the client  and type
--
# mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/export/users /home/users
--
i get


mount.nfs4: mount system call failed

I can't help with your specific problem but I know you can trust the instructions you link to. I've used them on my server and have access to my files.

One thing: I mount my shares via fstab instead of the command line. I assume you are doing that for testing at the moment tho.

---

### Post by princeofnam on 2010-08-19
what's the difference between mounting on fstab vs the terminal, and how would one go about doing that?

---

### Post by drdos2006 on 2010-08-19
Here is a HOWTO I found extremely informative and useful.
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

Addendum:	On the Server machine
Needed to add Group of users on the machine designated as the server. Added the group via Webmin because that was what I was using. If that does not work then use terminal on the Server machine:
sudo addgroup MyGroupName
Added /media/sharedfiles on server with :	sudo mkdir /media/sharedfiles
Needed to change group permissions for /media//sharedfiles
sudo chgrp MyGroupName  /media/sharedfiles
//**
On the Client machine: Created a directory of /media/sharedfiles with : sudo mkdir /media/sharedfiles, mounted /media/sharedfiles from terminal as /media/sharedfiles with : 
sudo mount  <serverIPaddress>:/media/sharedfiles  /media/sharedfiles 
Can also be added to /etc/fstab for automatic mounting.
Copied files as test and it worked.
regards

---

### Post by imbjr on 2010-08-19
> **princeofnam said:**
> what's the difference between mounting on fstab vs the terminal, and how would one go about doing that?

The page you link to covers it, but basically, when you boot up and log in, the NFS share is ready to use - it's as if it's on your logged-in machine's HD. Of course, your server has to be running before you do that.

---

### Post by Jose Catre-Vandis on 2010-08-19
What are your OS versions? This chap had trouble when trying with Lucid on client and server, but sorted it out eventually.

[http://ubuntuforums.org/showthread.php?t=1489646](http://ubuntuforums.org/showthread.php?t=1489646)

Also any reason why you are using nfs4 as opposed to the default?

---

### Post by princeofnam on 2010-08-20
i sort of sorted it out. i just resorted to SSH

---

