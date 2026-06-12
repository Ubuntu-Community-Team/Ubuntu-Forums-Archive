---
title: "Simple NFS setup?"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2011-02-17
Hey guys, I need a simple tutorial on how to setup an NFS server.  I have a client PC that needs a CRAP TON of space for the /home/ben file and I need it to be able to get that from the server.  Right now, I have a server with 1TB raid and a client.  Both have Ubuntu.

How do I do this?


Thanks.

---

### Post by inobe on 2011-02-17
right click the folder and hit sharing options, share the folder of of choice, you should receive a dialog telling you services need to be installed, there should be a drop down menu with choices, one is samba and the other is nfs, i think you can choose both or just one.

or just watch the video [http://vimeo.com/688987](http://vimeo.com/688987)

---

### Post by oldfred on 2011-02-17
I gave up using Samba as I found NFS a lot easier once I understood what I had to do.

HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I copy several folders/partitions with data from my Desktop computer to my laptop when traveling & then copy back when returning. I end up with "server" installed on both.

My mounts & folders are the same on both machines:
/mnt/data so I add a LT or DT to the remote to keep track.

My folders are mounted and then I add them to /etc/exports
Editing /etc/exports
the /etc/exports file is used for creating a share on the NFS server

invoke your favorite text editor or
sudo nano /etc/exports
gksudo gedit /etc/exports

/mnt/data 192.168.1.0/24(rw,no_root_squash,async)
/mnt/shared    192.168.1.0/24(rw,no_root_squash,async)

Install NFS client support on my laptop (but I also install server)
sudo apt-get install portmap nfs-common

This was my install on the server:
  356  sudo apt-get install nfs-kernel-server nfs-common portmap
  357  sudo dpkg-reconfigure portmap
  358  #sudo /etc/init.d/portmap restart obsolete see next 
  359  service portmap restart
  360  ifconfig
  361  sudo exportfs -a

on my portable :
sudo apt-get install portmap nfs-common

   15  service portmap restart
   16  sudo service nfs-common restart
   17  sudo /etc/init.d/nfs-common restart
   18  service portmap status
   19  service nfs-common status
   43  sudo bash Mount_DT_NFS.sh 
   44  sudo bash sync_from_DT.sh 



I have two files for each computer one with DT and one LT:
```
#!/bin/bash
# check that exports has been updated and path is correct
#/etc/exports
#/mnt/data 192.168.1.0/24(rw,no_root_squash,async)
#mnt/shared   192.168.1.0/24(rw,no_root_squash,async)

sudo mkdir /mnt/data_DT
sudo mkdir /mnt/shared_DT
sudo mount 192.168.1.20:/mnt/data /mnt/data_DT
sudo mount 192.168.1.20:/mnt/shared /mnt/shared_DT

``````
#!/bin/bash
# run Mount_NFS.sh first
rsync -aruvP /mnt/data_DT/Documents /mnt/data
rsync -aruvP /mnt/data_DT/Projects /mnt/data
rsync -aruvP /mnt/data_DT/PDF /mnt/data
rsync -aruvP /mnt/data_DT/kmymoney /mnt/data
#
rsync -aruvP /mnt/shared_DT/OfficeFiles /mnt/shared
rsync -aruvP /mnt/shared_DT/mozilla /mnt/shared
rsync -aruvP /mnt/shared_DT/Photos/All2010 /mnt/shared/Photos


```I tested each rsync with smaller samples to make sure i was copying the correct data.

---

### Post by inobe on 2011-02-17
> **oldfred said:**
> I gave up using Samba as I found NFS a lot easier once I understood what I had to do.

HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I copy several folders/partitions with data from my Desktop computer to my laptop when traveling & then copy back when returning. I end up with "server" installed on both.

My mounts & folders are the same on both machines:
/mnt/data so I add a LT or DT to the remote to keep track.

My folders are mounted and then I add them to /etc/exports
Editing /etc/exports
the /etc/exports file is used for creating a share on the NFS server

invoke your favorite text editor or
sudo nano /etc/exports
gksudo gedit /etc/exports

/mnt/data 192.168.1.0/24(rw,no_root_squash,async)
/mnt/shared    192.168.1.0/24(rw,no_root_squash,async)

Install NFS client support on my laptop (but I also install server)
sudo apt-get install portmap nfs-common

This was my install on the server:
  356  sudo apt-get install nfs-kernel-server nfs-common portmap
  357  sudo dpkg-reconfigure portmap
  358  #sudo /etc/init.d/portmap restart obsolete see next 
  359  service portmap restart
  360  ifconfig
  361  sudo exportfs -a

on my portable :
sudo apt-get install portmap nfs-common

   15  service portmap restart
   16  sudo service nfs-common restart
   17  sudo /etc/init.d/nfs-common restart
   18  service portmap status
   19  service nfs-common status
   43  sudo bash Mount_DT_NFS.sh 
   44  sudo bash sync_from_DT.sh 



I have two files for each computer one with DT and one LT:
```
#!/bin/bash
# check that exports has been updated and path is correct
#/etc/exports
#/mnt/data 192.168.1.0/24(rw,no_root_squash,async)
#mnt/shared   192.168.1.0/24(rw,no_root_squash,async)

sudo mkdir /mnt/data_DT
sudo mkdir /mnt/shared_DT
sudo mount 192.168.1.20:/mnt/data /mnt/data_DT
sudo mount 192.168.1.20:/mnt/shared /mnt/shared_DT

``````
#!/bin/bash
# run Mount_NFS.sh first
rsync -aruvP /mnt/data_DT/Documents /mnt/data
rsync -aruvP /mnt/data_DT/Projects /mnt/data
rsync -aruvP /mnt/data_DT/PDF /mnt/data
rsync -aruvP /mnt/data_DT/kmymoney /mnt/data
#
rsync -aruvP /mnt/shared_DT/OfficeFiles /mnt/shared
rsync -aruvP /mnt/shared_DT/mozilla /mnt/shared
rsync -aruvP /mnt/shared_DT/Photos/All2010 /mnt/shared/Photos


```I tested each rsync with smaller samples to make sure i was copying the correct data.


hey where's the pictures? :tongue:

---

### Post by aeiah on 2011-02-18
> **oldfred said:**
> I gave up using Samba as I found NFS a lot easier once I understood what I had to do.

HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I copy several folders/partitions with data from my Desktop computer to my laptop when traveling & then copy back when returning. I end up with "server" installed on both.

My mounts & folders are the same on both machines:
/mnt/data so I add a LT or DT to the remote to keep track.

My folders are mounted and then I add them to /etc/exports
Editing /etc/exports
the /etc/exports file is used for creating a share on the NFS server

invoke your favorite text editor or
sudo nano /etc/exports
gksudo gedit /etc/exports

/mnt/data 192.168.1.0/24(rw,no_root_squash,async)
/mnt/shared    192.168.1.0/24(rw,no_root_squash,async)

Install NFS client support on my laptop (but I also install server)
sudo apt-get install portmap nfs-common

This was my install on the server:
  356  sudo apt-get install nfs-kernel-server nfs-common portmap
  357  sudo dpkg-reconfigure portmap
  358  #sudo /etc/init.d/portmap restart obsolete see next 
  359  service portmap restart
  360  ifconfig
  361  sudo exportfs -a

on my portable :
sudo apt-get install portmap nfs-common

   15  service portmap restart
   16  sudo service nfs-common restart
   17  sudo /etc/init.d/nfs-common restart
   18  service portmap status
   19  service nfs-common status
   43  sudo bash Mount_DT_NFS.sh 
   44  sudo bash sync_from_DT.sh 



I have two files for each computer one with DT and one LT:
```
#!/bin/bash
# check that exports has been updated and path is correct
#/etc/exports
#/mnt/data 192.168.1.0/24(rw,no_root_squash,async)
#mnt/shared   192.168.1.0/24(rw,no_root_squash,async)

sudo mkdir /mnt/data_DT
sudo mkdir /mnt/shared_DT
sudo mount 192.168.1.20:/mnt/data /mnt/data_DT
sudo mount 192.168.1.20:/mnt/shared /mnt/shared_DT

``````
#!/bin/bash
# run Mount_NFS.sh first
rsync -aruvP /mnt/data_DT/Documents /mnt/data
rsync -aruvP /mnt/data_DT/Projects /mnt/data
rsync -aruvP /mnt/data_DT/PDF /mnt/data
rsync -aruvP /mnt/data_DT/kmymoney /mnt/data
#
rsync -aruvP /mnt/shared_DT/OfficeFiles /mnt/shared
rsync -aruvP /mnt/shared_DT/mozilla /mnt/shared
rsync -aruvP /mnt/shared_DT/Photos/All2010 /mnt/shared/Photos


```I tested each rsync with smaller samples to make sure i was copying the correct data.


if all you're doing is rsync, why didnt you just use rsync over ssh?


but yes, i got our nfs up and running using the ubuntu wiki, as mentioned higher up. if you have issues with it trying to mount before the nic is up then you'll have to let the command sleep for a few seconds first. i did this within /etc/rc.local

---

### Post by oldfred on 2011-02-18
aeiah, good question. 

Once I got NFS working, I stopped looking for other solutions. I was coming from Samba with frustrations with Samba and NFS worked really well. All I had to do was run two scripts. Everything else for setup I have in my new system install scripts.

I have in my notes how to do SSH & that will be a test, real soon now.

---

### Post by pepsifx357 on 2011-02-18
It'l be all command line, no GUI.  I'm a brave soul.


Also as a side note, I posted a question on another forum for audio recording and I'd like for you guys to weigh in on it.  This is why I am doing the NFS.  I may have misrepresented the question by saying NAS instead of NFS.  I don't know.

"I have a need for mass storage with fault tolerance. I'm going with linux of course and a server that I built. Unfortunately it's fake raid but I've had it for a few years and it works pretty well as far as fault tolerance goes. My concern was throughput. I don't have a gigabit switch but I am using all Cat6 cabling for "future proofing." I'm planning on getting a faster switch in the future. Right now, it's a 100Mb unmanaged netgear switch. With this equipment, could I run reliable sessions straight from the server with, lets say, 88.2Khz 24 bit 24 channel sessions? That would probably be the most I would run. I'm talking recording and playback as well.

Edit:

I think I answered my question, but I need someone to check my math skills, which are terrible. My current setup with 100Mbps switch would be able to theoretically handle 12.5 megabytes per second, but let's be conservative and say 10MBps.

24 discrete 44.1kHz 24bit streams would look like this:

44100 x 24 x 24 = 25401600 bits per second.

Take 25401600 and multiply by .125 to get 3175200 bytes per second

Take 3175200 and divide by 1024 to get 3100.78125 kilobytes per second

Divide one more time by 1024 to get 3.028106689 Megabytes per second.

To me, that just sounds WAYYY to small of throughput to be possible. Where did I go wrong? That would mean that my current setup could easily do 24 channels @ 88.2kHz 24 bit @ 6.05 MBps."

---

### Post by inobe on 2011-02-18
> **pepsifx357 said:**
> It'l be all command line, no GUI.  I'm a brave soul.

> I need a simple tutorial on how to setup an NFS server

for future posts, could you possibly specify these things, because here i am asking where pictures are in your defense :P

---

### Post by pepsifx357 on 2011-02-18
> **inobe said:**
> for future posts, could you possibly specify these things, because here i am asking where pictures are in your defense :P

lol, I'm sorry, I guess I just assumed that setting up NFS was more advanced than GUI.  I didn't really know there was a GUI way to do it.  I guess "simple" was the misleading word there.:lolflag:

---

### Post by bartman2589 on 2011-04-03
> **inobe said:**
> right click the folder and hit sharing options, share the folder of of choice, you should receive a dialog telling you services need to be installed, there should be a drop down menu with choices, one is samba and the other is nfs, i think you can choose both or just one.

or just watch the video [http://vimeo.com/688987](http://vimeo.com/688987)

I wish it truly was as simple as you said (I'm using Kubuntu 10.10), I did exactly that (even made sure to check the box for 'Writable'), yet when I go back to the folder and check  the share tab a second time the share using nfs option has mysteriously unchecked itself.  I first thought it might be a problem with the permissions on the /etc/exports file since it's not set to allow anyone but root to modify it by default so I changed the file permissions to allow anyone to read and write to it and still no luck.  I'm going to keep on digging though.

---

