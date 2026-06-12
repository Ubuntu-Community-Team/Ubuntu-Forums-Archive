---
title: "k9copy Not Writing to Network Location"
date: 2010-08-22
forum: Multimedia Software
---

### Post by Gotit on 2010-08-22
Hi
I'm have a problem getting k9copy to write to my networked drive and I'm hoping someone can help.

_My set-up is:_ 
Netgear router with USB NAS
External HD connected to the USB NAS port
- HD partition NTFS (Netgear NAS doesn't seem to recognize ext*)
Network/share is SMB
Computer connected to router via RJ45/ethernet

_The problem is:_
When I launch k9copy and select a copy location of Network k9copy seems to start fine.  It runs for about 2 seconds and says "Selected titles have been successfully extracted".  This should have taken about 15 - 20 min.  When I look for the newly created folder I can not find it anywhere (not that there would be anything in it after 2 seconds).

I tried launching k9copy from the command line and performing a save to a Network location but that didn't show anything unusual:
```
gotit@Home-Linux:~$ k9copy
" dvdauthor -x /tmp/kde-gotit/k9copy/k9aCDF873.xml" 
gotit@Home-Linux:~$ 
```
When I launched from the command line via sudo and give a copy location of Network, k9copy runs the full 15 - 20 min but the new folder of the backed up disc is not on the network drive.  Instead it's under "/" (on the local HD) and of course belongs to root.  The terminal shows the following:
```
gotit@Home-Linux:~$ sudo k9copy
[sudo] password for gotit: 
Error: "/var/tmp/kdecache-gotit" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-gotit" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-gotit" is owned by uid 1000 instead of uid 0.
" dvdauthor -x /tmp/kde-gotit/k9copy/k9atj1215.xml" 
gotit@Home-Linux:~$ 
```
Which I guess I can understand.

My question is, how do I get k9copy to write to my Network drive?  Any thoughts?  Thanks!!

---

### Post by Gotit on 2010-09-20
bump

---

### Post by corcomp84 on 2010-09-20
I hated k9,,, Ill tell you what the best program I found was OGMrip.. simply download through synapatic manager and be on your way... as for sending it to a network location that could be a problem.. do you just not have the room to save it to your local computer first, because it would take forever to save it over the local network, it would want to decode it to which could cause problems.. At least I would think so..

---

### Post by perspectoff on 2010-09-20
I see your problem: you are trying to run k9copy as root user using sudo. Don't do that.

Just run k9copy as a regular user. That's the source of your errors.

You can't change NTFS folder permissions using Samba very easily; the permission of a folder at the time of its creation is how it has to stay, generally. Therefore, the NTFS folders on your NAS hard drive that are to be used for k9copy should be initially created by the same user that will run k9copy. That way the new folder(s) on the NAS will recognize the Ubuntu user (that created them) as the folder owner and k9copy will then be able to use it when it is run by that same user.

I have used k9copy the way you do (using network folders). You can specify the paths in two different places in k9copy configuration: DVD -> Output directory and Paths -> DVD (and other output locations). I happen to like to create 2 folders, k9copy and k9copytemp, on the NAS drive as a regular user (e.g. user whipporwill). Then k9copy (or dolphin or some other file manager app) can access them whenever it is run as regular user whipporwill. I use one folder for finished product storage and one for the temp directory.

The storage folder and the tmp folder can be specified independently in k9copy, so check the settings in both places.  Any network folders should have been created properly so they belong to the regular user and not to root.

Overall, I agree that the added time involved in network storage transmission is not worth it if you have space available on your hard drive. (It is definitely way too painful over a wireless network, but I see you are using Ethernet wired connections.) So I usually end up doing all the ripping/conversions on my hard drive and then just moving the finished product over to the NAS (I also use an NAS with NTFS folders, but mine is Buffalo, not Netgear).

OGMrip doesn't allow previewing, and I use that option frequently.

I didn't like k9copy either when only FFMPEG was available in it, but it works a lot better since it went to mencoder as well (which is what OGMrip uses).

k9copy is a one-click app for me. It shrinks correctly without fiddling. I can use it for recoding to other formats easily, now. (I used to have to revert to FFMPEG or AVIDEMUX for that in the past.) I love that.

However, k9copy has a funny little glitch. If you start extracting and then cancel midway, or try to extract something and then try to extract a second time, it will give the error you mention.

A solution I sometimes must revert to is to clean out the k9copy tmp folder.

For me (user whipporwill), that temp folder is found in Kubuntu at /tmp/kde-whipporwill/k9copy

I clean out that directory whenever I have problems and then everything works again. Of course, if I have set the temp directory to be somewhere different (a network folder, for example), then I have to clean out whichever network folder I have set to be the temp folder. It is for this reason that I store finished product in a separate directory, so I can clean out the temp directory when needed.

---

### Post by Gotit on 2010-09-21
WOW!
corcomp84 & perspectoff thanks for all the information.

I will say I have had good luck with k9 for the last 3 or so years even though the GUI seems to behave a bit strange from time to time.  Maybe that's because I use Gnome vs. KDE.  I'll have to take a peek at OGMrip, I hadn't heard of that one before.  

Also, the input you gave on time to decode to an NAS drive may make me rethink my setup.  I am a little tight on local space but maybe a separate move after decode isn't such a big deal.

Thanks again

---

### Post by Gotit on 2010-09-22
> **perspectoff said:**
> I see your problem: you are trying to run k9copy as root user using sudo. Don't do that.

Just run k9copy as a regular user. That's the source of your errors.

You can't change NTFS folder permissions using Samba very easily; the permission of a folder at the time of its creation is how it has to stay, generally. Therefore, the NTFS folders on your NAS hard drive that are to be used for k9copy should be initially created by the same user that will run k9copy. That way the new folder(s) on the NAS will recognize the Ubuntu user (that created them) as the folder owner and k9copy will then be able to use it when it is run by that same user.
Hmmm... still having problems with attached NAS
1. I have: 
[INDENT]created a new folder on NAS while logged in as my normal user[/INDENT]
[INDENT]launched k9copy as my normal user[/INDENT] 
[INDENT]pointed k9copy to the new folder[/INDENT]
But K9 could not write to the new NAS folder

2. I tried: 
[INDENT]unmounting the NAS drive[/INDENT] 
[INDENT]mounting the drive locally[/INDENT] 
[INDENT]making a new folder while logged in as my normal user[/INDENT]
[INDENT]double checked the permissions that it belonged to me[/INDENT]
[INDENT]reconnected the drive to the router as NAS[/INDENT] 
but k9 still could not write to the new folder  
Any other thoughts?? (I know, I know rip local and copy to NAS :))

> **perspectoff said:**
> The storage folder and the tmp folder can be specified independently in k9copy
I see where to specify the storage folder, but I don't find anyplace to specify the tmp folder.  I have also checked /home/gotit/.kde/share/config/k9copy and didn't find anything for tmp there either.  Maybe it's the version I'm running v2.3.5?

---

