---
title: "Multiple users, common share"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by oi_antz on 2012-02-24
Hello, I am setting up a development server for work. It will run PHP with Apache2, MySQL and Pure FTPD. This will enable us to develop websites more efficiently on our internal network, and with port forwarding on the router we will expose the sites to our outsource agencies so they can access the server as required.

One obvious issue with this is that each website must be isolated from the others, otherwise we risk someone writing to a site they have not been authorized to access. So the way I have approached is this is to write a very simple bash script that takes a bit of info and generates user accounts, virtual host file, /etc/hosts entry and restarts Apache. 

Each website is created under a new Linux user account. The user has a unique username and password so we could end up with hundreds of users, one for each active website. If you know a better way to do it, please suggest it! 

Pure FTPD then enables us to login to create and manage files as the true owner of those files. So the document root resides in /home/[username]/www and the Apache virtual host file uses the "AssignUserId" directive to set the [username] and group to www-data.

This is an example of an Apache2 Virtual Host directive:

```

<VirtualHost *:80> 
	ServerName test10.antz.loc 
	DocumentRoot /home/test10/www 
	ServerAdmin antz@example.com 
	ErrorLog /home/test10/error.txt 
	LogLevel notice 
	CustomLog /home/test10/log.txt combined 
	AssignUserId test10 www-data 
</VirtualHost>

```

So far so good, I actually have this running exactly as it should. Problem is that when we work internally we want to use Samba to share the server files instead of FTP. That's easily done by sharing the folder with the username and password of the owner, that anyone who logs in with the owner's username and password will create files that are owned by the rightful username. The problem is that for each website we create, we have to mount the share using the given username and password, but what we want is to have a super user account that we can use internally to access all sites under /home.

Not sure if this is even possible, or am I asking to keep the cake while eating it too. Perhaps there is a better way? I've only ever seen one or the other, either you have a username/password for each website or you have a super user account, but I've never seen both on the same server and I can't even imagine how to do it. So your input is greatly appreciated! ](*,)

Thanks!

---

### Post by redmk2 on 2012-02-24
> **oi_antz said:**
> Hello, I am setting up a development server for work. It will run PHP with Apache2, MySQL and Pure FTPD. This will enable us to develop websites more efficiently on our internal network, and with port forwarding on the router we will expose the sites to our outsource agencies so they can access the server as required.

One obvious issue with this is that each website must be isolated from the others, otherwise we risk someone writing to a site they have not been authorized to access. So the way I have approached is this is to write a very simple bash script that takes a bit of info and generates user accounts, virtual host file, /etc/hosts entry and restarts Apache. 

Each website is created under a new Linux user account. The user has a unique username and password so we could end up with hundreds of users, one for each active website. If you know a better way to do it, please suggest it! 

Pure FTPD then enables us to login to create and manage files as the true owner of those files. So the document root resides in /home/[username]/www and the Apache virtual host file uses the "AssignUserId" directive to set the [username] and group to www-data.

This is an example of an Apache2 Virtual Host directive:

```

<VirtualHost *:80> 
	ServerName test10.antz.loc 
	DocumentRoot /home/test10/www 
	ServerAdmin antz@example.com 
	ErrorLog /home/test10/error.txt 
	LogLevel notice 
	CustomLog /home/test10/log.txt combined 
	AssignUserId test10 www-data 
</VirtualHost>

```

So far so good, I actually have this running exactly as it should. Problem is that when we work internally we want to use Samba to share the server files instead of FTP. That's easily done by sharing the folder with the username and password of the owner, that anyone who logs in with the owner's username and password will create files that are owned by the rightful username. The problem is that for each website we create, we have to mount the share using the given username and password, but what we want is to have a super user account that we can use internally to access all sites under /home.

Not sure if this is even possible, or am I asking to keep the cake while eating it too. Perhaps there is a better way? I've only ever seen one or the other, either you have a username/password for each website or you have a super user account, but I've never seen both on the same server and I can't even imagine how to do it. So your input is greatly appreciated! ](*,)

Thanks!

I'm not sure why you have the web root in /home.  Samba shares can be located anywhere (I use /smb) and I assume that the web root can be configured too.  

When I have common files (multiple users) I control access by GID rather than  UID.  I also set the umask to 002 rather than 022.  This gets sets the perms to 775 for directories and 664 for files.  

If you look at the list of groups (**getent group**) you will see a group called *sambashare*.  If you add all users (that are sharing) to this group and chgrp the file to *sambashare *, all will be able to manipulate the files.  

If you set the sticky bit, users should not be able to delete files they didn't create.  You might try setting the sguid bit to force group ownership.  You can also do this by setting the force group parameter in your samba share for GID consistency.

