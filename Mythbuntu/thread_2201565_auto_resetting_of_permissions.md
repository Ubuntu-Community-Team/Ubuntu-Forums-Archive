---
title: "auto resetting of permissions"
date: 2014-01-24
forum: Mythbuntu
---

### Post by jonnybignote on 2014-01-24
Hello all.  I'll admit, I don't know if this is a mythtv, mythbuntu or an ubuntu thing.

Mythbuntu 12.04

Whenever I try to access they smb shares of my linux backend machine via network (macbook pro), I don't have enough permissions to do anything other than view files.  I can make the changes to the permissions via terminal and then all is ok.  However, the next time I come back to it (let's say 2 weeks later) then the permissions have been reverted and I have no access again.

Is there something like a cron script in the default install that may be running and is responsible for this?  I'm doing some automated rsync backups also, but I don't see why that would be responsible.

It's been going on a long time, but I'm doing more file transfers of music etc now, and it's starting to really get to me.  

Wondered if anyone knew...


Thanks in advance

---

### Post by tfrue on 2014-01-25
Well, I don't know much about Mythbuntu, but what commands are you using to change permission on the files? If you are SSHing into the linux machine and creating the files there, you may be making them as root which would give them access only.

You could add a user with smbpasswd -a and change the smb.conf to only allow you access to that share, but before I get into that, will you post this command on the machine hosting the samba shares.
```
sudo cat /etc/samba/smb.conf | tail 
```

You might not be giving yourself enough permission from the defined share.

---

### Post by Morbius1 on 2014-01-25
In order to answer the question the folks here need to know how you are set up. If you post the output of these commands it will tell them that:
```
testparm -s
```
```
net usershare info --long
```
Don't be surprised if you get no output from the second command. It's a "just in case".

---

### Post by jonnybignote on 2014-01-26
> **tfrue said:**
> Well, I don't know much about Mythbuntu, but what commands are you using to change permission on the files? If you are SSHing into the linux machine and creating the files there, you may be making them as root which would give them access only.

You could add a user with smbpasswd -a and change the smb.conf to only allow you access to that share, but before I get into that, will you post this command on the machine hosting the samba shares.
```
sudo cat /etc/samba/smb.conf | tail 
```

You might not be giving yourself enough permission from the defined share.

	force user = mythtv
	force group = mythtv
;	browseable = yes


[Mediapc-Home]
	path = /home/mediapc
	writeable = yes
;	browseable = yes
	guest ok = yes
	comment = Mediapc-Home

---

### Post by jonnybignote on 2014-01-26
> **Morbius1 said:**
> In order to answer the question the folks here need to know how you are set up. If you post the output of these commands it will tell them that:
```
testparm -s
```
```
net usershare info --long
```
Don't be surprised if you get no output from the second command. It's a "just in case".

mediapc@MediaPC-Backend:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[recordings]"
Processing section "[videos]"
Processing section "[music]"
Processing section "[pictures]"
Processing section "[Mediapc-Home]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = LAN
	server string = %h server (Samba, Mythbuntu)
	username map = /etc/samba/smbusers
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb


[recordings]
	comment = TV Recordings
	path = /mythtv/recordings
	force user = nobody
	force group = nogroup
	create mask = 0777
	directory mask = 0777
	guest ok = Yes


[videos]
	comment = Videos
	path = /mythtv/videos
	force user = mythtv
	force group = mythtv
	read only = No
	create mask = 0660
	directory mask = 0770
	guest ok = Yes


[music]
	comment = Music
	path = /mythtv/music
	force user = mythtv
	force group = mythtv
	read only = No
	create mask = 0660
	directory mask = 0770
	guest ok = Yes


[pictures]
	comment = Pictures
	path = /mythtv/pictures
	force user = mythtv
	force group = mythtv
	read only = No
	create mask = 0660
	directory mask = 0770
	guest ok = Yes


[Mediapc-Home]
	comment = Mediapc-Home
	path = /home/mediapc
	read only = No
	guest ok = Yes

---

### Post by tfrue on 2014-01-27
is the {Mediapc-Home] a share yo defined? If so, you have disabled *browseable* so you cannot browse through the share from a computer trying to access it.

You should change the share definition to look more like:
```

[Share]
comment= my new share
path= path/to/directory
read only= no
guest ok= yes
browseable= yes
writeable= yes

```
We can set up more security if you want, just let me know and I will help you with that too!

