---
title: "mythbuntu &amp; network attached storage devices"
date: 2007-11-14
forum: Mythbuntu
---

### Post by jderrick on 2007-11-14
Hi everyone,

I am about to embark on an installation of mythbuntu and have a question about integrating a Network Attached Storage device. I only have a 20GB internal HD in my soon-to-be mythbox. However, I have a 320GB Maxtor NAS device that I use essentially as a home media server and all my other computers are connected to it. I would rather not have to buy another internal HD for my mythbox if I don't have to. Does anyone have any experience with a similar setup? Do I need to do any special formatting to my NAS drive short of simply setting a mount point to it in my mythbox? I was able to set up Ubuntu fairly easily to connect to the NAS, but my Xubuntu laptop took a little more tweaking. Since the mythbox will also be running Xcfe (like Xubuntu) will it be difficult to mount the NAS to it? Any and all ideas would be most appreciated!

---

### Post by road2elysium on 2007-11-14
> **jderrick said:**
> Hi everyone,

I am about to embark on an installation of mythbuntu and have a question about integrating a Network Attached Storage device. I only have a 20GB internal HD in my soon-to-be mythbox. However, I have a 320GB Maxtor NAS device that I use essentially as a home media server and all my other computers are connected to it. I would rather not have to buy another internal HD for my mythbox if I don't have to. Does anyone have any experience with a similar setup? Do I need to do any special formatting to my NAS drive short of simply setting a mount point to it in my mythbox?

Since your NAS is probably configured to be a NTFS share, you might want to look into a new FS more suitable to large media files in linux.

---

### Post by roseway on 2007-11-15
I'm not sure if that's the case. My Buffalo Linkstation uses an embedded Linux system, and the disk is formatted as ext2, although it presents itself as a Windows share which I access using CIFS.

---

### Post by superm1 on 2007-11-15
Depending upon what network protocols it exposes, you can mount it using smbfs or nfs directly to the mythtv storage directory (/var/lib/mythtv/recordings)

---

### Post by jderrick on 2007-11-15
Thanks for the suggestions. My NAS is currently shared with my Xubuntu laptop and Ubuntu desktop (soon to be mythbox) via smbfs. The Xubuntu laptop took some tinkering to set up (via command line), but Ubuntu recognized the NAS very easily (via the GUI). So long as mythbuntu recognizes it as easily as Ubuntu did, I should be good to go. I'll post again if I run into any issues. If anyone else has any further suggestions/ideas, feel free to pass them along.

Thanks!

---

### Post by jderrick on 2007-11-20
Update:

Well, I've successfully installed mythbuntu and have it mostly configured. I've also been able to mount my NAS and can explore the files...for about 5 minutes or so. Then, it suddenly disappears. When running the fontend, any television show that I'm watching will record a few seconds/minutes onto the drive, and then it locks-up and loosing the connection to the NAS. Even when I try to re-mount the drive (sudo mount -a), it doesn't mount. It seems the only thing I can do is restart my mythbox. I obviously have the permissions set correctly since video files can be written to the drive, albeit a few seconds. Does anyone have any ideas? I really want this to work since all my music files and photos are on my NAS. Plus, I don't want to purchase another internal hard drive if I don't have to.

Thanks!

---

### Post by newlinux on 2007-11-20
How did you mount it? What options did you give it in fstab? If possible, I'd use CIFS instead of smbfs. More stable for me.

---

### Post by uopjohnson on 2007-11-21
I have never been able to successfully use an NAS device to record video from myth.  I searched quite a bit on this last time I built a backed and I found that most people had trouble much like yours that has to do with the fact that neither smb of cifs are really built to write in one long continuous stream.  Now  I keep all of my videos and music on the NAS and I bit the bullet and a couple of sata drives for my backend.  Since then, smooth sailing. 
If you really want to get it running I would ask on the main mythtv list and get some specific mount options that are working for someone else.  You also probably need to speed test your nas to see if it is fast enough.  You could do this by recording something in myth and then copying it to the NAS, if it takes longer to copy than it did to record you are probably in trouble.

---

### Post by jderrick on 2007-11-21
Thanks so much for the speedy responses. Regarding my fstab file, I discovered that the permissions were not correct. More specifically, the permissions were set to read only. Thus, I updated the permissions to allow read/write capability. That didn't work. Upon further research, I realized that the frontend apparently uses it's own "user account" called "mythtv." Maybe this should have been obvious from the beginning, but I didn't realize it. So, I added "mythtv"  to my fstab file (with read/write permissions) and, viola, it worked...sort of. The frontend was able to obtain my music files that are on my NAS, but still seemed to lock up when trying to watch/record tv. Looks like my network isn't fast enough for recording to a network attached storage device. So, unless someone else has any more ideas, it looks like I may need to suck it up and buy another internal drive to solely use for recordings. Not a tragedy, I suppose.

---

### Post by uopjohnson on 2007-11-24
That has been my experience as well, remote shares just don't seem to be fast enough.  I have a cat6 gigabit network, and still am not able to get good writing over cifs.  I'm sure there are steps I could take to make it work, but I'm just as happy with my internal storage.

---

### Post by newlinux on 2007-11-24
I tried using a CIFS share once (when my hard drive died), and it was fast enough to record, but once I tried rewinding or fastforwarding it was all over... (on a fast ethernet connection). I think it may be more the protocol than the network itself... You are right, though, probably some tweaking could get it to work, but internal is just easier for me...

---

