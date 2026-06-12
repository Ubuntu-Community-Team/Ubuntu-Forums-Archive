---
title: "Ubuntu Shared Folder"
date: 2013-11-22
forum: Multimedia Software
---

### Post by oozaru on 2013-11-22
Hi, I hope this is the right place to post this. On Windows there is a shared folder which all users have access to. I used to store music, videos and other files that way all users on the computer had access to them without install multiple files on the same hard drive. I was wondering if Ubuntu had a similar folder or if not how I could set one up like that.

Thanx

---

### Post by electrohandyman501 on 2013-11-22
I think it's possible. It comes down to the ownership properties for the folder you want to setup for sharing. 
I can't say that I'm fluent with the Linux file system as yet, I'm still learning too, but it's way different that how Windows controls file/directory access. 
The ownership would deal more with group ownership/rights and who's in the group for access.

Try reading here:[URL="http://linuxcommand.org/lc3_lts0090.php"] 
http://linuxcommand.org/lc3_lts0090.php[/URL]
It explaines the Linus permissions system.

---

### Post by Bucky Ball on 2013-11-23
If you have that folder already just access that from Ubuntu. 

Windows does not use EXT* filesystem. Doesn't know what it is. If you want to share between Win and Ubuntu you need to create (or use an existing) NTFS or FAT partition, which Ubuntu and Windows can read and write without issue.

I have a 15Gb partition called /Misc which is used for sharing.

That's it.

---

### Post by oozaru on 2013-11-23
> **Bucky Ball said:**
> If you have that folder already just access that from Ubuntu. 

Windows does not use EXT* filesystem. Doesn't know what it is. If you want to share between Win and Ubuntu you need to create (or use an existing) NTFS or FAT partition, which Ubuntu and Windows can read and write without issue.

I have a 15Gb partition called /Misc which is used for sharing.

That's it.

I was just using Windows as an example. I just need to share folders on the same computer, within a single ubuntu partition between 2 logins within that partition

---

### Post by Bucky Ball on 2013-11-23
> **oozaru said:**
> I just need to share folders on the same computer, within a single ubuntu partition between 2 logins within that partition

Oh. Aren't all users seeing the folders on the partition? Can you be more specific? You mean you want different users to be able to share folders on the same partition? 

You need to be more specific. How have you got these users set up that they can't see folders? ;)

---

### Post by Morbius1 on 2013-11-23
Like most things with Linux simple questions often result in complex answers - and in this case it all depends on what you mean by "shared"

Let's say you create a folder: /home/Shared

_The following configurations will allow multiple users to add to and delete from the shared folder._

