---
title: "Different permissions with Samba shares."
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-10-20
I'm questioning the masks here with samba.

I have 4 shares.

1 is mine, 3 are other users.

I want the other 3 shares to be 775 mask, and I have that set globally in the smb.conf.

But my share links to my home directory, which has 644 permissions by default due to the nature of linux.

If I add force mask - 644 to MY SHARE ONLY, will it apply to only my share and allow the other shares to still retain their default 775 mask? Or do I need to add force mask 644 to mine + force mask 775 to every other share?

EDIT - another question, but this time about ownership. Currently is a user logs in their samba share and creates a file, it gets owned by themselves, for example fred:fred. Now, that's okay, because jason (myself, owner of the samba server) is a member of the group fred, and currently all other users get the mask and directory mask of 775, so owner + group have full reign. And since I'm a member of the group fred, I have full reign of the files despite me not being the immediate owner.

Okay, fine.

But what if I want ALL files written by ANY user to be owned by jason. I know I can use force group (and I do indeed use it in my smb.conf) to force a group to the files/folders that get written. But can it be set so anything written to the server is owned by a particular owner? Can I set it to is fred writes a file, that file is thereby owned by jason? Of course, Fred wouldn't know the difference, since he'd have group permissions to the file - but I'm curious if it's possible to auto-own it.

---

### Post by uncle-c on 2009-10-20
You can place the lines **force user = xxxx** and ** force group = %U ** into the specific shares' section. This will result in any file which is created having owner xxxx and group the person who logged into the samba share. i.e. 
if force user = jason and the samba user jack logs in, any file created in the share will have file owner jason and group owner jack.

If you want to be absolute about group  than just use 
** force group = zzzz ** , where zzzz is the group owner you so desire

Even if a guest has access to a particular share and no password is requested, any file created will have owner as jason and group as "nobody" or whoever the guest account is mapped to.

---

### Post by Roasted on 2009-10-20
so on each share if I put force group = fred, force user = jason, then jason:fred will own ALL files created on the samba share regardless of what user it is that is logged in to the samba share, and on top of that bring down the mask/directory mask permissions of 775 on everything?

---

### Post by uncle-c on 2009-10-20
Yes, provided that in the "shares" section you have a line which sets the 775 mask. But make sure that this does not conflict with the permissions of the actual /home/shares directory, i.e if the directory has permissions 700 and you try to create a mask of 775 you may not get the desired result depending on what user you are. Directory permissions will always take precedence.

---

### Post by Roasted on 2009-10-20
What's the ideal setup like? I keep experimenting with different things and I'm not sure what the best setup would be or if I'm just creating more work for myself.

Currently, I use samba as a backup server, using Windows software on other family members machines to back their my docs up to their shares on my server at 4 am every day.

Up until now, I've always let them have 775 permissions on the share. That way, the files are accessible to "all users" but can't be tampered with. That also gives me permission, because the files come down as owned by bob:bob, since bob is the one who creates the files on his share on my computer. Then I just add myself to the group bob so I can access the files on my local machine for whatever reason.

I guess there's no real need for me to force file ownership to myself, because I don't need to own the files. I just need to access them if need be. For example my mother was looking for a file on her pc and couldn't find it. So I searched her share on my pc and found it and I told her the path. Bingo. Found it. All because I could access the backup of her stuff.

What are your thoughts, folks? Do I have a good thing going on or is there more I can do to make it more secure or more user friendly?

---

### Post by uncle-c on 2009-10-21
I'm no real expert on Samba but if I did have several users I would change the permissions to 770 so users could not read each others files - just for privacies sake. I would go along with your idea as not to force user to yourself but to the file creator and maybe create a group "sambadmin" and  force group ownership to it. You can add yourself to the group and in that way a combination of permissions 770 , user "son", group "sambadmin", only son and sambadmin  will have the ability to rwx the files and mum, daughter, gran won't be able to access the file at all.

Lastly, on the backup note, I think most people would say use rsync; it's a very versatile and flexible command for backup.

---

### Post by Roasted on 2009-10-21
> **uncle-c said:**
> I'm no real expert on Samba but if I did have several users I would change the permissions to 770 so users could not read each others files - just for privacies sake. I would go along with your idea as not to force user to yourself but to the file creator and maybe create a group "sambadmin" and  force group ownership to it. You can add yourself to the group and in that way a combination of permissions 770 , user "son", group "sambadmin", only son and sambadmin  will have the ability to rwx the files and mum, daughter, gran won't be able to access the file at all.

Lastly, on the backup note, I think most people would say use rsync; it's a very versatile and flexible command for backup.

I use both, actually. The other machines are Windows boxes, so I'm not sure how they could rsync to my Ubuntu machine from within Windows. But I have a 3rd party free app called Syncback SE, which synchronizes their my docs on a schedule to their share paths.

That's to my primary 250gb drive, which I refer to as my network drive since that's what samba is linked to. I have a second 250gb drive, that I rsync the data to each day as well... so I constantly have 2 backups of everybody's data.

