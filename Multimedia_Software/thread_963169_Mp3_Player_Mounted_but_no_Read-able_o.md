---
title: "Mp3 Player Mounted but no Read-able? :o"
date: 2008-10-30
forum: Multimedia Software
---

### Post by emoric on 2008-10-30
Hello :KS

I have a very quick question I would like to ask about mp3 players. Now, I have mounted my Sansa Clip mp3 Player but the only problem is that I can not read the files on it! :o

Now, I know I have music on there becouase I listen to it everyday. :lol:

So, my question is... how do I get Ubuntu to read my music? Ubuntu 8.04

I searched and I did not find my answer anywhere. :(

[IMG]http://i34.tinypic.com/wtg6d1.png[/IMG]

---

### Post by cariboo on 2008-10-30
There are several pages of posts concerning this same problem. Have a look here:

[http://ubuntuforums.org/showthread.php?t=895226&highlight=sansa](http://ubuntuforums.org/showthread.php?t=895226&highlight=sansa)

Post #2 has what you need.

Jim

---

### Post by emoric on 2008-10-30
Well, I don't really think that helped :lolflag:

Like I said, I see it on my desktop, and all my music players recognize it. Its just the simple fact that I just can't see the .mp3 files inside the device. Yes, they are there.

So what am I missing?

:/

---

### Post by EnlightMent on 2008-10-30
I am having the same problem. When I load songs onto my mp3 player under ubuntu 8.04 my mp3 player is unable to reqonize the files, but ubuntu see them on the device. when I reboot into winxp windows is unable to see the files on the device but reconizes the space being used.

what do I have to do so my mp3 player will see my songs loaded using ubuntu?

---

### Post by forger on 2008-10-30
Report a bug? [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

---

### Post by forger on 2008-10-30
1) Unmount your player, wait 10-15 seconds
2) Remount it, wait a minute or so

go to terminal and execute these commands:
```

lsb_release -a
mount
df
sudo fdisk -l
lsusb
dmesg|tail
```

Reply with the output and consider filing a bug report with this information

---

### Post by spaleo on 2008-11-08
I read carefully the posts about mounting an mp3 sansa clip, without figuring out a solution for mounting a SANSA clip AND playing music

My computer mount automatically it as MSC device;
I edited the file on /media/SANSA \ CLIP

.is_audio_player

audio_folders=MUSIC/
folder_depth=99
output_formats=audio/x-ms-wma,audio/mpeg,audio/aac,audio/mp4 

but it does not work, i.e. I'm not able to play the file I put in.


I then switched to MTP ( I did an upgrade of the  libtmp) but 
I cannot mount it. I tried using lsusb and I also tried a series 
of suggestions (touch the central bottom...) without succeeding 


any suggestion is welcome

thanks

---

### Post by DarKnyht on 2008-12-01
I think I understand what your problem is.  If I understand you correctly you connected the Clip to Windows and loaded music?  

If you connect it to Windows under MTP, the files are stored in a hidden directory that MSC cannot see.  You will have to remove the files using Windows and switch the player to MSC Only mode, then re-add the files.

The MTP mode in Linux is flaky and doesn't work properly.

---

