---
title: "Sharing Media Files - Windows to Ubuntu"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by cdinoz on 2006-11-29
My Windows box happily will play any media files stored on my Ubuntu Box. However my Ubuntu box refuses to play any media files stored on the Windows Box.

I can see all of my shared files and happily browse my shared files. But no media player seems to like to play them.

I was using Dapper - which would stream from the windows box using Rythm Box - but one day the program crashed - and I could no longer do this. I upgraded to Edgy - and still no luck.

Tried re-installing Rythm Box Player - still does not work. I have tried Amarok, Beep and VLC - and all crash when trying to play media files from my network.

Before I end up binning Ubuntu and going back to my "borrowed" windows install disc - can anyone shed some light on how I can get my ubuntu machine to play media files from my windows box?

---

### Post by b3tzi on 2006-11-29
What kind of media files?

---

### Post by cdinoz on 2006-11-29
Any media files - mp3 - mpeg .avi etc etc

I have to transfer the file onto my HDD on my Ubuntu box - and play them from there - its such a pain in the backside.

I cannot play ANY networked media files ](*,) ](*,) ](*,)

---

### Post by drphilngood on 2006-11-29
> **cdinoz said:**
> My Windows box happily will play any media files stored on my Ubuntu Box. However my Ubuntu box refuses to play any media files stored on the Windows Box....

Since you say that you can play the media stored on your Ubuntu box with both Ubuntu and Windows, why not just store the media on the Ubuntu box?  Conversely, you could use an external HDD formatted with FAT32 for your media and just swap it between your boxen.

---

### Post by dbrine on 2006-11-29
these are the kinds of things that makes it discouraging to use Linux. No offense but that always seems to be an anwser someone gives. store the files on the linux box. It doesn't fix the problem. It should matter where the files are. Windows doesn't care so....???? I feel your pain. I had a problem with an older version that would play from a windows network share either (no supported at time , now is). I think we would have a better following if everyone (most) stuff was more straight forward when problems occur.

---

### Post by cdinoz on 2006-12-20
I have actually given trying to share my windows stored media files on my linux box. It does kinda defeat the object that the PC I am using as my linux box was the product of bits of pc's being thown out - and now I am going out to buy a new HDD for it (only has a 10gig 6 year old HDD currently) - and was kinda hopin to stream my files to it over my network as a jukebox PC in the living room.

You are quite right - its this that puts people off Linux. Can someone fix it please on the next release of Ubuntu?:rolleyes:

---

### Post by marinovs on 2006-12-20
Why would I have to store my music from my eternal harddrive to my laptop which is running Linux so I can play MP3's etc? Or is this thread totally different?

I need help trying to get my Mp3 music from my harddrive to play on my laptop...what should i do? ( New User to Linux )...my windows is crashed on this laptop hence using linux

---

### Post by Xanthomryr on 2006-12-21
Did you mount the files on your Windows Box, if not do it.

---

### Post by paddy2706 on 2006-12-21
It depends how you mount the shared folder.
If you use gnome-vfs (the built-in network folders viewer in gnome) you will have to use a player that supports gnome-vfs or install the referring plugins.

if you mount them via smbfs or similar you shouldn't have any trouble using any player.

---

### Post by darrenm on 2006-12-21
Yep exactly. You need to add an entry in /etc/fstab to mount the SMB share. It will work fine then.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28mount%29](https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28mount%29)

---

