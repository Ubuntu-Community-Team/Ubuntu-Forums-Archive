---
title: "File sharing, Samba"
date: 2012-09-27
forum: Networking &amp; Wireless
---

### Post by ram0s on 2012-09-27
File sharing in Ubuntu is a living hell. So, I'll briefly explain the reason of my frustration:

I wanted to format my Ubuntu laptop to try another distro. Ok. That meant I had to backup files from the laptop I wanted to keep. Quite a few gigs.



It is not the first time I rage at this, some time ago I managed to share a folder from my Ubuntu laptop to my desktop pc, using guest account. So, I thought, to minimize frustration, I can simply move the files I want to backup to that same folder I'm able to share, and then I can go and get them from the desktop. Wrong! So, it wont let me copy/paste the files I want because they are not owned by this desktop. Sure enough, I could change the permissions manually to thousands of files. Now that I think of it, maybe I should have, It would probably be faster, than trying to transfer files the right way.


But I digress. I thought "well, I'll configure samba with my login details from my ubuntu login account and then I'll be able to login as admin from the desktop, and copy anything I want, since I would be the owner'. Wrong again. Configuring samba does nothing, and trying to access the ubuntu laptop, just returns "invalid user or pass".

I tried creating new user accounts on the ubuntu laptop, configuring them in samba, to no avail, same thing happened. During that trial and error frenzy, I lost the "guest" folder I had configured earlier. Now I can't create sharing folders - 'net usershare' returned error 255 cant convert name everyone to SID.

Tried purging samba and reinstalling the packages again. Nothing. It's almost 6 am, and what started to be a simple curiosity procedure turned into a fully fledged problem: I need file sharing working as it should, but I'm already too frustrated to go on. A whole night lost on trying to transfer some files, which supposedly should have taken 10 minutes tops of my time. 

I'm sorry but I'm pissed. Why are such simple tasks like this so complicated? Indulgence?

---

### Post by bab1 on 2012-09-27
> **ram0s said:**
> File sharing in Ubuntu is a living hell. So, I'll briefly explain the reason of my frustration:

5 hours ago - I wanted to format my Ubuntu laptop to try another distro. Ok. That meant I had to backup files from the laptop I wanted to keep. Quite a few gigs.

5 hours later to this moment, I'm pulling my hair out and literally cursing and wishing that all natural catastrophes fall at whomever implemented this. I. Just. Want. To. Goddamn. Transfer. Files. From. My. Laptop. To. My. Desktop. Through. My. Humble. Home. Lan. Network.
Implemented what?  What did *you* do to setup the file transfer?> 

It is not the first time I rage at this, some time ago I managed to share a folder from my Ubuntu laptop to my desktop pc, using guest account. So, I thought, to minimize frustration, I can simply move the files I want to backup to that same folder I'm able to share, and then I can go and get them from the desktop. Wrong! So, it wont let me copy/paste the files I want because they are not owned by this desktop. Sure enough, I COULD change the permissions manually to thousands of files. Now that I think of it, maybe I SHOULD HAVE, It would probably be faster, than trying to transfer files the right way.

Or even a bloody pen, <snip>! With 3 computers in the house, all connected by lan, how cool is it to use a <snip> pen to transfer large and numerous files from one place to another?  Yeeeap. The problem here, is that I refuse to do stuff the wrong way, and I force myself to learn the right way.

But I digress. I thought "well, I'll configure samba with my login details from my ubuntu login account and then I'll be able to login as admin from the desktop, and copy anything I want, since I would be the owner'. Wrong again. Configuring samba does nothing, and trying to access the ubuntu laptop, just returns "invalid user or pass".
Must have done something wrong.  I use Samba everyday to move files.  What did you do to setup Samba?> 

I tried creating new user accounts on the ubuntu laptop, configuring them in samba, to no avail, same thing happened. During that trial and error frenzy, I lost the "guest" folder I had configured earlier. Now I can't create sharing folders - 'net usershare' returned error 255 cant convert name everyone to SID.

Tried purging samba and reinstalling the packages again. Nothing. It's almost 6 am, and what started to be a simple curiosity procedure turned into a fully fledged problem: I need file sharing working as it should, but I'm already too frustrated to go on. A whole night lost on trying to transfer some files, which supposedly should have taken 10 minutes tops of my time. 

I'm sorry but I'm pissed. Why are such simple tasks like this so complicated? Indulgence?
It can be complicated, but once you sort out root problem setting up Samba is really simple.  How familiar are you with the terminal (CLI)?  What OS is the Desktop?

---

### Post by ram0s on 2012-09-27
Bab1 thank you for your reply, I will answer it later, I'm in a bit of a hurry now because of real life issues.

But, to add to my original post, a while ago I thought: I've had enough of this, I'm just going to get my external harddrive, and copy the files I need and get on with life.
So I connect the external harddrive to the laptop and try to copy my files to it: 

"The drive is read only"
"You are not the owner of the harddrive - read only"

