---
title: "Pointing mythtv towards videos on a samba share"
date: 2010-07-10
forum: Mythbuntu
---

### Post by XanII on 2010-07-10
I have an old windows server and i would like it's videos to be available to Mythbuntu 10.04 so they are visible to select when i go to the videos section with my remote control. 

Myhtbuntu 10.04 with XFCE doesnt seem to have samba installed so i have installed smbfs and smbclient and PyNeighborhood but right now i dont really know how to proceed. 

I have defined paths to the server in many different ways. (i.e. smb://192.168.xx.yy/Genoa (N)) or direct IP or smb://(server name)/(with or without a direct share name).

As seen above the share name also got a space before the (N) characters, i dont know if i can just use 'space' as a space for the name or if i have to use something to substitute the space. changing the name would be painfull as so many softwares point towards it now.  

Now i dont know how to proceed: I dont know if i have samba actualy working correctly OR if i have entered the paths correctly to mythtv. OR if this is even possible in the first place as i have not been able to find a howto for this tiny little detail. This is though quite important to me as the backend hd is small and the external server is the one system where the videos taken from other sources other than TV come and go. It was built long before current mythtv project so getting mythtv to work with its files would be more desireable than trying to go the other way around. It's discs are much larger. :D 

And if this 'samba share lookup directly in mythtv' would not be be possible then i would still need some manual-ubuntu-connect-to-server-like way to get the videos from the external server and drop them to the default video dir on the backend. Right now i dont have a network connection working towards the old XP server and PyNeighborhood only gives me the worgroup name but not much else.

---

### Post by ian dobson on 2010-07-10
Hi,

First try getting a mount working from the terminal, using the command like:-

mount -t cifs -o  username=NAME,password=PASSWORD  //IP_ADDRESS_OF_SERVER/SHARE_NAME /mnt

When the mount works you'll see your windows share under /mnt.

When it works you can add the command to /etc/rc.local so that it starts on every boot.

Regards
Ian Dobson

---

### Post by SnafuFlux on 2010-07-10
hi ian, is there any difference from /etc/rc.local and /etc/fstab?

in previous installations I've used fstab.  currently I use it on the back end for my videos which are on a different (physical) hard drive).

---

### Post by XanII on 2010-07-10
Thank you for the reply. However as i continued to narrow down things i noticed that the Media -> Videos department in mythtv frontend doesnt seem to update. I wonder if there is some manual trigger i can use to have the computer scan for media. 

I added a couple of .avi files to the default video folder and that format should be noticed (i have also unknown formats enabled) but the page just say it cannot find any videos. 

Good point on the samba though, if i can get the mythtv side to work then this permanent mounting of the share comes up next. 

This is tricky. :o But for the moment the problem lies in MythTV, not in samba.

---

### Post by SnafuFlux on 2010-07-10
Yah, you need to tell mythvideo to rescan your movie folders.

use: M | scan for changes

as for samba, I'm still having issues.  I think it's because samba is always asking for a password, and it shouldn't be.  I want to use the guest/nobody account.

---

### Post by SnafuFlux on 2010-07-10
I got it to automount using fstab.

```
//serverip/store /mountpoint cifs guest 0 0
```

this seems to work for me.

---

### Post by ian dobson on 2010-07-10
> **SnafuFlux said:**
> hi ian, is there any difference from /etc/rc.local and /etc/fstab?

in previous installations I've used fstab.  currently I use it on the back end for my videos which are on a different (physical) hard drive).

Hi rc.local is just a script that is run on startup.

Regards
Ian Dobson

---

### Post by nickrout on 2010-07-10
> **ian dobson said:**
> Hi rc.local is just a script that is run on startup.

Regards
Ian Dobson

fstab is the obvious way to do it.

---

### Post by XanII on 2010-07-13
> **SnafuFlux said:**
> Yah, you need to tell mythvideo to rescan your movie folders.

use: M | scan for changes

as for samba, I'm still having issues.  I think it's because samba is always asking for a password, and it shouldn't be.  I want to use the guest/nobody account.

:confused: Sorry lost me there. Use what? Command M pipe?

---

### Post by ian dobson on 2010-07-13
Hi,

Just stick the mount command in /etc/rc.local and have done with it (no problems with needing to enter passwords).

mount -t cifs -o username=NAME,password=PASSWORD //IP_ADDRESS_OF_SERVER/SHARE_NAME /mnt

Regards
Ian Dobson

---

### Post by SnafuFlux on 2010-07-13
[QUOTE=XanII] i noticed that the Media -> Videos department in mythtv frontend doesnt seem to update. I wonder if there is some manual trigger i can use to have the computer scan for media. 

I added a couple of .avi files to the default video folder and that format should be noticed (i have also unknown formats enabled) but the page just say it cannot find any videos. [/QUOTE]

Hi XanII,

I was saying that you will need to tell mythvideo to scan the folders which should have your videos in.  

the wiki for mythvideo on mythtv's website is most helpful.  Give it a read.  If you're still having issues, let us know.

[http://mythtv.org/wiki/Mythvideo#Setting_Up_Video.2FImage_Storage_Groups](http://mythtv.org/wiki/Mythvideo#Setting_Up_Video.2FImage_Storage_Groups)

---

### Post by andree_b on 2010-07-14
> **XanII said:**
> :confused: Sorry lost me there. Use what? Command M pipe?
In the video screen just press "M" - it's the default key for "menu"
A menu will pop up where you then select "Scan for changes"

---

### Post by XanII on 2010-07-16
Thanks all for the replies. Finding the 'm' key by googling proved to be impossible. And the mythtv interface doesnt hint that you can actualy give commands at this spot with the keyboard. Found out about the 'M' myself awhile ago when this thread was already open. 

Closing and solving this one.

---

