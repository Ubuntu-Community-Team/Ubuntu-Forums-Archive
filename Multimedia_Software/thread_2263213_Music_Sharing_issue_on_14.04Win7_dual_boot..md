---
title: "Music Sharing issue on 14.04/Win7 dual boot."
date: 2015-01-30
forum: Multimedia Software
---

### Post by JSFord on 2015-01-30
Alright, so I have a laptop dual booting with Ubuntu 14.04 and Windows 7. Everything runs smoothly in both OS's but when I am using the ubuntu side, I can't seem to get any music programs to remember the location of my music library. 

I have 3 partitions, one for the windows OS, one for Ubuntu and one to store other files on to share between the two. I use iTunes on the windows side so all of my music is in my iTunes library on the storage partition. I have tried Rhythmbox and Banshee recently, and in both I can set the music library to the location on the storage drive and it finds all the files no issue, it just takes a little bit (there's about 80Gb worth of music on it). After it finds all the music there are no problems playing any of it until I shutdown/restart the computer. Once It boots back up, the files still show up in the media player but won't play. I have to re-set the location of the music library and then rescan it to get anything to play again.

I'm a bit of a newbie to Ubuntu and Linux in general, but I want to spend more time with the OS and I like listening to music while I do so, so this is pretty much a necessity for me. 
Any help would be greatly appreciated!
Thanks!

---

### Post by TheFu on 2015-01-30
How is the data drive mounted?  In the fstab? If so, it is an issue with the music player. If it is mounted through gvfs - THAT is likely the problem - mount it through the fstab.

---

### Post by speartip on 2015-01-31
As TheFu says, it seems that you will need to mount the partition in the fstab file.
As an eg. I had all my data on ext4 partition sda5. So I named that partition storage & did the following:
```
[COLOR=#000000][FONT=Ubuntu][SIZE=3]sudo mkdir /storage[/SIZE][/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=Ubuntu][SIZE=3]sudo gedit /etc/fstab[/SIZE][/FONT][/COLOR]
```
Then I added this line at the bottom of my fstab file:
```
[COLOR=#000000][FONT=Ubuntu][SIZE=3]UUID=[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][SIZE=3]bf66xxxx-79xx-4xxx-bxxx-5xxx5bf7xxxx[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][SIZE=3] /storage        ext4    defaults        0       0[/SIZE][/FONT][/COLOR]
```
Obviously you need to replace that with your own UUID, & partition info. GParted will tell you what it is.
Then:
```
[COLOR=#000000][FONT=Ubuntu][SIZE=3]sudo mount -a[/SIZE][/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=Ubuntu][SIZE=3]sudo chown -R username:username /storage[/SIZE][/FONT][/COLOR]
```
Using your own User Name of course. Then:
```
[COLOR=#000000][FONT=Ubuntu][SIZE=3]sudo chmod -R 755 /storage[/SIZE][/FONT][/COLOR]
```
Then Reboot.
Hope this is helpful and gives you some idea,  more information can be found here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by JSFord on 2015-02-02
well, I appreciate the attempt to help, but as I said I'm a bit of a newb when it comes this. I tried following the code you gave me, and all I succeeded in doing was making my storage partition disappear from the 'devices' tab under my my file browser. when I restarted it said there was an error mounting storage. I tried reading some other resources and it akk diseb't make much sense to me. If there's any more you can dumb it down to help me understand that would be great. I very much appreciate the help so far!

---

### Post by speartip on 2015-02-02
Ok.
To start with can you tell me what file type you are using NTFS/FAT32/EXT4 etc...
Then what partition your music is on, that you wish to mount SDA1/2/SDB1 etc...

---

### Post by speartip on 2015-02-02
Actually ignore my last post. I have just found a very simple way to do this which I have tried and it appears to work. Check out the following link:
[http://askubuntu.com/questions/123234/how-to-automount-my-windows-partition-at-boot](http://askubuntu.com/questions/123234/how-to-automount-my-windows-partition-at-boot)
Scroll down to "The Visual Way" and follow the instructions using the program "disks" which should already be pre-installed.
Let us know how you get on.

---

### Post by TheFu on 2015-02-02
$ disks
No command 'disks' found.

Modifying the fstab directly, always works. Just sayin'.  Plus, if you ever need to do this on a server, there aren't any GUIs.
Ubuntu how-to: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by speartip on 2015-02-02
disks isn't a command it's a gui program. Ubuntu 14.04 comes with it preinstalled.
If for some reason, you haven't got it installed, you can do so from the software centre or synaptic.
It's called gnome-disk-utility.

---

