---
title: "Samba - Can't write to directories"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by altirisx on 2013-04-06
Alright so I creted a directory called "SharedData" in /usr/SharedData as the "root" user and then set the Owner to my name "shane" and put Folder Access to "Create and Delete Files" and I set the same thing for "Group" also. When I connect on a Windows 7 PC I can login and I see the "SharedFolder" folder and I can access it however when I try putting something in such as creating a folder it says I don't have perssmions. It seems that Samba is letting me only read the folder.

How do I fix this? My permissions are all set accordingly, here is a part that I edited in my my smb.conf

[SharedData]
    comment = Shared folder for everyone
    path = /usr/SharedData
    browseable = yes
    writable = yes
    valid users = shane

---

### Post by ahallubuntu on 2013-04-06
~

---

### Post by altirisx on 2013-04-06
Okay I ran that and I didn't get any permission denied errors so its something with Samba?

---

### Post by ahallubuntu on 2013-04-06
~

---

### Post by altirisx on 2013-04-06
I dont really understand what you mean by "share" if what you mean by "share" is the folder I made named SharedData then yes.

---

### Post by SeijiSensei on 2013-04-06
But when you log in to Samba are you using the directory's owner?

The easiest solution to this is to add 

```

force user = shane
force group = shane

```

to the share's definition.  That will write all files with user and group shane.  In a multi-user situation, you only want to take this approach if you don't care about auditing the files people place in this directory.  If you need to know that user "sue" has written a file, then you need to work harder on creating the right users and groups.

You might prefer to create a separate user and group just for the share and preserve your own username for your home directory.

---

### Post by altirisx on 2013-04-06
Alright so I just realized non-root users cant even write to the /usr folder lol so here is what I have done. (As a note this is only intended for my personal use) I created a folder in my /home/shane directory called "Shared" I read in the smb.conf file that to share a directory that Ive made and make it writable I need to type the command "chcon -t samba_share_t /PATHTOFOLDERHERE" I replaced PATHROFOLDERHERE with /home/shane/Shared. So now I tried logging in again and it worked!!!

So basically for anyone else who needs help, the best place IMO to use Samba is to make a folder named "Shared" on the root of a user (example: /home/bob/Shared) and then use the command "chcon -t samba_share_t /home/bob/Shared"  (REPLACE /home/bob/Shared with your actual profile path). Its also best to make that folder while logged in as that account (not root or anyone else just to be sure). You can then add this as in your smb.conf

[Shane Home]
    comment = Shane's Home Directory
    path = /home/shane/Shared
    browseable = yes
    writable = yes
    valid users = shane

(Replace Shane with your name) :D

---

### Post by ahallubuntu on 2013-04-06
~

---

### Post by bab1 on 2013-04-06
> **ahallubuntu said:**
> ...

Still, /usr probably isn't the "proper" place to put a share, anyway, and not an ideal place to put any folder users will write to, even if you CAN.   /home/USER/some-share-folder is fine.  There's not necessarily a "right" place to create share folders.  Sometimes I create a folder at root level called /shares and put share folders in there.

The */usr* directory is for [COLOR="#FF00FF"]U[/COLOR]nix [COLOR="#FF00FF"]S[/COLOR]ystem [COLOR="#FF00FF"]R[/COLOR]esources.  These are considered OS tools not personal data or users scripts.  You are better off creating a */data* directory or using */srv* to store data.  This would be away from the system binaries.

---

### Post by Morbius1 on 2013-04-07
> **altirisx said:**
> So basically for anyone else who needs help, the best place IMO to use Samba is to make a folder named "Shared" on the root of a user (example: /home/bob/Shared) and then use the command "chcon -t samba_share_t /home/bob/Shared"  (REPLACE /home/bob/Shared with your actual profile path). Its also best to make that folder while logged in as that account (not root or anyone else just to be sure). You can then add this as in your smb.conf

[Shane Home]
    comment = Shane's Home Directory
    path = /home/shane/Shared
    browseable = yes
    writable = yes
    valid users = shane

(Replace Shane with your name) :D
If you created a subfolder called "Shared" as "shane" in shane's home directory and then restricted access to that samba share only to "shane" then no modification to permissions is required because that remote user has become "shane".

The only reason I bring this up is because you posted the chcon step as an absolute necessary requirement and that is not true and only makes Samba more confusing to some users.

---

### Post by SeijiSensei on 2013-04-07
As I said earlier, in situations where I want to create a shared folder, I create a user to own the share and export /home/shareuser or some directory below that.  Then you either use the "force" commands to write everything as shareuser, or put all the people who will be writing files there in the shareuser group and give the group write privileges.

---

