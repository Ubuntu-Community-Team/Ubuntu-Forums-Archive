---
title: "Windows and ubuntu wont talk..."
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by Eleutherios on 2011-08-17
I have two Ubuntu (Natty's) and a windows 7 enterprise box at home, pone of the ubuntu's is a desktop for email client and a ping box... the other i use with a handful of 1T drives for media storage... What i have run into is, Each Ubuntu box can see the Windows 7 box no issue.. but the win7 box cant see the ubuntu's the problem here is the ubuntu storage is where i stream videos from to the win7... er that is would access them... Ideas?

---

### Post by Enigmapond on 2011-08-18
Well I would switch it around as Windows doesn't read ext'anything. You need a tool like ext2read but that will only read them and you would need to copy it to the Win7 in order to use. I would use the Win7 to stream to Ubuntu. I have an NTFS partition I use to share between OS's...

---

### Post by garvinrick4 on 2011-08-18
Are they USB drives?

---

### Post by Eleutherios on 2011-08-18
> **Enigmapond said:**
>  I would use the Win7 to stream to Ubuntu. I have an NTFS partition I use to share between OS's...

I should have been a little more clear. While the OS's themselves on the ubuntu boxes are ext.... the storage is NTSF just for transfering sake. and Gavin, They were installed with a USB drive, as per my usual, however the boxes are full on boxes with seagate or WD 40 gig HDD's for OS's and additional drives as needed. 

I am typically pretty good at this... but i cant seem to find anything that will set ubuntu as 'viewable' to windows.. I am wondering now if there is a go-between program...?

---

### Post by Enigmapond on 2011-08-18
There is no "go-between". Windows will NOT read ext4. That's why I suggested you switch it around.

---

### Post by Eleutherios on 2011-08-18
> **Enigmapond said:**
> There is no "go-between". Windows will NOT read ext4. That's why I suggested you switch it around.

I understand that Windows does not see ex2...3...or4... what iam saying is a go between for windows7 to ubuntu, networking wise, i dont need access to the ubuntu system, i need access to the harddrive that is in the ubuntu 'server'... if you will. as in maping a drive via a specific IP... or what packages are needed to share files over a network that are not default installed with natty... ?

---

### Post by Enigmapond on 2011-08-18
Ok...then I believe you are looking to install Samba which is used for network sharing. If you search the forum for Samba...you will find lots of answers and configs. It sometimes takes some work to get it to function. Hope this helps..

---

### Post by Eleutherios on 2011-08-18
> **Enigmapond said:**
> Ok...then I believe you are looking to install Samba which is used for network sharing. If you search the forum for Samba...you will find lots of answers and configs. It sometimes takes some work to get it to function. Hope this helps..

awesome! Thanks for the input and sorry for all the confusion. Ill give this a try tonight and see what we get.

---

