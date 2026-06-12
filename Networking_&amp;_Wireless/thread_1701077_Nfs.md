---
title: "Nfs"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by intranick on 2011-03-06
I have been trying to set up NFS to share /home/nick/shared for a couple days now.  

Following this guide, [https://help.ubuntu.com/community/SettingUpNFSHowTo#Minimalistic%20NFS%20Set%20Up](https://help.ubuntu.com/community/SettingUpNFSHowTo#Minimalistic%20NFS%20Set%20Up)

I changed exactly what I thought I needed to -- to be /home/nick/shared..

for example, using 
# mount --bind /home/nick/shared /export/shared

(after linking /home/nick/shared to /export/shared)

everything looks fine, and mounts on the client, but the folder shows up as empty 

I tried creating a quick text file in it from the client and and got denied

anyways.. I am new to this one, so if i left out anything you need to help me, lemme know and I'll gladly look into it

If I need to somehow login to "nick" on my server using that password, how do i do this? 

Thanks, any help would be appreciated

---

### Post by VastOne on 2011-03-06
> **intranick said:**
> I have been trying to set up NFS to share /home/nick/shared for a couple days now.  

Following this guide, [https://help.ubuntu.com/community/SettingUpNFSHowTo#Minimalistic%20NFS%20Set%20Up](https://help.ubuntu.com/community/SettingUpNFSHowTo#Minimalistic%20NFS%20Set%20Up)

I changed exactly what I thought I needed to -- to be /home/nick/shared..

for example, using 
# mount --bind /home/nick/shared /export/shared

(after linking /home/nick/shared to /export/shared)

everything looks fine, and mounts on the client, but the folder shows up as empty 

I tried creating a quick text file in it from the client and and got denied

anyways.. I am new to this one, so if i left out anything you need to help me, lemme know and I'll gladly look into it

If I need to somehow login to "nick" on my server using that password, how do i do this? 

Thanks, any help would be appreciated

I do not know how "locked into" NFS you are, but I would strongly recommend ssh/sshfs combination.  It is by far the easiest and fastest that I have worked with and here is a great link to help you

[_[COLOR="Blue"]sshfs How to here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=430312")

If you do try it and run into any roadblocks, let me know, I can help you with ssh/sshfs  

To let you know, I did run NFS elusively until I used ssh/sshfs

It also sets up great with another app called Grsync that is a front end for rsync, and once you get to that point it is an extremely beneficial incremental backup system.  I have a lot of music and tab files that change daily (thousands) and need to sync to another machine and this setup is unmatched

Good luck~!

---

### Post by intranick on 2011-03-06
well, I was hoping to be able to watch movies storied on my desktop from my laptop without transferring the whole file before i watch it (otherwise I would just scp them)  

would this be possible with sshfs?

---

### Post by VastOne on 2011-03-06
> **intranick said:**
> well, I was hoping to be able to watch movies storied on my desktop from my laptop without transferring the whole file before i watch it (otherwise I would just scp them)  

would this be possible with sshfs?

Connected through a standard router you should be no issues at all.

---

### Post by intranick on 2011-03-06
i kinda feel like im running in circles tho.. because nfs and smb are both failing and I wish I could figure out -why- because there has to be something that wasnt documented that im doing wrong...

---

