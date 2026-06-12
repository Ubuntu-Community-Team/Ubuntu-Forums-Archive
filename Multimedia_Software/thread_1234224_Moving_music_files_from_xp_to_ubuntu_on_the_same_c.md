---
title: "Moving music files from xp to ubuntu on the same computer"
date: 2009-08-07
forum: Multimedia Software
---

### Post by Aarondesktop on 2009-08-07
I just began using Ubuntu two days ago. So I'm very new. I love everything about it so far but I don't have my music on it. My other operating system is XP. I have about 11GB of music on there and really want to transfer it. Any suggestions?

---

### Post by HappyFeet on 2009-08-07
Just go to Places>your XP drive>documents and settings>username and find the music. Just cut/copy and paste them to your ubuntu drive.

Btw, welcome to ubuntu, and don't hesitate to ask any and all questions you may have. Patience is the key. We were all noobs at one time.

---

### Post by Aarondesktop on 2009-08-07
thanks buddy

---

### Post by ajgreeny on 2009-08-07
Or alternatively, but perhaps a bit more difficult for a new user, though useful to know for future, you could make a separate NTFS /music partition and share it between both OSs.  This would save the duplication of your 11GB on both systems.  You could do this with all your data if you prefer by making a new separate NTFS /data partition.  If you have masses of photos, which seems quite normal these days, you may have many more GBs of data worth sharing.

---

### Post by Aarondesktop on 2009-08-07
how would I go about making the share?

---

### Post by ajgreeny on 2009-08-08
You could do it using gparted on the live CD, but before that run the command ```
sudo fdisk -l
``` in terminal and report the output here and also that of ```
df -h
```which will tell us first the partition layout on the computer, then the space free and available to make a new partition to share.

---

