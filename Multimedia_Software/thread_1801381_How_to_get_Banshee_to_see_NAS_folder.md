---
title: "How to get Banshee to see NAS folder?"
date: 2011-07-10
forum: Multimedia Software
---

### Post by shawnerz on 2011-07-10
Hello all.
This may not be a Banshee problem, but I'll ask it anyway.
My music is stored on a NAS on my home network.
I am trying to get Banshee to see my MP3's on the NAS.  It looks like Banshee only will support local folders.
So, is a sym link (symbolic link) in a local folder be the solution?  If so, what's the syntax?  I know the basic form is ln -s <dir 1> <dir 2>.
Ubuntu's file browser sees the folder as 'smb://192.168.1.200/volume_1/level1/level2/level3/MP3's'
I haven't had any success trying to create a sym link to the NAS folder.

Or, am I approaching this totally wrong and can Banshee support the NAS without a sym link?

Thanks in advance,
-Shawn

---

### Post by shawnerz on 2011-07-10
Well, I got it to work, but I'm not sure if it was the easiest way.
First, I installed smbmount.
```
sudo apt-get install smbmount
```
Then I realized that the actual folder that the music is located in on the NAS isn't the folder shared on the network.  I also found that I had to map the NAS in /mnt and not just anywhere. :(
So the syntax was:
```
sudo smbmount //192.168.1.200/level_1 /mnt/remote -o user=myusername
```

You should be prompted for a password.  Mind your password! If you haven't entered the password for sudo, sudo could be asking you for your password.  In this case, you should see, "password for <username>"
Or, you may be being asked for your password on the remote file system.  In that case, enter the remote file systems password.

Once I mapped that location, I Opened the location in Banshee, browsed to the MP3 folder, selected the first folder, then scrolled to the bottom and did a shift-select, and then imported all of the MP3's.
:)
Good luck,
-Shawn

---

