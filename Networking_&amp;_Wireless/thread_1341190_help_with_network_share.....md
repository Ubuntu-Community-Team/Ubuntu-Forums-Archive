---
title: "help with network share...."
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by meomike2000 on 2009-11-29
i have a fresh install of ubuntu 9.10, and i have created a folder on my desktop that i wish to share with the newwork, this all works great, problem is that when i log off and then log in again i have to share the folder again.....

also, if i try to login to the share from my ubuntu laptop, i can and i can move files to the share from the laptop, when i try this from my windows machine i can see the share and a login pops up, i enter my username and password for the machine with the share and i get rejected.....

any help or a point in the right direction would be great thanks in advance,
mike

---

### Post by kja999 on 2009-11-29
what type of share are you setting up ? Samba ?

---

### Post by meomike2000 on 2009-11-29
not sure, this is what i did...
on mdesk, that is the name of the machine with the share, i went to the command line and used this code:

```
sudo shares-admin
```

and set my workgroup and then set the path to the shares folder that i created on my desktop of mdesk, named it shares to keep it simple, then i could see mdesk on the when i clicked on places/network from my ubuntu laptop, but i couldnt access the share folder. so on mdesk i right clicked on the shares folder and clicked on sharing options, then i checked the share this folder box and it was shared, all worked well, i moved files from my laptop, ubuntu, to the shares folder and all is well till i log off/shut down/suspend mdesk, machine with the shares folder. when i log on again i have to right click on the folder and then click on sharing options and check the box again......

also when i try to log on to the shares folder from a windows machine i can see the folder in the network, when i click on it a login box appears, i enter my username and password for mdesk, the machine with the shares folder,  just like from my laptop, but it is not accepted from the windows machine.... 

i would like to have a folder on my machine called mdesk that i can move files to and from my other machines with, i have both windows and ubuntu machines, and i have multiple users that will need to access this shared folder, the goal is to have it so that all users will have a folder inside the shares folder on mdesk that will be private to them, they will have to have a password, and a folder there that all network users can access from any machine that is on the network...

hope this helps, mike

---

### Post by meomike2000 on 2009-11-29
i think that a samba server will be the way to go for what i need, will try to find more info on how to set this up for my needs, if any body knows of a good link on how to config samba i would be very thankful......

mike

---

### Post by meomike2000 on 2009-11-29
i have started a new thread over with the server folks, so will mark this as solved.....

---

