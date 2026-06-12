---
title: "[SOLVED] Mythtv Front End shows videos, but won't play"
date: 2008-03-14
forum: Mythbuntu
---

### Post by freymann on 2008-03-14
I downloaded the MythBuntu 7.10 CD iso and installed it on a "core" (I guess they say that's a front end/back end).

I then installed the same CD on another computer, using advanced mode, and set it to frontend only.

On the frontend, I can "see" all the videos (*.avi) that I had previously stored but when I go to play them, it flashes for a second (like it's going to play) and then back to where you started.

On the "server" (the frontend/backend?) things play fine.

I don't know why it's doing that. I added the restricted codecs, etc.

So now I have both doing a system update (some 140+ files) and will try again in the morning.

I found similar to this in a FAQ, and it said to make sure the hostnames on each computer were unique. In my case, that is true.

I have another question to ask, but I'll post that separately.

Thanks for any assistance you can offer.

---

### Post by murbanci on 2008-03-14
Check out this on the MythTV wiki and see if it helps answer your question:
[http://www.mythtv.org/wiki/index.php/Mediashares](http://www.mythtv.org/wiki/index.php/Mediashares)

Hope this helps you out.

---

### Post by freymann on 2008-03-15
> **murbanci said:**
> Check out this on the MythTV wiki and see if it helps answer your question:
[http://www.mythtv.org/wiki/index.php/Mediashares](http://www.mythtv.org/wiki/index.php/Mediashares)
Hope this helps you out.

 I'm so glad to be back in the land of Ubuntu ;-)  (I spent a week pulling my hair out with LinuxMCE. Ug.)

 That sounds exactly what I need to resolve this problem.

 Thanks very much!

---

### Post by freymann on 2008-03-15
> **murbanci said:**
> Check out this on the MythTV wiki and see if it helps answer your question:
[http://www.mythtv.org/wiki/index.php/Mediashares](http://www.mythtv.org/wiki/index.php/Mediashares)

Hope this helps you out.

I followed the instructions and when I go to mount the NFS shares on a frontend I get this error message:

```

 sudo mount 192.168.0.2://var/lib/mythtv/pictures/ /var/lib/mythtv/pictures/
mount: wrong fs type, bad option, bad superblock on 192.168.0.2://var/lib/mythtv/pictures/,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The server has a 250GB Sata HD and Sata DVD Rom. After the installation I installed my 500GB IDE HD (formatted as NTFS) and I have mounted it as /media/nas/

I was using the 500GB drive on a Vista machine and it's half full of music, videos and photos so I didn't want to reformat it and lose all the media.

I then created symlinks to the Music, Photos and Video folders. Is that part of the problem?

For example, inside

/var/lib/mythtv/music on the server, I added a symlink so 

/var/lib/mythtv/music/Rock points to /media/nas/Music
/var/lib/mythtv/music/Country points to /media/nas/Country_Music

etc.

Initially, I just tried to set the paths inside MythTV to /media/nas/Music, /media/nas/Photos and /media/nas/Video but it won't export a NFS from that drive.

---

### Post by freymann on 2008-03-15
I was able to mount the NFS shares by simply adding the NFS stuff to the other frontends as explained in the link in the first reply :-)

---

