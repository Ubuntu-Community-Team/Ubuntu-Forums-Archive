---
title: "Import from Samba to Media Players"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by JoshuaRL on 2009-01-09
My plan is to have a server set up with Samba so that all 5 computers can access the shares.  It will primarily be for music, and my hope is that we can have storage there, and save space on each individual drive.  So far I have set up Samba on the server, and connected three Windows computers to it.  Now, I want to try to connect my Ubuntu laptop especially, since that will save me a lot of space.  And being able to access my music library is the whole idea.

I am connected to the Samba shares through Places->Network.  But when I try to load a music application with the share as the music folder, nothing works.  Not even basic playback, let alone building my library.  I have tried Rhythmbox, Banshee, Exaile, and Songbird.  VLC seems to work just fine, but I'm not really wanting to use that as my music application.

I get an error out of Rythmbox when I go to Music->Import Folder:
```

Could not open resource for reading.

```

Any ideas?

---

### Post by JoshuaRL on 2009-01-16
Well, figured out my problem.  Not sure why it wouldn't work the normal way, but I used smb4k.  It's a KDE app, and from what I see it mounts shares under
```

~/username/smb4k/sharename

```
So now all my music apps see it when smb4k is running.  Nice.

---

### Post by Zack McCool on 2009-01-16
It didn't work the other way because the app was not aware of the "mount".  The better solution, IMO, would be to edit fstab and put in a manual mount to the share.  This will work with all apps.

---

### Post by wjp.reg on 2009-01-16
> **Zack McCool said:**
> It didn't work the other way because the app was not aware of the "mount".  The better solution, IMO, would be to edit fstab and put in a manual mount to the share.  This will work with all apps.

Pardon me for jumping in, but can you give an example of how to set up the  mount in fstab.

Thanks

---

### Post by Zack McCool on 2009-01-16
Sure...

First, set up a mount point in your filesystem:
```

sudo mkdir /mnt/music

```

Or whatever you want to call it...

Now, this part will require close attention.  First, I like to use smbfs, so make sure it is installed:

```
 sudo apt-get install smbfs 
```

Then, edit fstab: ```
sudo nano /etc/fstab 
```

And add something like this:
```

//192.168.0.100/music /mnt/music   smbfs   auto,rw,credentials=/etc/credentials.cred,iocharset=utf8,uid=1000,gid=1000,file_mode=0777,dir_mode=0777 0 0

```

Where 192.168.0.100 is the ip of the windows (or samba) machine sharing the files, 
music is the name of the share on that machine, 
/mnt/music is your local mountpoint
/etc/credentials.cred is the name of a file on the local machine that has the username and password needed to access the share:
```
sudo nano /etc/credentials.cred

should look like this: [code]username
password 
```
then set it to owner root and strict permissions:
```
sudo chown root:root /etc/credentials.cred
sudo chmod 600 /etc/credentials.cred 
``` [/code]

After that's set up, you should be able to mount it by issuing ```
 sudo mount /mnt/music 
``` And it should also automatically mount when you reboot.

I did that pretty much from memory, but it should be right.  If you have any questions, do not hesitate to ask...

---

### Post by wjp.reg on 2009-01-16
Hi Zack;

I would thank you for your post but I don't get a button to do so 'cause I'm not the one that started this thread.  I'll try out your remedy later today.

A BIG thanks :popcorn:

---

### Post by JoshuaRL on 2009-01-16
> **Zack McCool said:**
> 
After that's set up, you should be able to mount it by issuing ```
 sudo mount /mnt/music 
``` And it should also automatically mount when you reboot.


Thanks, thats great.  I'm just getting into fstab myself, so I thank you for your help.

> **wjp.reg said:**
> Hi Zack;

I would thank you for your post but I don't get a button to do so 'cause I'm not the one that started this thread.  I'll try out your remedy later today.

A BIG thanks :popcorn:

Normally the thanks feature should work for everyone.  But with the forum issues lately, it was turned off in favor of more stability.  But there's new hardware on the way, so things should be getting better soon.

---

