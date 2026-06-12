---
title: "Need help with MythTV AV Media Server"
date: 2011-05-21
forum: Mythbuntu
---

### Post by mackgm on 2011-05-21
I am running mythtv 0.24 with KUBUNTU 11.04
I do not have a TV tuner or a remote to date because I am just testing video and music.
 
I want to view my videos on a DirecTV HR23. I have Tversity set up and it works well but it requires me to run a windows xp machine.
 
When I scroll the menus on the HR23 I can see the MythTV AV Media Server but when I select the recordings folder I get a message that there are no files. I have changed the directory for recordings in my MythTV BE and all my videos are in the mpeg 2 format.
 
I would like to know where to find a how to that explains this operation or if some one can tell me how to fix the problem that would be great. :confused:
 
Just to add, I am new to MythTV and Unbuntu but I have been developing on windows machines for years.
 
Thanks,
Mackgm

---

### Post by azmyth on 2011-05-22
Are you using a samba share? I assume you must of correctly set this up if you can see the folder on your directtv STB. Have you checked the permissions of the folder and video files?

---

### Post by mackgm on 2011-05-22
Yes I am using a samba share. I can access all the files from any PC in my house on the shares. Tversity actually aceesses the Samba shares and I can watch the videos on my Directv unit that way. I have set the permissions to allow anyone to read and write the video files.
 
Does this help? I appreciate your help.
Mackgm

---

### Post by azmyth on 2011-05-22
Doesn't look doable at least with samba as people are seeing the same issue as you -- no files.

[http://ubuntuforums.org/archive/index.php/t-1057398.html](http://ubuntuforums.org/archive/index.php/t-1057398.html)

I'd probably see if a nsf mount would work since you can specify the mount type and I would guess directv box doesn't like the file type on the smb mount.

---

### Post by mackgm on 2011-05-22
Thanks for the link I am going to try what they did and see if it works.

Mackgm

---

