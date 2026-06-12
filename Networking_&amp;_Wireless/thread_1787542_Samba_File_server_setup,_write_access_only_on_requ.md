---
title: "Samba File server setup, write access only on request possible?"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by RinRinchan on 2011-06-21
Hi, still green so don't hurt me :D 

I'm currently setting up a file server and am testing configs on a old system before it gets here. I currently through trile and error got samba working with user/pass. along with ssh somewhat settup.  
Current setup basically has just xubunto installed + samba and open_ssh.  What I would like to do is set is have the samba shares as read only unless the user specifically requests write access to be allowed on the shares. eg. they use putty to ssh into the box with there username/pass then run some kind of command. (which would then give their username write access to the samba shares they have access to)

Also if possible I would like this write access to timeout lets say 2-3days after it is requested. (only if possible)  
By doing this I plan on minimizing the possibility of a rouge compromised windows system given access to say my media shares and running a mass delete and/or corrupting/ infecting other files. (example) 

Any help would be awesome, thanks in advance

---

### Post by Toz on 2011-06-21
Okay, I'll bite.

Here is what I do (somewhat similar). I've created two shares that point to the same directory. One is a read-only share and the other is what I call an admin share. Here are the relevant sections from my samba config file (disclaimer: I'm running samba on an OpenBSD server so my samba config file may differ slightly from the version Ubuntu uses - you will need to test and adapt as required).
> [media]
      comment = Media Files
      path = /data/media
      public = yes
      writeable = no
      printable = no

[_media]
      comment = Media Files - Admin
      path = /data/media
      valid users = @mediaadmins
      public = no
      writeable = yes
      printable = no
      force create mode = 0775
      force directory mode = 2775
      force group = mediaadmins

The first group, read-only by virtue of directory/file permissions (see below) must have smb account on server to access files (smbpasswd -a) and accesses the **media** share.

The second group, full access by virtue of directory/file permissions (see below) must have smb account on server _and_ belong to mp3admins group and accesses the **_media** share.

Now the directory/file permissions:
```
chmod -R 2775 /data/media
chown -R root:mediaadmins /data/media
```
...resulting in:> drwxrwsr-x  2 root    mediaadmins 4096 2011-06-21 12:10 media/

Now, to answer your question of logging in via ssh and making some change, the change could be to add the user to the mediaadmins group and then access the _media share.

To automatically delete the group membership after 2-3 days will require some advanced scripting. However, I must say, if you get compromised by someone who wants to delete all your data, the 2-3 day thing won't really matter. Consider backing up your data.

---

### Post by RinRinchan on 2011-06-21
Firstly thanks for the reply, nicely layed out and easy to understand.

I never thought of this, and it would work as a solution for my own files.
(though still open to idea's/ expansions to this idea :D  )

Though I don't think I could implement this on the other 2 user's I plan create due to not wanting to not give them root access and needing root for the command.
(I would rather they didn't break my new server, trust me i'm sure they would somehow break the os even just useing basic commands lol)

As for backup's I backup externally monthly for my main pc and I plan to do the same on the server. this is just a extra precaution to protect the data in between backups, 
I sugested 2-3 days only cause that would alow for a mass copy of any size in that time-frame. If they could choose x amount of hours that would work too.

Thanks again so far.

---

### Post by collisionystm on 2011-06-21
You should backup using rsnapshot. Monthly backups are a bit dangerous.

---

### Post by RinRinchan on 2011-06-21
> **collisionystm said:**
> You should backup using rsnapshot. Monthly backups are a bit dangerous.

While that's true, the reason I use monthly backups is due to having the drives physically unplugged from power/system except for backups.
Just a balance of data protection/ convenience I guess. I can live with 30 days of lost data, loosing a whole drive worth is another story :D

I will keep the program in mind though since I'm used to doing my backup sync's on my windows machines I've yet to choose a program to do this task on the  xubunto server.

Thanks for input :D

---

### Post by Toz on 2011-06-21
> **RinRinchan said:**
> Though I don't think I could implement this on the other 2 user's I plan create due to not wanting to not give them root access and needing root for the command.
Just thinking out loud here. You could create a root cron script that runs every minute and looks for the existence of a specific file in each user's home directory (ie. need_full_access), and if it exists, use the root credentials to add that user to the proper group. Maybe even expand on this and put some sort of time tracking logic in there so that expires after say 2-3 days. All the user would have to do is:```
touch ~/need_full_access
``` and wait for a minute.

---

### Post by RinRinchan on 2011-06-22
Thanks again Toz,

Does this have any adverse side effects (security wise). 
Sorry for the newbyness :D 
I've only touched abit of linux for fun over the years never as a permanent OS.

---

### Post by Toz on 2011-06-22
> **RinRinchan said:**
> Does this have any adverse side effects (security wise).
I guess it would depend on what you mean by "adverse side effects". You will be granting these users full access to your media share, which you explained earlier was a concern. As for the system itself, I don't see any specific security issues from running this kind of setup outside the regular security issues of running any type of server offering up services. If the server is available to the general internet, make sure you are running a firewall.

---

### Post by RinRinchan on 2011-06-22
Yeah, I was planning on mostly likely killing its internet access bar update/ install repositories (right word im looking for?)

Only Need to access it from the local netowrk

Thanks again, your awesome :D

---

