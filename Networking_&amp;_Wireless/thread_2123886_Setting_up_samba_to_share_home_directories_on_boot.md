---
title: "Setting up samba to share home directories on booting"
date: 2013-03-09
forum: Networking &amp; Wireless
---

### Post by slowmo on 2013-03-09
Hi 

I want to use Samba as a centralised way to share files over a home network. 

I'm fairly familiar with Samba and have managed to set up /home and general shares that were accessible once I had logged in. However, getting this to work from booting has proved to be more difficult and I just wanted to check that I was taking the right approach? Ideally I would like to achieve the following: 

[LIST]
[*]That the /home directory on the Samba server becomes the /home directory for all clients on booting. 
[*]That once the user logs onto the client machine their home share is accessible without having to re-enter a password (or no more than once). 
[*]That local home (I.e. the client machine) is not accessible to the user when the remote home share is accessible. 
[*]That there is some sort of synchronisation or fail safe set up where local home is kept updated and accessible in the event of the server being unavailable. 
[/LIST]

So what I would like to know is the following: 

[LIST]
[*]Is the [homes] setup in smb.conf suitable for this? 
For example could I use //ipaddress/homes/	/home/	cifs _netdev,user=samba,password=password	0 0 in fstab on the client machine to achieve the goals above? Or should I create a separate customised share for the server /home directory and link to that in fstab? E.g. 
[home]

path = /home/
comment = /home
browesable = no
writeable = yes 
valid users = @users 
And then link to that in fstab. 
Note: I'm aware that this is not a secure set up and is simply to test that it actually works. 
[*]Whether there is anything I'm missing, whether there is a better way to do it? (Preferably Samba based, as I want to be able to share with Windows machines and also because I want to learn Samba). 
[/LIST]

Some system details: 

Ubuntu 10.04 – Samba server. 
Linux Mint 11 – Samba client. 
Network – Standard wired ethernet. 

If there is anything that I haven't made clear then feel free to ask. Otherwise thanks in advance for any help.

---

### Post by Cheesemill on 2013-03-09
I'm afraid you can't use Samba as a solution for this problem.

CIFS (the protocol that Samba uses) was written by Microsoft for sharing files across a Windows network. As such it doesn't support the permissions structure that is necessary for a Linux home directory. This is the same reason you can't have an NTFS partition mounted as /home.

Having /home on a network is usually accomplished using NFS.
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by bab1 on 2013-03-09
> **Cheesemill said:**
> I'm afraid you can't use Samba as a solution for this problem.

CIFS (the protocol that Samba uses) was written by Microsoft for sharing files across a Windows network. As such it doesn't support the permissions structure that is necessary for a Linux home directory. This is the same reason you can't have an NTFS partition mounted as /home.

Having /home on a network is usually accomplished using NFS.
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I have to disagree here.  The Samba [homes] share is for just that purpose (e.g. maintaining home directories on a central server).  In fact you only need to configure the basic [homes] share and Samba will expand that to the specific users when they log in.

---

### Post by bab1 on 2013-03-09
> **slowmo said:**
> Hi 

I want to use Samba as a centralised way to share files over a home network. 

I'm fairly familiar with Samba and have managed to set up /home and general shares that were accessible once I had logged in. However, getting this to work from booting has proved to be more difficult and I just wanted to check that I was taking the right approach? Ideally I would like to achieve the following: 

[LIST]
[*]That the /home directory on the Samba server becomes the /home directory for all clients on booting. 
[*]That once the user logs onto the client machine their home share is accessible without having to re-enter a password (or no more than once). 
[*]That local home (I.e. the client machine) is not accessible to the user when the remote home share is accessible. 
[*]That there is some sort of synchronisation or fail safe set up where local home is kept updated and accessible in the event of the server being unavailable. 
[/LIST]

So what I would like to know is the following: 

[LIST]
[*]Is the [homes] setup in smb.conf suitable for this? 
For example could I use //ipaddress/homes/	/home/	cifs _netdev,user=samba,password=password	0 0 in fstab on the client machine to achieve the goals above? Or should I create a separate customised share for the server /home directory and link to that in fstab? E.g. 
[home]

path = /home/
comment = /home
browesable = no
writeable = yes 
valid users = @users 
And then link to that in fstab. 
Note: I'm aware that this is not a secure set up and is simply to test that it actually works. 
[*]Whether there is anything I'm missing, whether there is a better way to do it? (Preferably Samba based, as I want to be able to share with Windows machines and also because I want to learn Samba). 
[/LIST]