---

### Post by oi_antz on 2012-02-24
> **redmk2 said:**
> I'm not sure why you have the web root in /home.  Samba shares can be located anywhere (I use /smb) and I assume that the web root can be configured too.  

When I have common files (multiple users) I control access by GID rather than  UID.  I also set the umask to 002 rather than 022.  This gets sets the perms to 775 for directories and 664 for files.  

If you look at the list of groups (**getent group**) you will see a group called *sambashare*.  If you add all users (that are sharing) to this group and chgrp the file to *sambashare *, all will be able to manipulate the files.  

If you set the sticky bit, users should not be able to delete files they didn't create.  You might try setting the sguid bit to force group ownership.  You can also do this by setting the force group parameter in your samba share for GID consistency.

Thanks, yes I don't care where the files are kept as long as it is consistent. But I really don't want directories to be 775, I want all directories and files to be 644. I only want the FTP user and the Apache run user to be able to write to the directories and files they own. 

Basically this is to protect us in case one of our outsource companies has a malicious developer, they may use FTP or Apache to plant a malicious script on a site they have not been granted access to. This is the purpose of creating separate Linux users for each website. Maybe I have not explained it so clearly, let me give an example:

User 1:

Site: [www.foodsupplies.com](www.foodsupplies.com)
Username: foodsupplies
Password: pasword1

This user should have rw access to everything in /[path is whatever]/foodsupplies.com but not /[path is whatever]/toolsupplies.com

User 2:

Site: [www.toolsupplies.com](www.toolsupplies.com)
Username: toolsupplies
Password: password2

This user should have rw access to everything in /[path is whatever]/toolsupplies.com but not /[path is whatever]/foodsupplies.com

Can you see that making directories any greater than 644 will defeat the purpose of granting separate user permissions? The aim is to prevent one user from writing to a path that they don't own.

However, that is not the problem, I actually have it working like that and have confirmed that each website is sufficiently segregated to prevent unauthorized writing.

The problem I need to solve is whether the Samba protocol can create a root share to access all paths under /home while maintaining the owner's username when writing. I'm expecting a very simple "no" to this, but I did want to ask before I went back to my manager with that answer.

Thanks again! :D

---

### Post by redmk2 on 2012-02-24
> **oi_antz said:**
> Thanks, yes I don't care where the files are kept as long as it is consistent. But I really don't want directories to be 775, I want all directories and files to be 644. I only want the FTP user and the Apache run user to be able to write to the directories and files they own. 

Basically this is to protect us in case one of our outsource companies has a malicious developer, they may use FTP or Apache to plant a malicious script on a site they have not been granted access to. This is the purpose of creating separate Linux users for each website. Maybe I have not explained it so clearly, let me give an example:

User 1:

Site: [www.foodsupplies.com](www.foodsupplies.com)
Username: foodsupplies
Password: pasword1

This user should have rw access to everything in /[path is whatever]/foodsupplies.com but not /[path is whatever]/toolsupplies.com

User 2:

Site: [www.toolsupplies.com](www.toolsupplies.com)
Username: toolsupplies
Password: password2

This user should have rw access to everything in /[path is whatever]/toolsupplies.com but not /[path is whatever]/foodsupplies.com

Can you see that making directories any greater than 644 will defeat the purpose of granting separate user permissions? The aim is to prevent one user from writing to a path that they don't own.

However, that is not the problem, I actually have it working like that and have confirmed that each website is sufficiently segregated to prevent unauthorized writing.

The problem I need to solve is whether the Samba protocol can create a root share to access all paths under /home while maintaining the owner's username when writing. I'm expecting a very simple "no" to this, but I did want to ask before I went back to my manager with that answer.

Thanks again! :D

A couple of thoughts.  You must allow all directories that are to be traversed (descend into or passed through) execute permissions.  This means for a single user at least 5 (r X) or (7 rwx).  Note this is for directories only.  Files of course should be 6 (rw) or 4 (r).  

As far as I know there are no superuser (root) rights that Samba can provide.  Certainly none that trump the system permissions.  

The root user is a local (to that host) notion.  If you set it up, you can always ssh to the host and *su to root* to modify or provide maintenance to all of the files.

Edit:  Another way to do this would be to create a group for each web site that includes the admin (your super user).  That way you get what you need (separation) and an admin user that can access all the developers sites.

It would be like this```

user:group
====:====
foodsupplies:web_admin
toolsupplies:web_admin
```

Of course the perms would be 775 for directories and 664 for files.  This is not as insecure as you think.  Only the designated user and the web_admin have access to each web sites.

This of course is a variation on my first idea.

---

