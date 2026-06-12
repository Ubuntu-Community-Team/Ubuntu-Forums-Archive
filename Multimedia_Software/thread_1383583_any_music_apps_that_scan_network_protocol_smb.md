---
title: "any music apps that scan network protocol smb:// ?"
date: 2010-01-17
forum: Multimedia Software
---

### Post by maestrobwh1 on 2010-01-17
I am looking for something that can recognize the protocol smb:// but I fear there is nothing.  Amarok 2 lookede promising but even though there is a network tab, it doesn't seem to work (it looks for nifs I think, and not samba shares?).

I know I can "mount" shares using cifs

```
sudo mount -t cifs //ipofserver/SHARENAME /mountpoint options
```

This is cumbersome since nautilus (or dolphin) can do it with a click.  I also know I can use fstab and know how to do it.

Anything out there that handles shares without hard mounting?

---

### Post by sgosnell on 2010-01-17
What are you trying to do?  To play music from a samba shared computer, I just open Nautilus, navigate to the folder with the music, and have the music player open the files.  Do you need to do something more involved?

---

### Post by sports.car.guy on 2010-01-17
The reason why you are having issues is because you are just accessing the drive through Nautulis or Dolphin, not because of physically mounting the drive. That is how Linux works and is designed to work. What is the problem with having a Samba share mounted on your system?

I have several file mounts setup over my network without any issues. All of them are written in /etc/fstab and point to a credentials file that is set for only my account to have access to, besides root obviously. Is there a particular reason you don't want to mount Samba shares?

---

### Post by maestrobwh1 on 2010-01-17
Just thought there might be a music app that can deal with network shares like nautilus but then be able to scan a directory and if someone knew about that, it would simplify what I am trying to do.  So far, the bug still exists in karmic were if a share is left mounted on shutdown, the shutdown hangs.  One just has to reorganize the shutdown scripts to fix this but still... 

Windows actually handles this a bit more helpfully by mapping a drive and does not seem to have a problem if the computer is suspended and then resumed out of range of the mounted share.  I found a way around this with my other laptop with running karmic with shares in my fstab.

---

### Post by sports.car.guy on 2010-01-17
> **maestrobwh1 said:**
> Just thought there might be a music app that can deal with network shares like nautilus but then be able to scan a directory and if someone knew about that, it would simplify what I am trying to do.  So far, the bug still exists in karmic were if a share is left mounted on shutdown, the shutdown hangs.  One just has to reorganize the shutdown scripts to fix this but still... 

Windows actually handles this a bit more helpfully by mapping a drive and does not seem to have a problem if the computer is suspended and then resumed out of range of the mounted share.  I found a way around this with my other laptop with running karmic with shares in my fstab.


I have not encountered this problem in Karmic at all. I am running Kubuntu though and could be why. In 9.04 I encountered a long hang but never a complete system hangup when I had the same setup going on it up until a couple weeks ago.

I would suggest smb4k then. It will allow you to mount your shares in a directory local to your user account and being mounted physically through smb4k you shouldn't have any of the issues you are encountering with Samba.

Mounting through /etc/fstab is how I have my shares mounted and I suggested you mount them the same way. It is not a way around anything. It is how Linux and Unix have been designed from the ground up to work. It treats everything like hardware and network storage as part of the file tree for the most part.

Physically declaring a Samba share's mount in /etc/fstab is the same exact thing in essence as mapping a network drive in Windows. There is no difference and both function in the same manor. Just because it is different and accomplishes the same thing does not mean Windows is better then Linux.

If this is a PC that is in one location and you are mounting these shares every time the system is booting why care if you have the mounting done through /etc/fstab?

---

### Post by ratcheer on 2010-01-17
I noticed the same problem the OP is talking about, just today. I have my flac files on a 1.5 TB external drive that is connected to my XP machine. If I open Nautilus, it is right there under Network >> My XP hostname >> the shared directory. From Nautilus, I can navigate to one of the files and right click and say, Open with vlc.

However, if I use the vlc Media menu and try to either Open File or Open Directory, the network share does not show at all and I can find no way to navigate to it.

So, using the first method, I can play one music file at a time. But, I cannot open a music directory and play all the songs in it, like I could if I could open the shared directory from vlc.

At least, I think this is what the Op is talking about.

Tim

---

### Post by sports.car.guy on 2010-01-17
> **ratcheer said:**
> I noticed the same problem the OP is talking about, just today. I have my flac files on a 1.5 TB external drive that is connected to my XP machine. If I open Nautilus, it is right there under Network >> My XP hostname >> the shared directory. From Nautilus, I can navigate to one of the files and right click and say, Open with vlc.

However, if I use the vlc Media menu and try to either Open File or Open Directory, the network share does not show at all and I can find no way to navigate to it.

So, using the first method, I can play one music file at a time. But, I cannot open a music directory and play all the songs in it, like I could if I could open the shared directory from vlc.

At least, I think this is what the Op is talking about.

Tim


[B]It is not a problem, a bug, lack of compatibility, or anything like that!

Linux is designed to be this way intentionally!