This will allow all users to add to the folder:
```
sudo chmod 0777 /home/Shared
```
This will restrict it to only members of the plugdev group:
```
sudo chmod 0770 /home/Shared
sudo chown :plugdev
sudo gpasswd -a morbius plugdev
```
[COLOR=#0000cd]*The last command adds morbius to the plugdev group.*[/COLOR]

_If you want users to be able to do the above and also to edit the files contained within that shared folder things get a bit more complicated._

This will allow all users of the plugdev group add/delete access to the folder and edit access to any new files created in or copied to the folder:
```
sudo chmod 2770 /home/Shared
sudo chown :plugdev /home/Shared
```
[COLOR=#0000cd]*Note: What it will not do is affect any files **moved** to the shared folder. For that you need bindfs.*[/COLOR]

[COLOR=#0000cd]*Another Note*[/COLOR]: [COLOR=#0000cd][I]If you are using Ubuntu13.10 you will unfortunately have to make one correction to the system:
**EDIT: I had to edit this post since on a fresh install of 13.10 even this didn't work correctly. It looks like in 13.10 you will need to use bindfs if you want to edit the contents of a shared directory.**
[/I][/COLOR]
[COLOR=#0000cd]*Last Note*[/COLOR]: You can also add a "sticky bit" to these that will prevent one user from deleting a file owned by another which I can explain if desired.

---

### Post by oozaru on 2013-11-23
> Oh. Aren't all users seeing the folders on the partition? Can you be  more specific? You mean you want different users to be able to share  folders on the same partition? 

You need to be more specific. How have you got these users set up that they can't see folders?

Basically what I need is a single location where I can store music, videos, ebooks etc so that the library programs I use (Banshee for music & video, Calibre for ebooks) can access them on both my account and my wife's account so that we don't have multiple copies of files on the computer.

Also I wanna allow the Guest account to access them too through the library software, i.e. they can play the music or watch the videos but without being able to edit or delete the files. I would think that this would be default but I just wanted to check.

---

### Post by Morbius1 on 2013-11-23
Then everywhere I posted a "0770" make it a "0775"

The owner and everyone in the plugdev group can add and delete in the folder and edit the files within them but everyone else can only read the files.

---

### Post by oozaru on 2013-11-23
> **Morbius1 said:**
> Then everywhere I posted a "0770" make it a "0775"

The owner and everyone in the plugdev group can add and delete in the folder and edit the files within them but everyone else can only read the files.

ok, this might be a stupid question but what is the plugdev group?

---

### Post by oozaru on 2013-11-23
ok I know what it is now

---

### Post by Morbius1 on 2013-11-23
I just used a group that is already created and ready for use. Back in the before time all new users were members of the plugdev group by default. But now only the first user created is a member so you will have to add all the other users to that group.

As I recall it was created so users could access hot-**plug**gable devices - usb, cameras, etc....

[COLOR=#0000cd]EDIT[/COLOR]: oops, posted past each other.

---

### Post by oozaru on 2013-11-23
when I put sudo chown :plugdev into the terminal it says chown: missing operand after `:plugdev'

---

### Post by oozaru on 2013-11-23
also how do I enter code in it's own box like you did?... I didn't mean to put in those smileys

---

### Post by Morbius1 on 2013-11-23
You have to specify the path to the folder whose permissions you want to change;
```
sudo chown :plugdev /home/Shared
```

You put the code tags around things by highlighting what you want and select  "#" in the forum editor.

---

### Post by Morbius1 on 2013-11-23
Note: I had to make an edit to my original post concerning editing /etc/upstart-xsessions for Ubuntu 13.10. I just did this on a new system and even that workaround doesn't work reliably so either wait for the update if it ever comes, wait till the next release, or use bindfs if you want both users to be able to edit each others files.

---

### Post by oozaru on 2013-11-23
ok, I got the shared folder to work but now it won't allow access to the folder within it on my wife's profile... is there a way to set the same permissions for all the folders within the shared folder or do I need to run the code each time I create a folder in it?

---

### Post by Morbius1 on 2013-11-23
The other user doesn't have access to the subfolders of the share?

Can you post the output of this command becasue I don't understant how that's possible:
```
ls -al /home/Shared
```
I don't know what folder you are sharing so replace /home/Shared with it's real path.

And what version of Ubuntu are you using?

---

### Post by oozaru on 2013-11-23
```
drwxrwsr-x  18 root  plugdev 4096 Nov 23 16:08 .
drwxr-xr-x   5 root  root    4096 Nov 23 12:44 ..
drwxrwxr-x  20 blaze blaze   4096 Nov  5 14:01 Audiobooks
drwxrwxr-x   3 blaze blaze   4096 Nov 18 19:37 Backup Info
drwxrwxr-x   3 blaze blaze   4096 Nov  6 17:38 Bass Guitar
drwxrwxr-x  52 blaze blaze   4096 Nov 16 12:26 Books
drwxrwxr-x   2 blaze blaze   4096 Nov 15 12:38 Chord Sheets
drwxrwxr-x   3 blaze blaze   4096 Nov 12 17:57 Code
drwxrwxr-x   4 blaze blaze   4096 Nov 19 17:51 Compositions
drwxrwxr-x   2 blaze blaze   4096 Oct 24 17:40 Drums
drwxrwxr-x   2 blaze blaze   4096 Nov 14 14:16 Lead Sheets
drwxrwxr-x   2 blaze blaze   4096 Nov  6 15:23 Miranda
drwx------ 116 blaze blaze   4096 Nov 23 14:19 Music
drwxrwxr-x   2 blaze blaze   4096 Sep 23 15:29 Pictures
drwxrwxr-x   3 blaze blaze   4096 Oct 11 13:22 Software
drwxrwxr-x   3 blaze blaze   4096 Oct 10 17:15 Ukulele
drwxrwxr-x   4 blaze blaze   4096 Oct 16 15:40 Videos
drwxrwxr-x   3 blaze blaze   4096 Nov 16 23:04 Websites
```

I'm using 12.04

---

### Post by Morbius1 on 2013-11-23
THe other user has access just not write access - I got it. You need to do a recursive chown to change all existing folders and files to have plugdev as group:
```
sudo chown -R :plugdev /home/Shared
```
EDIT: Have to shut down for the day so I'll check in again tomorrow.

---

### Post by Morbius1 on 2013-11-24
Let me try to clean this up a bit so that it looks more coherent. 

To share a directory using the standard method one creates a directory:
```
sudo mkdir /home/Shared
```
Then one changes the group of the folder - in this case to plugdev:
```
sudo chown :plugdev /home/Shared
```
Then one sets permissions to set the sgid bit so that all new files "inherit" that group and allow that group to write to the directory:
```
sudo chmod 2775 /home/Shared
```
Then one adds files/folders to that directory by either creating new files or copying over old files. [COLOR=#0000cd]A move to the directory will not work it has to be a copy[/COLOR].

From what I can tell from your post you instead did this on an existing directory or perhaps you moved files/folders to the new directory. In this case you will need to do 2 things to correct for permissions:

A recursive chown so all entries have plugdev as group:
```
sudo chown -R :plugdev /home/Shared
```
And then recursively setting the sgid bit on all existing subdirectories - but not files using this butt ugly expression:
```
find /home/Shared -type d -exec chmod g+s {} \;
```

Just remember that this works for all new files created in and any files copied to the folder - [COLOR=#0000cd]but not with files moved to the folder[/COLOR]. A move is not a copy-then-delete it's a change to the part of the file that specifies it's path so the sgid bit has no affect on it. [COLOR=#0000cd]If you do a lot of moving to this directory I would strongly suggest **bindfs**.[/COLOR]
[I][COLOR=#0000cd][B]
Also Note[/B][/COLOR][/I]: The standard method does not work properly in Ubuntu 13.10 [because umask is hopelessly broken]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686"). The bug was classified as "fixed released" and the bug report was for 13.10 specifically but the fix was made for [14.04 not 13.10]("https://launchpad.net/ubuntu/+source/upstart"). Will the fix be relased for 13.10? There really isn't any incentive by Ubuntu to do so but you may get lucky. Again, bindfs is my recommendation to circumvent this issue in 13.10.

---

### Post by oozaru on 2013-12-09
Ok, It can access all the folders except one /home/Shared/Music
 It keeps saying permission denied

---

### Post by Morbius1 on 2013-12-10
> drwx------ 116 blaze blaze   4096 Nov 23 14:19 Music
Mount point for an NTFS partition?

---

### Post by oozaru on 2013-12-11
> **Morbius1 said:**
> Mount point for an NTFS partition?

I don't understand

---

### Post by Morbius1 on 2013-12-12
>                                                          drwx------ 116 blaze blaze   4096 Nov 23 14:19 Music                      
It's very rare that a directory has permissions of 700 as that one does. If it's on a Linux filesystem then you changed it to that on purpose and I would suspect you'd remember doing it. You usually see those permissions on an NTFS filesystem so the chances were good that is was a mount point for that partition.

If you think it's a Linux partition then change permissions:
```
sudo chmod 2775 /home/Shared/Music
```
Then change ownership:
```
sudo chown -R :plugdev /home/Shared/Music
```
If at the end of this your permissions still look like this then the Music folder sits on an NTFS partition:
>                                                           drwx------ 116 blaze blaze   4096 Nov 23 14:19 Music                       

---

### Post by oozaru on 2014-01-05
Ok it worked, thank you for the help.
One more thing. I just learned about shell scripts, how would I organize this into a script in case I need to do a clean install?

---

