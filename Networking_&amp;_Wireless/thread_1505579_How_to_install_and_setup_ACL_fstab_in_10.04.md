---
title: "How to install and setup ACL fstab in 10.04"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by AfrikaDietmar on 2010-06-09
I have been trying to figure out since several days how to setup a network with protected folders. Until I found this video: 

[http://www.youtube.com/watch?v=F9aLvoH4-BQ](http://www.youtube.com/watch?v=F9aLvoH4-BQ)

with which i messed up my fstab, i think because its for an older ubuntu version.
On my other computer on which i'm testing i currently can't load Ubuntu anymore due to the change i made to fstab, mounting problem which i have addressed in another post.

Apart from that, all steps seemed the same in ubuntu 10.04.

Can someone please explain to me how I should set the fstab correctly in 10.04 to get ACL running ?

cheers, dietmar

---

### Post by AfrikaDietmar on 2010-06-10
anyone ?

---

### Post by Morbius1 on 2010-06-10
You've got posts in three different threads discussing this problem so I've decided to basically hijack this thread to respond. I viewed the youtube howto you referenced and I think you're making this far too complicated. There is absolutely no reason to use ACL to control who has access to a remote samba share. Samba has built in functionality to address this.

Please post the output of the following commands so we can see where you are:

```
net usershare info
sudo net usershare info
testparm -s
```

[COLOR=Blue]EDIT: And please tell us how you want to restrict access to those shares. Do you want to require a username and password to access all restricted shares? Or do you want user1 to have access to only one share and user2 to only have access to another. [/COLOR]

NOTE: Samba can inherently restrict who can access a given share. Depending on your requirements and what method of samba sharing ( Nautilus vs Classic ) it's either one click or adding things like this to control who has access:

One Example: 
```
valid users = jdoe
```

---

### Post by AfrikaDietmar on 2010-06-10
am still stuck on this one: [http://ubuntuforums.org/showthread.php?p=9439708#post9439708](http://ubuntuforums.org/showthread.php?p=9439708#post9439708)

once i can load my ubuntu from hard drive then the results will be more relevant i guess ?

---

### Post by AfrikaDietmar on 2010-06-10
Problem solved, i can boot my ubuntu again. 

> There is absolutely no reason to use ACL to control who has access to a  remote samba share. Samba has built in functionality to address this.
I didn't get any satisfactory results with ACL... But i learnt a good lesson about the FSTAB.

> [COLOR=Blue]And please tell us how you want to restrict access to  those shares. Do you want to require a username and password to access  all restricted shares? Or do you want user1 to have access to only one  share and user2 to only have access to another. [/COLOR]
There are 2 things i need to manage to do.
1. Restrict a main shared folder. That is simply password protect it. Whoever wants to access it in the network needs to input a password. In this way i protect my network.
2. If this is possible, inside the shared folder, add more folders, and some will be password protected for 1 specific user. In this way, not everybody can access this folder. 

Question, will it also work if someone is accessing it from windows ? So far i have no problem in sharing a folder with windows. But i just don't know how to password protect it. When in Samba I changed sharing into user, a password popup was seen in windows, but whenever i gave in a password, nothing happened.

So here are the results:

> net usershare info

```
info_fn: file /var/lib/samba/usershares/test1 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/test is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/tutu is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/networktest is not a well formed usershare file.
info_fn: Error was Path is not a directory.
```

> sudo net usershare info
testparm -s
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[IM-SERVER]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = IM-NETWORK1
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = im-003
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[IM-SERVER]
    path = /home/im-003/IM-SERVER
    read only = No

```


Hope this is useful. Catch up with you later.

---

### Post by Morbius1 on 2010-06-10
**First,** you need to clean up something:
```
gksu gedit /etc/samba/smb.conf

```Look for the following line:
> security = SHAREand place a # sign in front of them so it looks like this:
```
#security = SHARE

```Then restart samba:
```
sudo service smbd restart
```**Second,** Just to be clear of your requirements, you want to:

Create a restricted share
Restrict access to a given subdirectory of that share to one specific user

You would have to ask for one of the few examples where ACL's is the classic way to accomplish this. :p

Since ACL's didn't work out for you so well I suggest the following as an example.

I am going to create a directory that I want to share and a subdirectory that I will restrict access to only one user:
```
sudo mkdir /home/Shared
sudo mkdir /home/Shared/User1
```I'm going to set the permissions on those directories to enable samba to allow remote access:
```
sudo chmod 0777 /home/Shared
sudo chmod 0700 /home/Shared/User1

```I'm going to set ownership of the subdirectory to user1:
```
sudo chown user1 /home/Shared/User1
```Now I'm going to create a share for /home/Shared:
```
[Shared]
    path = /home/Shared
    inherit permissions = yes
    writeable = yes
    valid users = user1, user2, user3, user4
```This will allow user1/2/3/4 to access /home/Shared only after submitting a valid username and password.
Only user1 will be allowed access to /home/Shared/User1.

You will of course need to set up user1/2/3/4 on the server and also set up samba passwords for those users.

If you need it, the following procedure will create a user1/2/3/4 account on the server that have no local server login capabilities so they will only be used for samba purposes:
```
sudo useradd -s /bin/true user1
sudo smbpasswd -a user1
```The first command will create a local server user and the second will add AND enable a samba password for that user.

---

### Post by AfrikaDietmar on 2010-06-10
```
#security = SHARE
```

That did the trick for my shared folder to require password to access it.
(Thats a big step!)

I verified and my ACL is working.

I tried for several hours a lot of things. But it just doesn't want to accept me to password connect to another subfolder of the main shared folder. I always get the access denied message.

I have created 2 users with local server login who i have also created as samba users with password.

So its not possible then to have a sub folder in main shared folder password protected ? (i mean with a different password)

Else if its not possible to make a protected subfolder with a different password of a different user. How could i make another shared folder accessible with a different password work at root level ? I tried it, but it didn't work.

When i access the computer on a whole, as a server, where i have to input my password in the network to access it, it shows me the folders it has which are shared. And any of those, if password protected for a different user, dont work. Access denied message.

---

### Post by Morbius1 on 2010-06-10
Sorry didn't follow that at all.

You keep using the word password to describe how you're getting access. You need a username and password to access those shares.

If you want user1 to only access /home/Shared/User1 and nothing else in /home/Shared then it would be best to create another shared directory: /home/Shared2 and limit access to only user1. Just remember to set the linux permissions to enable samba to allow remote access.

---

### Post by AfrikaDietmar on 2010-06-11
> You keep using the word password to describe how you're getting access.  You need a username and password to access those shares.

Exactly. 

i have one shared folder here:
home/user1/shared1

And i tried the following 3 additional combinations:
1. Like this
home/user1/shared2

2. Like this
home/user1/shared1/shared2 (Where i assign shared2 to another owner)

3. Like this where i directly put the shared folder in another linux user folder
home/user2/shared1

I then access the workgroup, where i have to input a login and password.
Its like the global access.
Then i can see all folders which are shared. Wether its inside a folder or in home or in anothers users account. That is for instance above in user2. I believe because i use only one samba config file where i have inputed all details for all folders.


If I password protect shared2, or assign it to another user, when i click on it, computer says, access denied, or that i cannot make 2 connections.

even if i use this structure:
home/user1/shared1
home/user1/shared1/shared2 (Where i assign shared2 to another owner)
home/user2/shared1


You get my point ?

---

### Post by Morbius1 on 2010-06-11
That didn't help I'm afraid. There are just some things about your description that I'm not personally familiar with:
> I then access the workgroup, where i have to input a login and password.I'm not familiar with any configuration that requires authentication to access at a workgroup level. Perhaps if you had subnets, where part of a domain, or where using Active Directory then that would be true, but that's beyond me I'm afraid.
> Where i assign shared2 to another ownerDon't know what that means. You did a chown on shared2 and now you have shared2 owned by user2 located within shared1 which is owned by user1?
> If I password protect shared2"password protect"? You mean you encrypted shared2? Or do you mean you turned off guest access? 

When a remote user tries to access a share that requires authentication he will be asked for a username and password. From that point on that will be the only way the server will see him. If you're trying to require two different usernames and passwords in one session then that won't work.

If you're trying to access home/user1/shared1/shared2 such that all users will have to authenticate to gain access to shared1 and one among them will have exclusive access to shared2 then I would suggest my earlier post ( #6 ).

If you're trying to access home/user1/shared1/shared2 such that a remote user has access to shared2 but no access to shared1 then I would suggest you you make shared2 a separate share at the same level as shared1. So you would have two shares:

/home/user1/shared1
/home/user1/shared2

For shared1 you would have a share defined like this:
```
[shared1]
    path = /home/user1/shared1
    writeable = yes
    valid users = user1, user2, user4
```For shared2 you would have a share defined like this:
```
[shared2]
    path = /home/user1/shared2
    writeable = yes
    valid users = user3
```

---

### Post by AfrikaDietmar on 2010-06-11
> I'm not familiar with any configuration that requires authentication to  access at a workgroup level.

Ok, i might have expressed myself wrongly, lets see i can see the computer in the network when i click on workgroups, then i type in username and password and there i can see all folders which are shared. I can see

/home/user1/shared1
/home/user2/shared2

etc.

Ofcourse i can't see the subfolders.

If i have given this folder ownership to another user and require login and password 
/home/user2/shared2
after having logged into the computer through the network, this doesn't work.

hmm, that might be the problem:
> When a remote user tries to access a share that requires authentication  he will be asked for a username and password. From that point on that  will be the only way the server will see him. If you're trying to  require two different usernames and passwords in one session then that  won't work.

I want to login into share1, and then with a different username and password login into share2, i would be the only one to have access to share 2.

> "password protect"? You mean you encrypted shared2? Or do you mean you  turned off guest access? 


I right click on the folder, go on permissions and assign it to a particular user, i go on samba and assign it that same user. Or i do it directly in smb.conf

> If you're trying to access home/user1/shared1/shared2 such that all  users will have to authenticate to gain access to shared1 and one among  them will have exclusive access to shared2 then I would suggest my  earlier post ( #6 ).
That didn't work, it says access denied.

i input my username and password for folder /home/user1/shared1
and then folder which i have ownership home/user1/shared2 - cannot be accessed, there is a popup where i can input login and password, but then it says, it cannot make 2 connections or access denied...

---

### Post by Morbius1 on 2010-06-11
> I want to login into share1, and then with a different username and  password login into share2, i would be the only one to have access to  share 2.That cannot be done. If share2 is a subfolder of share1 then my post ( #6 ) will give you the same affect. When user2 supplies his username and password to gain access to share1 he will not have access to share2. If user1 supplies his username and password then he will have access to share1 and share2.

You have to make sure that share2 is owned by user1 and with the right permissions ( 0700 ).

---

### Post by AfrikaDietmar on 2010-06-11
Ok, i kind of get the logic.

I'll put it in my words, lets see if this makes sense and if did get the logic behind it.

There are 2 users:
user1
user2

Folder /home/shared is created

user1 and user2 are allowed to access shared.
Wether user1 or user2 input their login and password, they have access to the shared folder.

For user2, a folder will be attributed, to which only user2 has access.
Folder /home/shared/User2

When user2 logs in, he has access to shared and user2 folder.
Whern user1 logs in, he has access to shared but cannot access user2.

My way of thinking thought, user1 could then type in login details of user2 and then also have access to his folder. But thats where i was wrong, this would be the wrong methodology.

So, i guess I got it now! :) (...do I???)


On the other, i have been trying this for a bunch of hours. I have another problem, when i open SAMBA GUI, under SAMBA USERS User1 has transformed into nobody.
I removed him and tried to read User1 from the pulldown list, when i input the password, Samba says, User1 already exists. How to do i get things back in proper shape there ?

---

### Post by Morbius1 on 2010-06-11
First, I think you've got it.

Second, you didn't want to delete nobody. That's required for guest access to work.

Third, Don't use a samba GUI. Use the Terminal.

To create a samba password for a user account:
```
sudo smbpasswd -a user1
```Even if it already exists it will ask for a new password.

---

### Post by AfrikaDietmar on 2010-06-11
thats nice, that worked!

Thanks a lot! :)

---

### Post by AfrikaDietmar on 2010-06-14
Hi Morbius1,

i have a question concerning chown. Can you chown several users to one folder ?

I will have 5 Users.
The will all have access to the shared folder.
In the shared folder there will be folders that only certain users will have access to.

For example on 1 Folder, only User 1 will have access.
And on another Folder, Users 1,2 would have access.

So thats where i wonder if you can chown a folder for several folders.
Is there also an "unchown" function ? where you remover ownership and make it accessible to all again ?

It won't be necessary in smb.conf to input validity for each folder, that is who will have access to each subfolder if ownership is used right ?

You have explained how to add a samba user in this way:
sudo useradd -s /bin/true user1

How would you remove a samba user that has become obsolete ?
Is there a way you can also list all samba users ?

Well, a bunch of beginners questions... :confused:

---

### Post by Morbius1 on 2010-06-14
Wow, there are entire web pages devoted to most of those questions. Let's see how far I can get without making a mistake:
> You have explained how to add a samba user in this way:
sudo useradd -s /bin/true user1This was not adding a samba user. This was adding a local user on the server itself without creating a home directory or local sign on capability. To remove a local user the command would be :
```
sudo userdel user1
```> How would you remove a samba user that has become obsolete ?```
sudo smbpasswd -x user1
```> Is there a way you can also list all samba users ?```
sudo pdbedit -w -L
```> I will have 5 Users.
The will all have access to the shared folder.
In the shared folder there will be folders that only certain users will have access to.

For example on 1 Folder, only User 1 will have access.
And on another Folder, Users 1,2 would have access.To be honest I don't know if this will work or not if you've followed my  post #6. I'd have to test this out to see if it would actually work. But conceptually you could:

Create a new group: share1
```
sudo groupadd share1
```To delete a group:
```
groupdel share1
```Add user1 to that group:
```
sudo usermod -a -G share1 user1
```To remove a user from a group:
```
sudo deluser user1 share1
```Change ownership of the target directory to include the new group:
```
sudo chown user1:share1 /path-to-shared-folder
``` **[COLOR=Blue]But there is a far better way of doing this - don't have shares within shares. [/COLOR]**Instead of having a parent folder that everyone has access to and child folders that only some have access to, have separate independent stand alone shares:

/home/Shared/Share1 - to which valid users = user1, user2, user5
/home/Shared/Share2 - to which valid users = user1, user3, user4
/home/Shared/Share3 - to which valid users = user2, user5

This is far more manageable.

---

### Post by AfrikaDietmar on 2010-06-15
Hi Morbius1,

thanks a lot! I spent sometime last night reading about the various ways you can also configure the smb.conf, i found out that there is even a firewall called UFW (uncomplicated firewall; cool name!) which samba can use but its usually set on off. But we won't get into this.

 I also read that it says, its wise for security purposes to make the owner a user other than root. So, this would mean then, the user with which i log into the ubuntu server, i shouldn't use that one as samba user, and create extra users which will be used along the network i suppose. But i also read its for file attribution, you can for example include in smb.conf force user = johnny and all files in that share will always be attributed to him. You can still add valid users to the list.

> **[COLOR=Blue]But there is a far better way of doing this -  don't have shares within shares. [/COLOR]**Instead of having a parent  folder that everyone has access to and child folders that only some have  access to, have separate independent stand alone shares:

/home/Shared/Share1 - to which valid users = user1, user2, user5
/home/Shared/Share2 - to which valid users = user1, user3, user4
/home/Shared/Share3 - to which valid users = user2, user5

This is far more manageable.     That seems to make most sense.

I'm still wondering about chown though. Is it possible to make a folder have ownership to several users ? And how would you remove the ownership again ?
Ok, it looks like this is solved with groups, i'm still trying to comphrehend this.

Change ownership of the target directory to include the new group:
 	Code:
 	sudo chown user1:share1 /path-to-shared-folder 
For me to comphrehend: user1 is a user and share1 is the name of the group. Thus user1 is part of group share1.
If there were 5 users lets say, would i need to list them like this if i want to give them ownership on a folder (assuming i have already added them to the group): chown user1, user2, user3, user4, user5:share1 /path-to-shared-folder ?

---

