---
title: "Samba share subfolder permissions?"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by new2linux09 on 2009-08-06
Hello,
I have read alot of tutorials on created read or write only access to the primary shared folder. So I hope I have not missed something already discussing this. I am trying to create a public share through samba that has read access for the primary shared folder and write only access for sub folders. I've been able to create a read folder and sub read / write folders but not a write only folder. I've ran "sudo chmod 733 /dir path" for the secondary folder but when trying to add files i get an access denied message. 

My smb.conf file has at the end...

[share-test]
        comment = share-test
        path = /home/share-test
        browseable = yes
        guest ok = yes
        read only = no
        create mask = 0755


I am running Xubuntu 8 and am accessing the shares from an XP Pro box. 
Any suggestions??

---

### Post by swerdna on 2009-08-07
Can you elaborate: what does "write only" mean?

---

### Post by new2linux09 on 2009-08-07
I want to be to write a file to that folder without listing its contents. In other words I can drag and drop a file to that folder but i cant open it. Similar to the public share drop box on an Apple. File permissions should allow it but I cant get it working on a subfolder only a folder that has been added and listed within the smb.conf file will work. 
So what I am wanting is a shared folder where it will open and list its contents such as several folders with different categories. Those folders wont open but can have files added to them. Thus the write only permissions. 

I hope this helps. I would really like to get this resolved on my file server.

---

### Post by new2linux09 on 2009-08-07
Anyone have any ideas on this???

---

