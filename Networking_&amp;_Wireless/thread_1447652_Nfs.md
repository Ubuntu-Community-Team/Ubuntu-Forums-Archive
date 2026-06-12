---
title: "Nfs"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by theozzlives on 2010-04-05
I'm tired of Samba not working. I want to switch to NFS but a have one Windows 7 box. Suggestions?

---

### Post by drdos2006 on 2010-04-05
If you are running Windoze then you will need Samba. Why isn't Samba working ? I found that for me I had to install other libraries relating to Samba to get Samba working properly. I installed anything and everything remotely related to Samba to get Samba to work.
regards

---

### Post by theozzlives on 2010-04-05
> **drdos2006 said:**
> If you are running Windoze then you will need Samba. Why isn't Samba working ? I found that for me I had to install other libraries relating to Samba to get Samba working properly. I installed anything and everything remotely related to Samba to get Samba to work.
regards

I heard there was a Unix protocol that allows NFS to marry and play nice.

---

### Post by bab1 on 2010-04-05
> **theozzlives said:**
> I'm tired of Samba not working. I want to switch to NFS but a have one Windows 7 box. Suggestions?

I believe that Windows uses Subsystem for Unix-based Applications (SUA) and that NFS can be used.  See [_here_]("http://social.answers.microsoft.com/Forums/en-US/w7programs/thread/dac033e7-662c-4290-94cf-e3005e1720c0").

If it works let is know.

---

### Post by theozzlives on 2010-04-05
> **bab1 said:**
> I believe that Windows uses Subsystem for Unix-based Applications (SUA) and that NFS can be used.  See [_here_]("http://social.answers.microsoft.com/Forums/en-US/w7programs/thread/dac033e7-662c-4290-94cf-e3005e1720c0").

If it works let is know.

That helped. but I still need an easy way to convert from SAMBA to NFS. I have all my shares on my headless server in my smb.conf file. Does NFS have a conf file that would allow me to do the same thing? Sorry, Linux+ is my next class.

---

### Post by bab1 on 2010-04-05
> **theozzlives said:**
> That helped. but I still need an easy way to convert from SAMBA to NFS. 
I have all my shares on my headless server in my smb.conf file. Does NFS have a conf file that would allow me to do the same thing? Sorry, Linux+ is my next class.

Sorry?  What have you done to try and educate yourself?  See [**[B]_here_**[/B]]("http://www.google.com/search?q=NFS&btnG=Go!").

---

### Post by theozzlives on 2010-04-06
> **bab1 said:**
> Sorry?  What have you done to try and educate yourself?  See [**[B]_here_**[/B]]("http://www.google.com/search?q=NFS&btnG=Go!").

A simple Google search on NFS is NOT what I'm looking for! I've studied the Windows Networking model, the OSI Model, but the down to earth Linux is yet to come. I just want a clean cut way to network my Ubuntu laptop, my Ubuntu server, and my Windows 7 machine using NFS. If that's to much to ask, then I'm sorry to have been a part of this community since 2007.

---

### Post by lisati on 2010-04-06
I have found [this Samba tutorial]("http://ubuntuforums.org/showthread.php?t=202605") helpful using four different machines, a handful of versions of Ubuntu and three different versions of Windows.

---

### Post by theozzlives on 2010-04-06
> **lisati said:**
> I have found [this Samba tutorial]("http://ubuntuforums.org/showthread.php?t=202605") helpful using four different machines, a handful of versions of Ubuntu and three different versions of Windows.

I want NFS! NOT Samba... Samba don't work right now. I get this when I try to install NFS:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nfs


---

### Post by netztier on 2010-04-06
> **theozzlives said:**
>  If that's to much to ask, then I'm sorry to have been a part of this community since 2007.

Since 2007? Wow. I am certain that of course know your ways around [https://help.ubuntu.com/](https://help.ubuntu.com/) and that - without the slightest doubt - you entered "NFS" as a very simple search keyword right there, only to find...

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

... as the first link in the results list. And of course, glancing over that pretty exhaustive entry in Ubuntu's help wiki, you did not overlook the section about "Minimalistic NFS Set Up" at the bottom of the wiki entry, did you?

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)


regards

Marc

---

