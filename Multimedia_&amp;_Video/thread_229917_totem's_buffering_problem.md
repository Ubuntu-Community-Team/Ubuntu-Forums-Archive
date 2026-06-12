---
title: "totem's buffering problem"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by true_friend on 2006-08-05
I am ubuntu 6.06 user. using totem to play movies etc. .dat files from my LAN's shared folders. on windows (xp) i can see the movie without any hinderance but in ubuntu totem buffers only 10 sec of movie after showing this part it starts once again buffering. i am very teased by this situation it 
can some one tell me its solution. i also tried to change the networking connection but did not worked instead totem crashes. movie player i installed and tried but i does not opening the files form network.
plz help me.
Regards
True_Friend

---

### Post by ThirdWorld on 2006-08-18
I have exactly the same problem that you have. Looks like nobody knows how to fixed, or if they know they give a damn about new users, thats typical in this forum. I dont use totem to stream video i use gxine movie player.

---

### Post by ewerx on 2006-08-18
I was connected to my Windows XP machine's shared folders using Nautilus to connect to the SMB share. When I played MPEG video files on the Windows share (by accessing them through smb://blah) using Totem I got this buffering problem.

But then I actually mounted the Windows shares in fstab, and when I access the shares through the mounted dir (/mnt/blah or /media/blah), the problem is gone and the video plays smoothly (even over 802.11g wifi).

I also installed MPlayer using Automatix and I prefer this player to Totem (not as pretty, but more advanced).

---

### Post by funchords on 2006-08-18
When copying files from an SMB share, I get 5x to 8x the average speed that I get when using Totem, even when Totem is refilling the buffer. 

I tried to mount an smb drive into /mnt, but struggled with the smbfs options and could not find the smbmount program that mount's man page referred to.

> **ewerx said:**
> But then I actually mounted the Windows shares in fstab, and when I access the shares through the mounted dir (/mnt/blah or /media/blah), the problem is gone and the video plays smoothly (even over 802.11g wifi).

Can you show us what you added to fstab?

---

### Post by ewerx on 2006-08-18
> **funchords said:**
> I tried to mount an smb drive into /mnt, but struggled with the smbfs options and could not find the smbmount program that mount's man page referred to.

Can you show us what you added to fstab?

I just followed the directions here:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by funchords on 2006-08-18
> **funchords said:**
> When copying files from an SMB share, I get 5x to 8x the average speed that I get when using Totem, even when Totem is refilling the buffer. 

I tried to mount an smb drive into /mnt, but struggled with the smbfs options and could not find the smbmount program that mount's man page referred to.

Ah, figured it out (at least for me), thanks to some more searching...

```

     sudo apt-get install samba
     sudo apt-get install smbfs
     sudo mkdir /mnt/topol002
     sudo mkdir /mnt/topol002/video
     sudo mount //192.168.177.102/video /mnt/topol002/video

```

Between the first two lines, one or the other may not be necessary.  You might try this just with smbfs (starting on the 2nd line).

If you need to use another username/password, or to see how to make this permanent, then see this FAQ answer and the next 3 that follow it...

[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read")

---

### Post by H.E. Pennypacker on 2006-09-03
I see we're all in the same boat.  So far, I know of four people (that includes me) who describe Totem as been terrible when it comes to buffering (it buffers way too much), and it crashes when trying to change the connection speed under Preferences.  

This deserves a Launchpad report.  To all those who suffer from this, please report it using Bug Buddy to Gnome developers.  Many more people may be experiencing the same problem.  Silence won't change anything.

---

### Post by wataboutbob on 2007-03-12
actually this is a problem that has cropped up for me since yesterday. Don't have a clue why. I used to be able to happily watch movies even over WiFi, but since yesterday, even if I'm connected via Wired, I've started to get this issue with Totem's 10 sec buffering.

---

