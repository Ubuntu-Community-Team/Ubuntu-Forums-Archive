---
title: "trying to add samba shared printer from ubuntu to ubuntu"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by fibo112358 on 2009-03-16
Hello,

I have a printer connected to my desktop shared with Samba. My wife's Vista laptop can access and print to the printer fine, so I know it's working. I have a laptop running Ubuntu 8.10, and I am trying to add the printer remotely. I go to System->Printing and try to add a new printer. It detects my Workgroup, Desktop, and then printer, but prompts me for some kind of authorization. I tried all username/password combinations on both machines for this authorization prompt, but nothing works. The job just sits in que with the message "held for authorization". Is there another procedure for adding this printer (I am using the Windows via Samba option in the printer configuration)? I would appreciate anyone's help in getting this going. 

-112358

---

### Post by lindsay7 on 2009-03-16
Do you have Firestarter installed on your Ubuntu machine, is so you need to turn of the firewall. I always forget to do this and my print jobs are held.

---

### Post by inobe on 2009-03-16
[https://help.ubuntu.com/community/SettingUpSamba#Sharing%20CUPS%20Printers](https://help.ubuntu.com/community/SettingUpSamba#Sharing%20CUPS%20Printers)

:)

---