If that doesn't help you, then post the output of:
```
cat /etc/samba/smb.conf
```

---

### Post by Morbius1 on 2014-01-27
***** I'm not sure why you deviated from the default smb.conf but there is one thing I would recommend putting back in smb.conf:

Place the following line - under the workgroup line:
```
map to guest = Bad User
```
Without it samba defaults to "map to guest = Never" - at least for some clients.
Then restart samba:
```
sudo service smbd restart
```

***** The rest of it may just be a permissions problem of what is being shared.

Run the following command to see what the permissions are and who owns the folders:
```
ls -al /mythtv
```
All of your shares allow guest access and all but one of them have a "force user" in them so the permissions of each folder either has to be 777 or owned by the user specified by the "force user" line. So for example the [recordings] share either has to have permissions of drwxrwxrwx or is owned by "nobody".

If not make it so by either setting permissions to 777:
```
sudo chmod 777 /mythtv/recordings
```
[COLOR=#0000cd]**OR**[/COLOR], leave the permissions where they are and set ownership to the "force user" user:
```
sudo chown nobody /mythtv/recordings
```
 
The way you have this set up all files added to the [recordings]  share will be owned by "nobody" because of the "force user" so as long as all files added are happening through samba this is good to go. If however you are adding or moving files into /mythtv/recordings locally - outside of samba - then there may be an issue here since they will not be owned by "nobody". [COLOR=#0000cd][I]Is this the case?
[/I][/COLOR]
If so we need to do something else.

***** Are you sure you want your home folder to be guest writeable?
> [Mediapc-Home]
comment = Mediapc-Home
path = /home/mediapc
read only = No
guest ok = Yes 

If you set /home/mediapc to 777 that will make it so anyone can write to the folder but it won't help them edit any of it's contents since everything will be owned by "mediapc". If you want the ability to access the folder and edit it's contents do to this what you did to the others:
> [Mediapc-Home]
comment = Mediapc-Home
path = /home/mediapc
read only = No
**[COLOR=#0000cd]force user = mediapc[/COLOR]**
guest ok = Yes 

[COLOR=#0000cd]*Side note: this statement is inaccurate:*[/COLOR]
>                           is the {Mediapc-Home] a share yo defined? If so, you have disabled *browseable* so you cannot browse through the share from a computer trying to access it.
All shares are browseable by default and can only be disabled by explicitly stating so in the share definition with a "browseable = no". You can add it back in if you want - or remove the leading ";" in the line - but it won't make any difference. The system will likely just add the ";" back then next time samba runs. Either way testparm won't print anything that is a default.

---

### Post by jonnybignote on 2014-02-01
Sorry for the delay, and thanks everyone for the help - it is much appreciated.

I have implemented the changes, so we shall see what happens.  

The issue is that I'm aware the permissions aren't right, and I do keep correcting them to allow the smb file transfers to take place.  I'm confused though as to why the permissions seem to be resetting themselves in time, to the point that I again can't transfer files.

I have made the permissions and ownership on the video and music folders to be the same as all the others - maybe that will do it.

Thanks again.

---

### Post by jonnybignote on 2014-02-05
So looking again 3 days later and ownership has been changed to root:root

Confused.  I didn't do anything  - is there anything automated in Mythbuntu or mythtv that could do that?

Thanks

---

### Post by jonnybignote on 2014-02-19
Help!

Still in the same boat here.

To reiterate; via samba, I can browse, open folders and files, but I cannot copy files to the machine, or create new folders.  I don't understand what kind of script or operation would be happening to do this.  The two folders Videos and Music are changed to 'root' while others remain the same.  Everytime I want to copy new files to the machine, I have to (via ssh) login and change ownership, and permissions.

Let me know if more logs are needed.

Thanks in advance for the help.

---

### Post by newlinux on 2014-02-20
I've only scanned this thread, so sorry if I repeat a question you've answered. What do the permissions (ownership and read write execute) look like after they change and what do you change them to?  When you say they've changed to root is that from the perspective of the client machine or the machine actually hosting the share or both

I don't know of any job in a standard ubuntu install that would cause this. Does the access or modification time on your file change when the permissions seem to revert? Do you modify the permissions from the machine that hosts the files via Samba or from the client machine that needs access to the files?

Unfortunately I don't use Macs very often but how do you actually access the file via the Mac? What options do you use to connect to the samba share? I know that in linux how you mount the share can make a difference in access permissions.

---