Some system details: 

Ubuntu 10.04 &#8211; Samba server. 
Linux Mint 11 &#8211; Samba client. 
Network &#8211; Standard wired ethernet. 

If there is anything that I haven't made clear then feel free to ask. Otherwise thanks in advance for any help.

You have the general idea right.  Although the [homes] share is located like this //SERVER/USER_NAME.  When the user logs in the share is available for them.  This will not eliminate the local /home/$USER directory.  The [homes] share can be mounted inside the local home directory.  Note you do NOT share the entire user base.  Samba creates on the fly a share for the individual user as they mount the share to the local host.

NFS is a little different in that you can easily mount the entire home directory structure (all users) at /home of the local host.  The user will only have access to their own home directory.  Just as it would be if all users of the local host had local home directories.

Either way will work.  I find that they both have their advantages and disadvantages.  

NFS works great if you have a later CPU and HDD  I/O capacity.  If not, it has latency problems.  Samba on the other hand doesn't seem to have any latency problems.  I have host with a P3 with 512MB of RAm that is a Samba server.  NFS won't work very well on this machine.      

Samba[homes] is not intuitive to setup in fstab for Linux (easier as a mapped share),  but is really only needed if you have Windows hosts.  NFS is easiy to set up and is seamless to Linux users when properly installed.

---

### Post by slowmo on 2013-03-10
Thanks for the responses, they have proved very helpful. 

I think I will have to look into NFS properly as I'm not sure Samba is entirely suitable for my needs. I started with Samba because although I don't use Windows machines very often, I do occasionally, so it seemed better to use a method that could be used by both systems. I had also read a lot about NFS not the most secure, so it seemed better to try Samba. 

Although Samba can mount in a users /home directory the problem I could envisage with that is that it gives the users the option to save files locally as well as on the server share (if they mount and access it). Therefore data could become decentralised by users that do not understand that they are different physical locations. Is this why sometimes people use links with Samba? I mean would it be feasible to either delete or hide all objects in a users home directory and just create a link to the [homes] Samba share? 

This way they may be more likely to access the centralised server files, although they would still be able to save to their local /home directory and this could de-centralise. Also would it require a lot of reconfiguration because a lot of programs would have default locations in the users home directory for saving data? So it does seem like NFS is probably the more straight forward and suitable solution here. 

Sorry if this has gone on but I thought I would go through my thought processes a little bit encase it is useful to anyone else.

---

### Post by bab1 on 2013-03-10
> **slowmo said:**
> Thanks for the responses, they have proved very helpful. 

I think I will have to look into NFS properly as I'm not sure Samba is entirely suitable for my needs. I started with Samba because although I don't use Windows machines very often, I do occasionally, so it seemed better to use a method that could be used by both systems. I had also read a lot about NFS not the most secure, so it seemed better to try Samba. 
Generally speaking Windows hosts can't access NFS exports.  If you have any windows hosts you will need to share files via Samba with a Linux host.> 

Although Samba can mount in a users /home directory the problem I could envisage with that is that it gives the users the option to save files locally as well as on the server share (if they mount and access it). Therefore data could become decentralised by users that do not understand that they are different physical locations. Is this why sometimes people use links with Samba? I mean would it be feasible to either delete or hide all objects in a users home directory and just create a link to the [homes] Samba share? 
Something to  to ponder; there is no absolute reason that Linux home directories need to be at /home. You could mount all of the users [homes] directories  /smb or /smb/home if you wanted. > 

This way they may be more likely to access the centralised server files, although they would still be able to save to their local /home directory and this could de-centralise. Also would it require a lot of reconfiguration because a lot of programs would have default locations in the users home directory for saving data? So it does seem like NFS is probably the more straight forward and suitable solution here. 

Sorry if this has gone on but I thought I would go through my thought processes a little bit encase it is useful to anyone else.
In most cases it it better to create something that is simple and generally known.  You need to decide if you are storing *some* of the users files centrally or *all* of the users files in their home directory centrally.  Remember that the home directory does not have to be /home/$USER.

In the past I have used all of these paradigms.  I've stored data at /data and home directories both  /smb/home and the standard /home/$USER (not at the same time) and NFS exports to /home for home directories.

Start simple but don't be afraid to experiment.

---

