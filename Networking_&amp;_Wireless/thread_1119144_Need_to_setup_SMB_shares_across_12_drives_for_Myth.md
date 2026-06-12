---
title: "Need to setup SMB shares across 12 drives for Mythvideo ? Confused."
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by rodercot on 2009-04-07
Hello All,

 I have been at this since Saturday morning at 5am. I am trying to setup mythvideo to see my Mediaserver, I would like mount the server shares on the master backend and then symlink the folders to /var/lib/mythtv/videos/movies and /var/lib/mythtv/videos/hdmovies.

 All my machines are on the same network (local) I have an Unraid Server with the 12disks in it and on each of those 12 disks I have a Movies1-12 folder and a TV1-12 folder and on disk10 and 12 I have a Hdmovies10 and 12 folder. 

 I have tried pyNeighborhood and xsmbrowser with no luck, It just will not see my mediaserver even if I force it. The media server is Unraid (Samba 3.0?) but the shares are SMB as windows (M$ network neighborhood show 12 disks under the Computer (Tower)

 So I am coming to the conclusion that I need to create a separate entry in fstab for each folder on each drive and set those to the proper corresponding share in the folder /home/user/media/ that I have created.  I hope this is right because I am lost otherwise.
 
 //192.168.1.102/disk1/Movies1 /home/user/media/Movies1 
 //192.168.1.102/disk2/Movies2 /home/user/media/Movies2 etc...

 and the same for all my TV show folders.

 Now, once this is all done and the folders are mounted, how can I create ONE symlink to the /var/lib/mythtv/video/movies directory or is that possible. 
 
 Any help would be Greatly Appreciated.

 Thanks,
 
 Dave

---

