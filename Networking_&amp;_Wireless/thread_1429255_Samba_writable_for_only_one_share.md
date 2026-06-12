---
title: "Samba writable for only one share"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by moldiver on 2010-03-13
Hello,  I've searched the forums and try many things but nothing has worked.  Any help would be greatly appreciated.

I have a Ubuntu server sharing out 5 shares.  All 5 are readable and browseable on all of the windows clients I have.  This is all on an internal network.  However only one of them is writable (share3) even though they all have the same permissions.  I want to be able to get all 5 writable.  When I try to create a file in the 4 other shares I get a Windows popup saying permission denied.


Here is my /etc/samba/smb.conf
```
[global]
workgroup = HOME
server string = %h server (Samba, Ubuntu)
name resolve order = bcast host lmhosts wins
preferred master = yes
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False

log file = /var/log/samba/log.%m
syslog = 0

security = user
encrypt passwords = true
map to guest = bad user
guest account = nobody
read only = no
writable = yes
browsable = yes
create mask = 0755
directory mask = 0755
guest ok = yes

[share1]
	comment = Share1
	path = /media/truecrypt2/share1

[share2]
	comment = Share2
	path = /media/truecrypt2/share2

[share3]
	comment = Share3
	path = /media/truecrypt2/share3
etc....
```

Here is the output of # ls -als /media/truecrypt2
```
total 216
 4 drwxrwx--- 1 matt matt  4096 2010-02-18 10:07 .
 4 drwxr-xr-x 7 root root  4096 2010-03-13 20:21 ..
12 drwxrwx--- 1 matt matt 12288 2010-03-08 21:39 share1
44 drwxrwx--- 1 matt matt 45056 2010-03-13 13:46 share2
 4 drwxrwx--- 1 matt matt  4096 2010-03-13 17:54 share3
16 drwxrwx--- 1 matt matt 16384 2010-03-13 13:26 share4
16 drwxrwx--- 1 matt matt 16384 2009-05-02 09:12 share5
```

I've tried making the permissions on the shares 777, it doesn't change anything.

Here is the output of the # ls -als /var/log/samba/log.client
```
[2010/03/13 20:38:28,  1] smbd/service.c:1047(make_connection_snum)
  client (192.168.1.5) connect to service share1 initially as user matt (uid=1000, gid=1000) (pid 3575)
[2010/03/13 20:38:28,  1] smbd/service.c:1047(make_connection_snum)
  client (192.168.1.5) connect to service share3 initially as user matt (uid=1000, gid=1000) (pid 3575)
```

Here is the output of # smbclient -L 192.168.1.4
```
smbclient -L 192.168.1.4
Enter matts's password: 
Domain=[HOME] OS=[Unix] Server=[Samba 3.4.0]

	Sharename       Type      Comment
	---------       ----      -------
	share1          Disk      Share1
	share2          Disk      Share2
	share3          Disk      Share3
	share4          Disk      Share4
	share5          Disk      Share5
```

Thanks ahead of time.

---

### Post by dmizer on 2010-03-14
These two options are mutually exclusive:
security = user
guest ok = yes

Either add accounts to your server for each computer which will be using the server and remove the "guest ok = yes" option, or change "security = user" to "security = share".

---

### Post by moldiver on 2010-03-14
Oops,  I've edited the smb.conf so many times the past couple days,  I missed that error.  Thanks dmizer.  I deleted the "guest ok = yes" line; however, I still can't write to all my shares.

---

### Post by Morbius1 on 2010-03-14
(1) > These two options are mutually exclusive:
security = user
guest ok = yesThat statement is 100% incorrect.

(2) You could use security = share but it hasn't been used since Ronald Regan was president.

(3) > usershare owner only = FalseThis one has me a little confused ( well, more confused than normal for me ;) ). You say you have Ubuntu Server but that option is for Nautilus-share. By setting it to false it allows a user to share a folder using Nautilus for folders he does not own. Please post the output of the following commands:
**net usershare info**
**sudo net usershare indo**

It's possible that you have nautilus-share settings that are in conflict with classic-share settings.

(4) Having said all that the thing that has me really confused is this:
> 12 drwxrwx--- 1 matt matt 12288 2010-03-08 21:39 share1
44 drwxrwx--- 1 matt matt 45056 2010-03-13 13:46 share2
 4 drwxrwx--- 1 matt matt  4096 2010-03-13 17:54 share3
