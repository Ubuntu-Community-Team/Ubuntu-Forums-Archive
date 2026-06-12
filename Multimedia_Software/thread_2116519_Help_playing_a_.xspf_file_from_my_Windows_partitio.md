---
title: "Help playing a .xspf file from my Windows partition"
date: 2013-02-16
forum: Multimedia Software
---

### Post by 412toby on 2013-02-16
Hey Ubuntu Forums,

I have Ubuntu 12.10 and Windows 7 installed on my hard drive on separate partitions.  I also have Ubuntu automatically mount the Windows partition on startup, using "NTFS Configuration Tool".  Whenever I attempt to open a .xspf from  my Windows partition (using VLC), I get errors like so in VLC ```
File reading failed:
VLC could not open the file "/C:/Users/Tobias/Music/01 Harlem Shake.mp3". (No such file or directory)
Your input can't be opened:
VLC is unable to open the MRL 'file:///C:/Users/Tobias/Music/01%20Harlem%20Shake.mp3'. Check the log for details.
```
I understand that the .xspf is literally just a list of song locations and that Ubuntu doesn't read "C:/Users..."  My question is would it be possible to use this .xspf on both Windows 7 and Ubuntu, either making Ubuntu just read the "C:" as "/media/Windows_7" or would a different file type of playlist work for this problem?  I would like to keep the playlist on my Windows partition so I can access and change it from both Ubuntu and Windows 7 without having to copy and paste it whenever I change something.

Thanks much, ask if you need any more information

412toby

---

### Post by guyr34 on 2013-02-16
You can create a link :
sudo ln -s /media/Windows_7 /C:

---

### Post by ron999 on 2013-02-16
> **412toby said:**
> ...  I would like to keep the playlist on my Windows partition so I can access and change it from both Ubuntu and Windows 7 without having to copy and paste it whenever I change something...

Hi
This is tricky.

When you create or edit an xspf playlist using Windows it records the file locations on the playlist like this:-
> <location>file:///C:/Documents%20and%20Settings/Administrator/Desktop/The_McCoys-Hang_On_Sloopy.m4a</location>
Same as in your error message
> VLC is unable to open the MRL 'file:///C:/Users/Tobias/Music/01%20Harlem%20Shake.mp3'

But if you create or edit an xspf playlist using Ubuntu it records the file locations on the playlist like this:-
> <location>file:///media/690DC2637F6B1E28/Documents%20and%20Settings/Administrator/Desktop/The_McCoys-Hang_On_Sloopy.m4a</location>

Maybe it's not possible to use the same xspf playlist for both systems.

---

### Post by 412toby on 2013-02-16
> **guyr34 said:**
> You can create a link :
sudo ln -s /media/Windows_7 /C:

This worked!

Thanks!

---

