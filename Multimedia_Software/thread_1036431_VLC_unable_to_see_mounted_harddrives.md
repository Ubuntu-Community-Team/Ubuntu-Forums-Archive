---
title: "VLC unable to see mounted harddrives?"
date: 2009-01-10
forum: Multimedia Software
---

### Post by Nitrius on 2009-01-10
So i just downloaded VLC, but it looks like it's unable to see my mounted storage drive, it's NTFS. Though dragging files over from the disk into the player or right-clicking the file to play it in VLC works just fine. But am unable to browse to the harddrive from within the VLC player. Is this possible to alter?

---

### Post by mikewhatever on 2009-01-11
Do you get any errors? What happens exactly when you try browsing to the drive?

---

### Post by Nitrius on 2009-01-11
Nothing, because i cant see them at all through the "open file(s)" option in VLC. All i see is the partition which Linux is installed on.

---

### Post by Dr Small on 2009-01-11
Did you mount the NTFS partition to a directory somewhere?

---

### Post by mikewhatever on 2009-01-11
Can you post the outputs of the following commands:
sudo fdisk -l
df -h

---

### Post by Green_Grenade on 2009-01-11
I have to exact same problem.. I just went the long way around.. like.. thro the harddrive found the video and just opend it that way.. 
I loaded Movie Player and it reads the harddrive.. havent had a problem with it..

---

### Post by mikewhatever on 2009-01-12
> **Nitrius said:**
> Nothing, because i cant see them at all through the "open file(s)" option in VLC. All i see is the partition which Linux is installed on.

I suspect you don't see them because you don't know where to look. Partitions are usually mounted in /media, so try navigating there.

---

### Post by madmaxnj on 2009-01-22
I have a similar/same thing.  I connect to my iomega home network drive from the Places menu.  I setup a bookmark to ftp login to the nas.  I can navigate to the nas and double click images or music and it works fine.  Video (.mpg) files is a different story.  If I double click the default movie play opens and then I get an error message.  The delay between double clicking and the error message is proportional to the file size, so I think its trying to buffer the entire file locally before something gives out.  If I copy the .mpg to the local hard disk and it plays fine.  I figured I needed a better player than the one built-in to the default 8.10 install.  I looked around and VLC seemed like the way to go.

I have the same problem that from the File-Open I can only see the local hard disk.  Since my nas is setup as an FTP, it doesn't show up as a local folder (at least not to my knowledge).

If I go to the ftp folder and right click on the .mpg and do play with vlce, then vlc tries to open it and I'll see a couple of frames and then vlc closes.  No error message, it just acts likes its the end of the file.  

I'll keep an eye on this thread to see if anybody knows how to fix our woes.

---

