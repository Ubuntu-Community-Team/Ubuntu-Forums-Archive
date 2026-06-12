---
title: "how-to mount a network smb share so that mythbuntu will recognize it"
date: 2008-01-14
forum: Mythbuntu
---

### Post by onesojourner on 2008-01-14
This took my a while to figure out but I finally did with some help from Dr_willis on the irc. 

Step 1
find the location of the samba share. Mine was at:
smb://desktop/videos

Find the actuall ip address of the share. on the machine that is hosting the smb share ope a terminal and type ifconfig that will display your network adapters.

so my share was found at smb://192.168.1.129/videos

step 2

Create new directory, in the terminal
```
 sudo mkdir /var/lib/mythtv/videos/smb_videos
```

```
 sudo apt-get install gedit 
```

open Applications > Accessories > Thunar File Manager

on the left, click file system.

Right click on ect and then open terminal here.

in the terminal
```
sudo gedit fstab 
```


then at the bottom of the file you need to add this line modified with your information

```
   //192.168.1.129/videos  /var/lib/mythtv/videos/smb_videos  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

The first part (//192.168.1.129/videos) is my network share. change that to the ip address and the name of your share.  the second part (/var/lib/mythtv/videos/smb_videos) is the location you want the share mounted to and the share name.

Then in the terminal:
```
sudo mount -a
```


Hopefully that saves some one out there a little time.

---

### Post by Trimble Epic on 2008-01-17
I keep this threat on speed-dial for when I want to mess with my connections

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by Truande on 2008-01-29
Thank you!!!

It has been really usefull!!!!
You saved 1 mythbuntu user, I was loosing patience...3 days!
Thanks again mate!

---

### Post by onesojourner on 2008-01-30
glad it helped. One thing I have noticed though, if my machine hosting the share is off during boot up the myth machine will try to connect to the share for about 5 minutes before it gives up.

---

### Post by Truande on 2008-02-01
Just Thank you!
It saved me a lot of time! (I just spent several days to look for this info as I am a newbie in linux)

bye

---

### Post by sceo on 2008-06-13
> **onesojourner said:**
> glad it helped. One thing I have noticed though, if my machine hosting the share is off during boot up the myth machine will try to connect to the share for about 5 minutes before it gives up.

I have a somewhat similar problem.  I have the samba share mounting in the fstab, except it appears to be attemping to mount the share before the network is started... so my boot process takes a long time, and then it's never mounted when the machine starts up -- I have to manually mount it.

Is there a good way to mount network drives after the network has started up?

---

### Post by TonyJ2 on 2009-10-02
> **sceo said:**
> I have a somewhat similar problem.  I have the samba share mounting in the fstab, except it appears to be attemping to mount the share before the network is started... so my boot process takes a long time, and then it's never mounted when the machine starts up -- I have to manually mount it.

Is there a good way to mount network drives after the network has started up?

I am having the same problem.  Has anyone determined what the problem is in this situation?

---

### Post by Caysho on 2009-10-02
I have the same issue with the speed, but it [does mount]("http://ubuntuforums.org/showthread.php?t=1219037").
My experience is that Network Manager is slow.

---

### Post by TonyJ2 on 2009-10-03
> **Caysho said:**
> I have the same issue with the speed, but it [does mount]("http://ubuntuforums.org/showthread.php?t=1219037").
My experience is that Network Manager is slow.

Try doing adding this to the end of /etc/network/interfaces:
```

auto eth0
iface eth0 inet dhcp

```
This solved the failing to mount at boot problems for me.  It may speed up your boot.

I also switched to wicd, but that didn't solve the problem until I added those lines to the interfaces file.

---

### Post by blacknanna on 2010-02-19
I'm probably doing something stupid but, I did everything above and it has obviously worked because if I go to the video folder with Thunar all my movies appear when I click Movies_A or Movies_B. However I cant get the movies to show up in mythtv. I have directed mythtv to this folder in setup but when I try to access the movies with mythtv they don't show up. I just dont remember it being this hard last time.   #-o

---

### Post by blacknanna on 2010-02-19
woops, probably the wrong forum for that one.....

---

### Post by blacknanna on 2010-02-19
woops, probably the wrong forum for that one......

---

