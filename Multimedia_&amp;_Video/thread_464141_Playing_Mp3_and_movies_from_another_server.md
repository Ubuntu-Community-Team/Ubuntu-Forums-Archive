---
title: "Playing Mp3 and movies from another server"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by frolle on 2007-06-04
Hello everyone :)

I finally did it, i installed Ubuntu 7.04 in my PC, but I am having problems. I have a Win2003 server with all my mp3's and movies and I would like it to be that way. When is I was using XP, I just opened the file via shares. I am trying to do the same in Ubuntu, but it is not working.

The only thing I have tried is to access the shared folder with smb://<localIP>.

Any ideas?

Thanks in advance!

Regards

---

### Post by madmetal on 2007-06-05
> **frolle said:**
> Hello everyone :)

I finally did it, i installed Ubuntu 7.04 in my PC, but I am having problems. I have a Win2003 server with all my mp3's and movies and I would like it to be that way. When is I was using XP, I just opened the file via shares. I am trying to do the same in Ubuntu, but it is not working.

The only thing I have tried is to access the shared folder with smb://<localIP>.

Any ideas?

Thanks in advance!

Regards

you have to configure samba correct
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
and then add NTFS read/write support and mount windows partition..
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

and i suggest VLC player (you can find it in synaptics)

UAResolved.

---

### Post by MetalMusicAddict on 2007-06-05
frolle. You will also need to add your Ubuntu user to the windows box.

---

### Post by madmetal on 2007-06-05
> **MetalMusicAddict said:**
> frolle. You will also need to add your Ubuntu user to the windows box.

yeap :) 
i think i am forgeting windows :P

---