The only catch with my backup drive is, I don't run rsync as root, so it doesn't retain the owner of the files and actually changes the owner to me since I'm the one handling the files and "creating" them on the 2nd drive. However, that's not a big deal. If I ever have my main network drive go down and I need to bring the backup over, the data will come through as jason:fred instead of fred:fred. Well, jason + fred are still a member of the group fred, so the user won't notice anything anyway. A few quick commands and all of the data would be re-owned by the proper user.

Damn, I love linux. :guitar:

---

### Post by uncle-c on 2009-10-22
Just a quick final note, if you do use ** force group = zzzz **, when a user logs into the share he takes on the privileges associated with that group, this could mean rwx permissions, hence user ** force user | group = xxxx ** does have plenty of security risks associated with it. The way round the ** group ** issue is to ** chmod g+s *directory* **, if this directory is owned by group ** family ** then any file created in this directory will also be in the group ** family **.

---

### Post by Roasted on 2009-10-22
> **uncle-c said:**
> Just a quick final note, if you do use ** force group = zzzz **, when a user logs into the share he takes on the privileges associated with that group, this could mean rwx permissions, hence user ** force user | group = xxxx ** does have plenty of security risks associated with it. The way round the ** group ** issue is to ** chmod g+s *directory* **, if this directory is owned by group ** family ** then any file created in this directory will also be in the group ** family **.

Hm, is this what you mean? Not sure if my example lines up with yours or not...

*Everything is 775 permissions*

/media/storage = jason:smbusers
Members of smbusers = jason, fred, bob, dave

/media/storage/fred = jason:fred
Everything inside /media/storage/fred = fred:fred

jason + fred (users) are a member of the group "fred".

That means:

- All users are in smbusers group.
- All users can access the storage share where samba folders are.
- All users own their data, while the shares are owned by jason, with the users getting access to their share folders via group access.
- Jason, however, can access all data - being a member of each user group.

Is there a limitation to how many groups 1 user can be in?

---

### Post by uncle-c on 2009-10-22
Looks good.
What I was getting at was that you do not need to use ** force group = smbusers ** in the [COLOR="Blue"]smb.conf[/COLOR] file to make files inherit group **smbuser** ownership when they are created. You can use  ** sudo chmod g+s ** on the smbuser directory. It is generally regarded as a less risky option. Obviously any file created in the /media/storage directory will be group smbuser and hence rwx by all smbusers. Any files created in /media/storage/fred should be fred:fred. But one thing which you may deem important. If /media/storage/fred has permissions 775 then any user will be able to access that directory and  ( ls ) list, and thus see, all the files contained within the directory i.e. bob will be able to see all of fred's files. If the files within /media/storage/fred also have permissions 775 then bob will also be able to read freds files. If you want privacy you could create a mask for the share so any directory or file created has 770 permissions.

You can be in as many groups as you like !

---

### Post by Roasted on 2009-10-22
I understand that 775 permissions means that Bob can see Fred's documents, etc. But that's only on my local machine, which nobody logs into but me. On the samba side of things, each share is password protected. So if Bob goes start - run - \\area51, he can see the shares. At this point, if he clicks Bob, he has access. If he clicks Dave, it prompts him for Dave's password.

---

### Post by uncle-c on 2009-10-22
Hmm very interesting. I have a similar setup but if I click on another share folder it does not ask me for a password but just gives a warning message that I have no access. See attachment. All interesting nonetheless !

---

### Post by Roasted on 2009-10-22
Actually, I'd rather have that error message. Can you post the shares section of your smb.conf? Do you have a "denied users" section listed? All I have is "valid users" for each share.

---

### Post by uncle-c on 2009-10-22
On my samba server I have the following directory: /path/to/directory/share 
This directory has many files which all users can access, howeve,r it also contains a specific directory called "music". This directory is owned by unclec and group owner is "music". Its permissions are 770.

[B]1./path/to/directory/share : permissions 770 root:share # group share have rwx access

2. /path/to/directory/share/music : permissions 770 unclec:music # unclec and group music have rwx[/B]

Notes:

There is a third user on my system called **video** who belongs to the "share" group

User music is member of group share but also a member of group music, so he has access to the ../share/music directory.

unclec is also member of group "share" so he has access to both 1. and 2. as group member and owner respectively.

The relevant section of the smb.conf file is oh so very simple :

```

[linux-share]

path= /path/to/directory/share

read only = no

 create mask = 0770
 force create mode = 0770

```

So when user video ( from windows ) does Start -> Run -> Open -> \\xxx.xxx.xxx.xxx\linux-share the file manager opens and video can see all the files in the share. If, however, he clicks on the "music" directory he get the warning window pop-up which says he has no access rights and does not get asked for username / passwd to access the said directory.

The smb.conf file can get you easily muddled if there are too many lines in there controlling permissions and users, so I've tried to control things at directory / file level on the server.

---