So now I can't even copy MY STUFF from MY LAOTOP to MY externl harddrive, cause ubuntu says i'm not the owner? Can't even change any permissions, 'cause I'm not the owner. Aahhahahah!!!! 
This is me laughing, to avoid crying in rage. What was turning into a useful and brilliant operative system just lost all credibility and I'm sick of it. I just want to rescue my files from this bureaucratic os so I can wipe it forever.

Is there anything I can do?

---

### Post by bab1 on 2012-09-27
> **ram0s said:**
> Bab1 thank you for your reply, I will answer it later, I'm in a bit of a hurry now because of real life issues.
Ah, life...  Just another irritant.> 

But, to add to my original post, a while ago I thought: I've had enough of this, I'm just going to get my external harddrive, and copy the files I need and get on with life.
So I connect the external harddrive to the laptop and try to copy my files to it: 

"The drive is read only"
"You are not the owner of the harddrive - read only"
This behavior is normal.  I assume the drive has the partition formatted as NTFS or FAT32.  Partitions on the drive are always mounted by the user *root* unless instructed to do otherwise.  In the absence of instructions the partition is owned by the user root.  USB flash drives are detected differently and are mounted by root but the ownership is the $USER (e.g the logged in user) > 

So now I can't even copy MY STUFF from MY LAOTOP to MY externl harddrive, cause ubuntu says i'm not the owner? Can't even change any permissions, 'cause I'm not the owner. Aahhahahah!!!!
Try not to whine so much...  The computer has no idea who you are.  It only knows user accounts.> 
 
This is me laughing, to avoid crying in rage. What was turning into a useful and brilliant operative system just lost all credibility and I'm sick of it. I just want to rescue my files from this bureaucratic os so I can wipe it forever.

Is there anything I can do?
The OS is what it is.  It would be wise for you to not try to make it out to be something that it isn't.  I don't use a baseball bat to spread butter on my bread or use a spoon to move concrete.  It always helps to learn to use the tool (Ubuntu) correctly.

---

### Post by gromacs on 2012-09-27
> **ram0s said:**
> "The drive is read only"
"You are not the owner of the harddrive - read only"

So now I can't even copy MY STUFF from MY LAOTOP to MY externl harddrive, cause ubuntu says i'm not the owner? Can't even change any permissions, 'cause I'm not the owner. Aahhahahah!!!! 
This is me laughing, to avoid crying in rage. What was turning into a useful and brilliant operative system just lost all credibility and I'm sick of it. I just want to rescue my files from this bureaucratic os so I can wipe it forever.

Is there anything I can do?
Send it to yourself as email attachment:lolflag:

I'm trying to figure out how to get samba working too, or cifs is it now called...
I remember a few years ago I was able to access Windows shares fine, but now I find that Ubuntu needs a few extra packages to use cifs before it can even see the Windows shares, and even then accessing them is only 10% the speed that Windows 7 does it.

Anyway, here is how I got to at least see the shares, although transferring data and even getting file list is far slower than doing the same action from Windows 7 -> Server 2008 R2 (which is not running ZFS since there's Samba... right?)
```
sudo mount -t cifs //SERVER/Public /mnt/Public -o username=gromacs,domain=gromacs,iocharset=utf8,file_mode=0777,dir_mode=0777
```
Obviously replacing the path with your own server name, and domain\username. You will have to install a few packages iirc, Terminal will let you know which ones. Also you need to mount it to an empty folder, in this case I like to mount it in /mnt and whatever the share name is. If you aren't familiar with it already, just cd /mnt and mkdir something.

Hope that helps you :)

---

### Post by ram0s on 2012-09-27
> **gromacs said:**
> Send it to yourself as email attachment:lolflag:

LOOL! Haven't thought about that possibility, nice one.

[QUOTE=bab1]This behavior is normal.[/QUOTE]

That's exactly the problem. Well, it isn't the problem, who am I to dictate the way the OS is programed, but it's what makes me mad. It shouldn't be normal. I know Ubuntu for its easy user accessibility, so I thought a masters degree in Unix wouldn't be necessary to properly set up a file sharing connection with the other computers in the house. With osx, I just need to turn on the devices and that's it, the computers recognize one another instantly, only needing to define what to share. (Don't get me wrong, I'm not trying to turn this into a brand war, and I'm not advocating apple here, I don't even like apple in the first place nor its products, but hey it is a fact. My girlfriend gets home, turns on her macbook, and it is instantly detected on the network.) And I know what I'm comparing here, I'm aware that Ubuntu is free, etc, but is it that hard to provide an easy home file sharing solution, for those people who aren't installing Ubuntu on their enterprises mainframes with 100s of accounts, with ultra secret files for world domination?

I know Linux to be the kind of software that works like: "- Linux, please lift a foot. Ok, now lift the other." That's why I tried Ubuntu on this laptop, which is (was) being used mostly as a pseudo-storage device. Now it's a glass safe box for which I don't know the combination. But hey, it's cool, I'm not that mad anymore and it is only my fault, I accept that. It's just that something that should be simple and straight forward is taking way more time than it should. Frustration takes my IQ to the level of a potato, which in turn frustrates me more.

