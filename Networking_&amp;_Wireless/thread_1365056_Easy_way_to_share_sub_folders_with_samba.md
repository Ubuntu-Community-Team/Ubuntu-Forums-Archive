---
title: "Easy way to share sub folders with samba?"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by deathbyswiftwind on 2009-12-26
Could anyone please tell me if there is an easier way of sharing sub-folders on samba. I really dont want to have to go through and right click on every folder in order to share everything. I have all of my music broke down like /home/bob/music/band/album and there has just got to be an easier way for me to apply the share permission to all folders and files within the music folder instead of right clicking on every individual folder. If not I may have to relook at the way I sort out my music

I have alot of music and it would take forever to go through right clicking everything. Also if I do that then it all just shows up as a seperate share. Lol when I have approx 1000 cds thatd be alot of shares.

---

### Post by Morbius1 on 2009-12-26
Right click to share on /home/bob/music doesn't share all of it's subdirectories?

---

### Post by deathbyswiftwind on 2009-12-26
No for some reason it wont. It will allow me to see any files and the folders inside but if I try to click on a sub-folder it gives me a permission denied error. 

Just a basic rundown is I am running Ubuntu 9.10 on both my desktop(file server) and my laptop.

---

### Post by Morbius1 on 2009-12-26
Could you post the output of the following command please:

Open **Terminal**
Type **ls -l /home/bob/music**

If it's like 30 pages long or something I'll get the idea after a dozen or so.

---

### Post by deathbyswiftwind on 2009-12-26
Nevermind Im retarded. When I copied all of my files over from my windows external I forgot to fix the permissions on the individual files.

---

### Post by Morbius1 on 2009-12-26
You know you could set this up so that if you forget again it won't matter.

Those folders and files that you copied came over with owner = bob and permissions set to read/write for bob only. You could trick samba into thinking that every remote user is you ( at least as far as that share is concerned ) by doing something like this:

Press **Alt+F2**
Type **gksu gedit /etc/samba/smb.conf**

In the **[global]** section add the following line:

**force user = bob**

Save the file and restart samba: [B]sudo service samba restart

[/B]This technique still follows the nautilus-share authentication rules. If you allow guest everyone will have access. If you require authentication then only users that have password will have access. If you only allow read access then only read access will be permitted, but once they're into the share they will appear to be you.

It also comes in handy the other way around. If somebody writes to your share it comes across as owner = nobody. That means you have to change permissions in order for you to write to it. But with **force user** those files will come across as owner = bob.

Something to think about if you do this a lot.

---

### Post by deathbyswiftwind on 2009-12-26
Awesome thank you for that I didnt know you could force user. Thats one thing I love about linux. Everytime I find something I need some crafty person has already created it!

---

### Post by Artmanx on 2010-01-30
Thanks, helped a lot!

---

### Post by jkurtisr32 on 2010-11-21
> **Morbius1 said:**
> You know you could set this up so that if you forget again it won't matter.

Those folders and files that you copied came over with owner = bob and permissions set to read/write for bob only. You could trick samba into thinking that every remote user is you ( at least as far as that share is concerned ) by doing something like this:

Press **Alt+F2**
Type **gksu gedit /etc/samba/smb.conf**

In the **[global]** section add the following line:

**force user = bob**

Save the file and restart samba: [B]sudo service samba restart

[/B]This technique still follows the nautilus-share authentication rules. If you allow guest everyone will have access. If you require authentication then only users that have password will have access. If you only allow read access then only read access will be permitted, but once they're into the share they will appear to be you.

It also comes in handy the other way around. If somebody writes to your share it comes across as owner = nobody. That means you have to change permissions in order for you to write to it. But with **force user** those files will come across as owner = bob.

Something to think about if you do this a lot.

Good look. This worked to fix my permission issues as well. Thanks, man

---

### Post by SagnaB on 2012-01-11
> **Morbius1 said:**
> You know you could set this up so that if you forget again it won't matter.

Those folders and files that you copied came over with owner = bob and permissions set to read/write for bob only. You could trick samba into thinking that every remote user is you ( at least as far as that share is concerned ) by doing something like this:

Press **Alt+F2**
Type **gksu gedit /etc/samba/smb.conf**

In the **[global]** section add the following line:

**force user = bob**

Save the file and restart samba: [B]sudo service samba restart

[/B]This technique still follows the nautilus-share authentication rules. If you allow guest everyone will have access. If you require authentication then only users that have password will have access. If you only allow read access then only read access will be permitted, but once they're into the share they will appear to be you.

It also comes in handy the other way around. If somebody writes to your share it comes across as owner = nobody. That means you have to change permissions in order for you to write to it. But with **force user** those files will come across as owner = bob.

Something to think about if you do this a lot.

```

[B]sudo service samba restart
[/B]
```gives me
```

samba: unrecognized service

```as though it's not installed, but Synaptic says it is... :S

I am having trouble sharing with samba, period. Nautilus and samba do not seem to work well together.
I was at the begining of all this, unable to access child directories, but that seems to work magically now. So my post is probably a bit off-topic here.

I'm trying to share files on an external HDD plugged into a desktop over WIFI to my laptop.
I can access some shared files (not on ext.HDD) but only using Ctrl+L and typing in the bar:
smb://192.168.1.9
as nautilus displays nothing at all.

The issue with the ext.HDD, would that be due to it being mounted to /media, a ROOT controlled directory?

---

### Post by Morbius1 on 2012-01-11
> samba: unrecognized serviceSine my post the "samba" service has been split between it's constituent daemons. So the current way to restart is:
```
sudo service smbd restart
```>  The issue with the ext.HDD, would that be due to it being mounted to /media, a ROOT controlled directory?     Depends on how you formatted the external HDD. If it's with a linux filesystem then you need to change permissions on the mounted directory to allow access to the samba client. If it's NTFS or FAT32 then it will mount with access permitted only to you and no one else. In either case a "force user" will fix it.

---

### Post by Fodderuntu on 2012-07-24
Just wanted to say thanks man, fixed my issue to! working well thanks!

Ubuntu 12.04 server and Windows 7 x64 clients

---

### Post by yvan232002 on 2012-09-12
Hi, thank you so much, this conversation solved my problem too.
Best wishes,
Yvan     :p



> **Morbius1 said:**
> You know you could set this up so that if you forget again it won't matter.

Those folders and files that you copied came over with owner = bob and permissions set to read/write for bob only. You could trick samba into thinking that every remote user is you ( at least as far as that share is concerned ) by doing something like this:

Press **Alt+F2**
Type **gksu gedit /etc/samba/smb.conf**

In the **[global]** section add the following line:

**force user = bob**

Save the file and restart samba: [B]sudo service samba restart

[/B]This technique still follows the nautilus-share authentication rules. If you allow guest everyone will have access. If you require authentication then only users that have password will have access. If you only allow read access then only read access will be permitted, but once they're into the share they will appear to be you.

It also comes in handy the other way around. If somebody writes to your share it comes across as owner = nobody. That means you have to change permissions in order for you to write to it. But with **force user** those files will come across as owner = bob.

Something to think about if you do this a lot.

---

