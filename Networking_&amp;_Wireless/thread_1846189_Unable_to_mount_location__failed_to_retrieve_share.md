---
title: "Unable to mount location / failed to retrieve shared list from server"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by luizgguidi on 2011-09-18
Hello there

I am pretty new here and to linux and have been searching all day for a solution to this problem without success.

I am trying to put files from my standard laptop which operates Windows XP to my netbook which has Ubuntu 11.04.

I have them connected with a lan cable and I can enter the ubuntu system via windows but it does not work the other way round. When I try to open the windows system from ubuntu the following error appears:

Unable to mount location / failed to retrieve shared list from server

This is issue is discussed in various places but it seems like each case is different so i thought i'd ask for advice on the steps to identify what is wrong here.

I have installed the Samba server and winbind but that has not helped either. Both computers are already in teh same group if that makes any difference.

I would really appreciate help here! 

Thanks

---

### Post by Toz on 2011-09-18
How are you trying to mount the Windows system? What commands/actions are you using?

Does Windows have firewall enabled preventing connections?

Make sure you have **smbfs** installed in ubuntu system. Look for it in the Software Centre or via command line:
```
sudo apt-get install smbfs
```

---

### Post by Morbius1 on 2011-09-18
>  I am trying to put files from my standard laptop which operates Windows XP to my netbook which has Ubuntu 11.04.Is this one time transfer of files or are you talking about a permanent file sharing network?

If you just need to transfer files from A to B then you might consider using Dukto: [http://code.google.com/p/dukto/downloads/list](http://code.google.com/p/dukto/downloads/list)

Place it on the Windows and the Ubuntu machine and transfer away. From their Wiki:
> Dukto is a standalone software, it doesn't need installation, it doesn't  creates any configuration file or registry key on your PC, it doesn't  require any software (apart from the operating system) to run, it  doesn't require configuration or account registration. And it runs on  Windows, Mac OS X and Linux.> Dukto usage is very simple, just start it on the two PC connected over  the LAN (or directly connected). On the buddy list will be showed the  other peer. Now simply drag and drop your files and folders over the  dukto window and they'll be transferred to the other end. That's all. Just to be clear, this isn't a replacement for Samba or any other file sharing protocol as there is  no authentication mechanism involved or permanent mounts. It's simply a very easy way to get files from A to B without any setup.

---

### Post by Gunix on 2011-09-30
Hello
I want your help.

I have a problem my hard disk. Unable to mount location.
I have also downloaded GParted. I go to check at /dev/sdb4 xfs i say this [http://imageshack.us/photo/my-images/52/screenshotunledwindowg.png/](http://imageshack.us/photo/my-images/52/screenshotunledwindowg.png/)

I don't idea and i want my data.

---

### Post by Toz on 2011-09-30
> **Gunix said:**
> Hello
I want your help.

I have a problem my hard disk. Unable to mount location.
I have also downloaded GParted. I go to check at /dev/sdb4 xfs i say this [http://imageshack.us/photo/my-images/52/screenshotunledwindowg.png/](http://imageshack.us/photo/my-images/52/screenshotunledwindowg.png/)

I don't idea and i want my data.

Hello Gunix and welcome to the forums. I think you might have some better luck getting a knowledgeable response by creating a new thread to deal specifically with your problem.

---