And that is the conclusion of my rant, no offense intended or anything, just my opinion on the idea that "the os is what it is" or "l2 use it first".

On the house I have the laptop with Ubuntu installed, a macbook, a desktop mac, and a desktop pc with windows 7. I don't think the issue is on the windows/osx side, I haven't got any issues sharing whatever between them. I also have no problem while accessing the other computers from the Ubuntu laptop, with their admin accounts. I can pull files to the laptop, can't send files to the desktop, though. Don't know why also, since I'm always logged in with the "receiver's" admin account.

Anyway, I'm still going through a few tutorials I read months ago when I set up a sharing folder successfully (but only un-secure with guest account)), let's see if I can figure it out tonight, sorry for all the implied arrogance.

---

### Post by bab1 on 2012-09-28
> **ram0s said:**
> ...

That's exactly the problem. Well, it isn't the problem, who am I to dictate the way the OS is programed, but it's what makes me mad. It shouldn't be normal.
Why should it be any different than it is?  Could it be that YOU don't understand how to configure it? > 
 I know Ubuntu for its easy user accessibility, so I thought a masters degree in Unix wouldn't be necessary to properly set up a file sharing connection with the other computers in the house. With osx, 
You don't need to have any special experience, although it sure helps.  What is important is either a basic knowledge of the system, or the willingness to ask politely for help. > 
I just need to turn on the devices and that's it, the computers recognize one another instantly, only needing to define what to share. (Don't get me wrong, I'm not trying to turn this into a brand war, and I'm not advocating apple here, I don't even like apple in the first place nor its products, but hey it is a fact. My girlfriend gets home, turns on her macbook, and it is instantly detected on the network.) And I know what I'm comparing here, I'm aware that Ubuntu is free, etc, but is it that hard to provide an easy home file sharing solution, for those people who aren't installing Ubuntu on their enterprises mainframes with 100s of accounts, with ultra secret files for world domination?
Well... actually it is hard to accommodate all the possibilities available for configuration.  In a closed environment (Windows or Apple) the developers can control all of possibilities.  It really is a trade off between time and money.  If you want to pay then you get ease of use.  If you want free, then be prepared to do some of the work configuring the rougher aspects of computing; or learn to ask politely for help. > 
I know Linux to be the kind of software that works like: "- Linux, please lift a foot. Ok, now lift the other." That's why I tried Ubuntu on this laptop, which is (was) being used mostly as a pseudo-storage device. Now it's a glass safe box for which I don't know the combination. 
What does that mean?> 
But hey, it's cool, I'm not that mad anymore and it is only my fault, I accept that. It's just that something that should be simple and straight forward is taking way more time than it should. Frustration takes my IQ to the level of a potato, which in turn frustrates me more.
Learn to ask polite questions and accept the help from those who are a little bit more knowledgeable.> 

And that is the conclusion of my rant, no offense intended or anything, just my opinion on the idea that "the os is what it is" or "l2 use it first".
I would say; accept some responsibility for your own computing education.  It will always come in handy.> 

On the house I have the laptop with Ubuntu installed, a macbook, a desktop mac, and a desktop pc with windows 7. I don't think the issue is on the windows/osx side, I haven't got any issues sharing whatever between them. I also have no problem while accessing the other computers from the Ubuntu laptop, with their admin accounts. I can pull files to the laptop, can't send files to the desktop, though. Don't know why also, since I'm always logged in with the "receiver's" admin account.

Anyway, I'm still going through a few tutorials I read months ago when I set up a sharing folder successfully (but only un-secure with guest account)), let's see if I can figure it out tonight, sorry for all the implied arrogance.
I'll bet the basic networking is not set up properly on the Ubuntu host, but that's just a guess since you haven't provided any information about what you did or how things are configured.

---

### Post by dbombtek on 2012-09-28
> **gromacs said:**
> Send it to yourself as email attachment:lolflag:

I'm trying to figure out how to get samba working too, or cifs is it now called...
I remember a few years ago I was able to access Windows shares fine, but now I find that Ubuntu needs a few extra packages to use cifs before it can even see the Windows shares, and even then accessing them is only 10% the speed that Windows 7 does it.

Anyway, here is how I got to at least see the shares, although transferring data and even getting file list is far slower than doing the same action from Windows 7 -> Server 2008 R2 (which is not running ZFS since there's Samba... right?)
```
sudo mount -t cifs //SERVER/Public /mnt/Public -o username=gromacs,domain=gromacs,iocharset=utf8,file_mode=0777,dir_mode=0777
```
Obviously replacing the path with your own server name, and domain\username. You will have to install a few packages iirc, Terminal will let you know which ones. Also you need to mount it to an empty folder, in this case I like to mount it in /mnt and whatever the share name is. If you aren't familiar with it already, just cd /mnt and mkdir something.

Hope that helps you :)

If you are trying to edit the permissions of the drive then look to the  etc/samba/smb.conf . make sure it is shared and the permissions are correct. if you are uncomfortable editing that then use sudo system-config-samba to set your permission. 
I hope this helps.

---