[/B]I have said this more then once in plain English and not trying to be a jerk here. Read what I wrote, or better yet google before asking a question. You will find the same exact thing online I have said here more then once now if you were to do a web search. 

If you want the Windows experience use Windows. If you are flexible and open to things working a little differently but basically doing the same thing then this should not be an issue, at all.

**You either need to mount the drive at boot using /etc/fstab or use an application like smb4k. That is the only way to have content work over the network like Windows.**

---

### Post by Silient on 2010-01-17
Senks

---

### Post by shazbut on 2010-01-17
[xbmc]("http://xbmc.org/") will do that, and more (maybe too much more).

---

### Post by sports.car.guy on 2010-01-17
> **shazbut said:**
> [xbmc]("http://xbmc.org/") will do that, and more (maybe too much more).

So won't MythTV, but he is just looking to have the share act like it would in Windows, not a find something like that.

That would be overkill for what he is looking to do and not allow for the remote share to act like a local drive or partition.

---

### Post by maestrobwh1 on 2010-01-17
Wow, I felt like I left a campfire and now the forest is on fire.

Yes, there is/was a bug and I see it in karmic all the way back to hardy.  It was simple to fix by moving S31umountnfs.sh **to S14umountnts.sh **in **/etc/rc0.d** and **/etc/rc6.d**:  The original order disconnected the network before trying to unmount shares.  That isn't REALLY what this post was about.  

I did find a gui that allows me to just browse my host and mount the available shares to whatever location I want: xsmbrowser.  Oddly, just as an fyi, you have to append it's menu entry by adding gksudo or kdesudo to get it to launch that way.  It half works.  It does mount, but does not unmount the shares so I just symlinked /etc/rc0.d/S14umountnts.sh to /usr/bin/umountsmb and created a desktop icon that executes that file.  I can also now just type 

$sudo umountsmb

xbmc and senks are not in the repos.  I will search around for them.

@sports.car.guy--> You are correct, there is an equivalent to mapping a network drive using fstab, but I was more or less looking to do it with a few clicks once in a while.  xsmbrowser lets me more or less do that like windows explorer.  It would be nice if nautilus gave an option to create an actual mount point for a share.  The way it works now is still good for most of my uses (transferring files).

---

### Post by sports.car.guy on 2010-01-17
Try smb4k.

It is exactly what you are looking for, open it up, and mount easily. No fuss, no muss.

---

### Post by ratcheer on 2010-01-17
> **sports.car.guy said:**
> [B]It is not a problem, a bug, lack of compatibility, or anything like that!

Linux is designed to be this way intentionally!

[/B]I have said this more then once in plain English and not trying to be a jerk here. Read what I wrote, or better yet google before asking a question. You will find the same exact thing online I have said here more then once now if you were to do a web search. 

If you want the Windows experience use Windows. If you are flexible and open to things working a little differently but basically doing the same thing then this should not be an issue, at all.

**You either need to mount the drive at boot using /etc/fstab or use an application like smb4k. That is the only way to have content work over the network like Windows.**

Ok, thank you.

Tim

---

### Post by maestrobwh1 on 2010-01-18
Cool.  I saw smb4 in the repos and figured it was a newer version, but didn't know it allowed me to do what I want.  I assume I have to put it ony my host machine as well?

---

### Post by sports.car.guy on 2010-01-18
> **maestrobwh1 said:**
> Cool.  I saw smb4 in the repos and figured it was a newer version, but didn't know it allowed me to do what I want.  I assume I have to put it ony my host machine as well?


NOOOOOOOO! smb4k not smb4.. smb4 is the protocol's new server and client incarnation.

I am not trying to be a jerk asking this, I am trying to see if you are just not understanding what I put here in plain English.

Is English a second language for you? I have been bending over backwards trying to help you with this, and you can't take the time to truly read, you are glancing. Don't ask for help if you aren't going to read what the help is.

You have taken what I said and ignored it multiple times in this post because you know what is wrong, its Linux and Samba being buggy. The whole time you've been trashing Linux saying this, and why, basically because Linux is not working like Windows.

Why should I help you when you can't take the time to try to help yourself. You didn't even take the time to try to find the answer yourself and came out here first thing, and it is because you didn't want to take the time and expect someone else to do it for you.

I told you to google what you claim to be a bug God only knows how many times so you would see it is how this is the intentional design of Samba and Linux the way it works, not a bug. You obviously couldn't do this before wasting my time and everyone elses out here. You have been swearing it is a bug and ignoring multiple times what I have said.

You have done nothing but act like a know it all, swearing this is why it is doing it, it is happening because of a bug. It can't be the intentional design, why would be made that way, because it makes no sense to be a feature (It is called for SECURITY!). You knew that much Mr. Know it All, so you should have been able to fix your issues yourself.

I am done trying to help you. I would have more success taking a gun and shooting myself square in the foot then helping you. It would be less painful too.

For future reference these forums are not your personal tech support. You need to do the leg work yourself and see what is out there for information first. If then you can't find a solution, or piece together one from looking over multiple outlets, then come out to ask for help! Not straight out here and have us do the work for you. 

That is lazy and scummy, especially when you act like a know it all and tell who is helping you that they are wrong and know what is what!

---

