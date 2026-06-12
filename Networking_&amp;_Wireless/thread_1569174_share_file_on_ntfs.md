---
title: "share file on ntfs?"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by kokanidja on 2010-09-06
i have a partition that i have ubuntu file sistem on, and couple of others that are NTFS because it had windows before. i tried to share an old folder from one of NTFS partitions but couldnt...could not change permissions on right click. Also could not change using 
sudo chmod.... nothing changed permissions.

---

### Post by howefield on 2010-09-06
Can you clarify what you want to do ?

If it is to access files on an NTFS partition whilst using Ubuntu, you should be able to do that by going to the places menu and selecting the appropriate option. There is no need to change permissions or "share" for Ubuntu to read NTFS.

---

### Post by sikander3786 on 2010-09-06
Are you trying to share the folder on network via Samba? Why do you want to change the permissions on that?

---

### Post by kokanidja on 2010-09-08
what can't you understand? Yes i was trying to share a folder that's on a disk(or a partition) formated as NTFS. 
(One partition is ext3 and that's where Ubuntu is. Others are NTFS.) hmm, this is probably what yo dont understand. Ext3 and NTFS partitions are all part of one computer powered by Ubuntu. 
There are folders on NTFS partitions. I was trying to share one of them. Of course using Samba how else? This is for Windows powered computers to see.
I see shared folder from a Windows powered computer but i cant access it. Because of permissions that are set the way they are of course.
The problem is that i cant change that permissions! Why?
I tried from GUI..nothing. I was not logged in as root so that might be the problem. Then i tried from terminal (command line) using Chmod command...and again nothing. 
"sudo chmod..." and it looked as it applied that because it did not give me any error but with "ls -l" you see that it did not change a thing.

---

### Post by drdos2006 on 2010-09-08
Sounds to me that Samba is not set up properly. Check your /etc/samba/smb.conf  file to see if the workgroup section is correct. That is your Ubuntu group is the same as your Samba group. I have found that I needed to add group and user access across my Ubuntu network on previous occasions.

regards

---

### Post by sikander3786 on 2010-09-11
> **kokanidja said:**
> (One partition is ext3 and that's where Ubuntu is. Others are NTFS.) hmm, this is probably what yo dont understand. Ext3 and NTFS partitions are all part of one computer powered by Ubuntu. 

Not hard to understand. Too old of a job for Ubuntu and Linux to do by now.

> 
There are folders on NTFS partitions. I was trying to share one of them. Of course using Samba how else? This is for Windows powered computers to see.
I see shared folder from a Windows powered computer but i cant access it. Because of permissions that are set the way they are of course.
The problem is that i cant change that permissions! Why?
I tried from GUI..nothing. I was not logged in as root so that might be the problem. Then i tried from terminal (command line) using Chmod command...and again nothing. 
"sudo chmod..." and it looked as it applied that because it did not give me any error but with "ls -l" you see that it did not change a thing.

That is not definitely a permissions issue. It is an authentication issue. Have you setup any samba user accounts? From which account are you trying to access from the Windows PC.

---