16 drwxrwx--- 1 matt matt 16384 2010-03-13 13:26 share4
16 drwxrwx--- 1 matt matt 16384 2009-05-02 09:12 share5I'll keep looking at your smb.conf because there is obviously something I'm missing because none of those should be accessible by a remote guest. If the remote user's windows login name was matt it would be possible but you would have had to set up an smbpasswd for matt. Right now from a linux perspective the only person that can read or write to those shares are local user matt.

[COLOR=Blue]EDIT: Try this for something off the wall. Add the following line to say the share definition for [share1][/COLOR]
> force user = matt
Restart samba and see if the remote user can read and write to that share.

---

### Post by dmizer on 2010-03-14
> **Morbius1 said:**
> (1) That statement is 100% incorrect.

Not when both options appear in the global section of smb.conf

---

### Post by moldiver on 2010-03-14
I should clarify the shares are not accessible by guest users.  They are accessible only with the user matt.  I did create a smbpasswd for matt. 

I think you are right morbius1, there is a conflict with the nautilus share.  

sudo net usershare info outputs nothing 

net usershare info outputs 
```
[share3]
path=/media/truecrypt2/share3
comment=
usershare_acl=Everyone:F,
guest_ok=n
```

Odd cause when I browse using nautilus /media/truecrypt2/share3 and look at the Properties -> Share, nothing is checked. 

So I then try to go to /var/lib/samba/usershares and copy and paste the share3 file for the other shares but that doesn't work. (I edited the files to point to the correct path).  Here is what the files show.
```
#VERSION 2
path=/media/truecrypt2/share3
comment=
usershare_acl=S-1-1-0:F
guest_ok=n

```

I also try the force user = matt and restarted samba and nothing changed. Thanks.

---

### Post by Morbius1 on 2010-03-14
Confused again :)

You've got **guest_ok=n **in Nautilus-share and **guest ok = yes** as a global variable in smb.conf. I would choose one method or the other to avoid this type of thing. Since your needs are really somewhat simple I would choose the Nautilus-share method but that's up to you.

This is what I would do if it where my system ( for whatever that's worth ).

I would return your smb.conf file to it's original state by making the adjustments marked in blue:
> [global]
workgroup = HOME
server string = %h server (Samba, Ubuntu)
name resolve order = bcast host lmhosts wins
preferred master = yes
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False

log file = /var/log/samba/log.%m
syslog = 0

security = user
[COLOR=Blue]force user = matt[/COLOR]
encrypt passwords = true
map to guest = bad user
guest account = nobody
[COLOR=Blue] #read only = no[/COLOR]
[COLOR=Blue]#writable = yes
#browsable = yes
#create mask = 0755
#directory mask = 0755
#guest ok = yes[/COLOR]

[COLOR=Blue]#[share1]
#    comment = Share1
#    path = /media/truecrypt2/share1

#[share2]
#    comment = Share2
#    path = /media/truecrypt2/share2

#[share3]
#    comment = Share3
#    path = /media/truecrypt2/share3[/COLOR]
> So I then try to go to /var/lib/samba/usershares and copy and paste the share3 file for the other shares but that doesn't work (I edited the files to point to the correct path). Here is what the files show.You would think that would work but it doesn't. It's best to go through nautilus itself to do this sort of thing because the last part of the nautilus-share process is that it will change permissions on the target to accommodate the the selections you made.. I would go into /var/lib/samba/usershares and just delete the entries and start over again though Nautilus.

Then restart samba and [-o<

---

### Post by moldiver on 2010-03-14
Ok weird.

I made all the changes in blue and restarted samba.
I also deleted all the entries in /var/lib/samba/usershares.

I go into Nautilus and manually share out all my entries.

I go to a Windows client and now share1 is writable (though it didn't prompt me for a password).  However shares 2-5 are getting the same permission error I was getting before.  It looks like I'm restricted to only one share being writable, odd.

[COLOR="RoyalBlue"]Edit: Nevermind, after a reboot of the Ubuntu box, everything seems to work as it should now.  All the shares are now writable.   Thanks for the help.[/COLOR]

---

