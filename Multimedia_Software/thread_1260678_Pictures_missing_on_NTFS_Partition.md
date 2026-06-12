---
title: "Pictures missing on NTFS Partition"
date: 2009-09-07
forum: Multimedia Software
---

### Post by aaalunchbox on 2009-09-07
I have a a secondary internal hdd formated NTFS that contains backups and what not from my windows 7 machine. I have it mounted in jaunty ubuntu in my fstab file. 

```

/dev/sdb1        /media/SATA    ntfs quiet,defaults,rw 0 0

```

I can see all my files in ubuntu except for one folder that contains a large photo backup. I can see the folder, but it appears empty. I know there should be pictures in there. I have other folders that contain lots of pictures and i can see them all fine, but that one seems to have problems.

I also have a buddy who installed Wubi on his Windows 7 machine. He mounted his NTFS partions in his fstab file with the same settings i used and he has a folder with photos that he cannot see the files in.

Has anyone else run into this problem? Or is there any programs that i can use to do a sector scan to see if it can find the files? I'm kinda suspecting a permission problem.

Also, i've seen articles about ntfs-3g. Is is supported in Jaunty? Might give it a shot if it is.

Any help is welcomed. :)

---

### Post by HappyFeet on 2009-09-07
ntfs-3g is already installed for you. If it was not, you would not be accessing your windows drive. ;)

You don't have to mount anything these days using your fstab. All that stuff is handled automatically now. As soon as you install ubuntu, all you have to do is go to places>your windows drive, click it, enter password, and it will auto mount and you will have access. You may have messed things up by fiddling with fstab. I have done many dual boots lately, and never once had to edit fstab to have full access to a windows drive or partition.

If you don't believe me that ntfs-3g is already installed, look for it in synaptic. It is there.

---

### Post by alienclone on 2009-09-07
are you looking in the correct picture folder? i dont know about W7 but i noticed that Vista has multiple "my pictures" folders, only one of them is the correct one and the others are hidden and empty but when mounted in linux all hidden folders are shown.

---

### Post by aaalunchbox on 2009-09-07
The drive was not connected durring the initial install. It did appear in Places when it was re-connected, but i added it to fstab so that i wouldn't have to re-mount it every time i logged in.  Still, it seems odd that it only seems to effect photo folders. But i do see that ntfs-3g is installed. 

My friend who has the same problem has ubuntu dual booting on the same drive with windows 7 and his windows partition was not automaticaly added. Thats why i added it to his fstab file, but he is having the same problem not seeing photos in a large picture folder.

---

### Post by aaalunchbox on 2009-09-07
Its the correct folder. Its in the root. There are no OS files on that drive. It was only used for file storage.

---

