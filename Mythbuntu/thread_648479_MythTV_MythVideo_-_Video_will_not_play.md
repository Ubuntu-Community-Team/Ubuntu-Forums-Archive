---
title: "MythTV: MythVideo - Video will not play"
date: 2007-12-23
forum: Mythbuntu
---

### Post by mechgt on 2007-12-23
I cannot get any video's to play using MythFrontend.

I just installed MythTV, MythVideo, & MythMusic on my Gutsy box.  I'm able to connect and play the videos in my /var/lib/mythtv/videos folder on my D-Link DSM-520, but unable to play anything using the MythFrontend.


When trying to play videos (Media Library > Watch Videos > videofile) it flashes "Loading videoname" extremely fast and then that's it.  I have 2 frontends, one on the local server and another on a different box, both give the same result.

```
dpkg -l | grep mythtv
ii  mythtv-common                              0.20.2-0ubuntu10.1
                   A personal video recorder application (commo
ii  mythtv-frontend                            0.20.2-0ubuntu10.1
                   A personal video recorder application (clien
ii  mythtv-transcode-utils                     0.20.2-0ubuntu10.1
                   Utilities used for transcoding MythTV tasks

```

---

### Post by foxbuntu on 2007-12-26
Please see the following Wiki, this usually happens when you have not setup a video player supporting the type of file:

[http://www.mythtv.org/wiki/index.php/MythVideo#Xine_Configuration]("http://www.mythtv.org/wiki/index.php/MythVideo#Xine_Configuration")

Also note that you will need to install Xine for this to work if you have not already done so

---

### Post by babylon66 on 2008-01-03
Mechgt, sorry to jump into your thread.  I was having the same problem but for a different reason, I deleted the file association for playing movie files from HD.

Can you tell me what settings you have in the following screen "MythVideo file associations"

...............
Utilities/Setup
Setup
Media Settings
Videos Settings
File Types
................

Thankyou very much.

---

### Post by mechgt on 2008-01-06
> **babylon66 said:**
> Mechgt, sorry to jump into your thread.  I was having the same problem but for a different reason, I deleted the file association for playing movie files from HD.

Can you tell me what settings you have in the following screen "MythVideo file associations"

...............
Utilities/Setup
Setup
Media Settings
Videos Settings
File Types
................

Thankyou very much.

I haven't changed any of this from the default (at least not to my knowledge!):

Ext - Command - Jse Default Player - Ignore
txt - (blank) -  - Ignore
log - (blank) -  - Ignore
mpg - Internal
avi - (blank) - default
vob - Internal
mpeg - Internal
VIDEO_TS - Internal
iso - Internal
img - Internal

All of the files I've been trying to play are avi.  After reading this, I changed the 'avi' extension to 'Internal' and got rid of the 'JSE Default Player' checkbox, and videos seem to play now.  Thanks!!!

The problem now, is that it wants all of the movies to be located locally in the /var/lib/mythtv/videos/... folder.  I tried a while ago to change the default location to smb://server/share, but it couldn't understand that.

How do I tell it to look on the mythtv server?  

I don't want to have to mount samba shares on each of the clients to  the server.  That sounds like a crap way to fix it.  I would have thought that it would have known to look on the mythbackend server rather than the mythfrontend client for the video files.

---

### Post by newlinux on 2008-01-06
Unfortunately, it does look on the frontend for the video files so you will need to mount the shares.

---

### Post by chipee on 2009-05-02
> **newlinux said:**
> Unfortunately, it does look on the frontend for the video files so you will need to mount the shares.
 
[FONT=Times New Roman][SIZE=3]Hello[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I am a new be to this,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I have been having these problems but I am having problems finding how to mount a network drive.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Please can some one point me in the correct direction[/SIZE][/FONT]

---

### Post by newlinux on 2009-05-02
search the forums or [https://help.ubuntu.com/](https://help.ubuntu.com/) for CIFS or NFS or SSHFS, depending on which protocol you want to use.

---

