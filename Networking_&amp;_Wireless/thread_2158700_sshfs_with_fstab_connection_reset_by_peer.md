---
title: "sshfs with fstab: connection reset by peer"
date: 2013-06-30
forum: Networking &amp; Wireless
---

### Post by skedar on 2013-06-30
Hi!
  I am trying to allow my laptop (Ubuntu 13.04) to access my PC  (Lubuntu 13.04) hard drive through SSHFS. I'm using RSA keys to connect.
  It works perfectly fine if I type this in the terminal:


  ```
sshfs my-PC:/a_folder /media/a_folder
```  

But I would like it to be mounted automatically when I boot my laptop. So I added myself to the fuse group:


  ```
sudo adduser mynickname fuse
```  

And I added the following line to my fstab file:


  ```
sshfs#mynickname@my-PC:/a_folder /media/a_folder fuse defaults,idmap=user,_netdev 0 0 
```  

When I boot the laptop, a_folder appears in the list of devices, but  is not mounted. When I try to access it through Nautilus, it displays  the following error:


  ```
mount: only root can mount sshfs#mynickname@my-PC:/a_folder on /media/a_folder 
```  

I get the same error if I try


  ```
mount /media/a_folder 
```  

in a terminal.
  If I try


  ```
sudo mount /media/a_folder 
```  

I get


  ```
read: Connection reset by peer 
```  

I get this same error in my boot log, so this is the issue that prevents the harddrive to get mounted at boot as well.
  I tried to add "allow_other" as an option in the fstab entry, and  uncommented the related line in /etc/fuse.conf, but it didn't change  anything.


  The user "mynickname" is the owner of the folder /media/a_folder and has rwx permissions.


  I looked at many threads on the internet about people with quite  similar issues, but nothing worked so far. Usually, people can't even do


  ```
sshfs my-PC:/a_folder /media/a_folder 
```  

without getting an error, whereas this works fine on my laptop.


  Any insight and tips will be greatly appreciated! Thanks.

---

