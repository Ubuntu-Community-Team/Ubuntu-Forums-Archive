---
title: "Sharing files in ethernet network ubuntu 9.04"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by GiantSpider on 2009-09-20
I have Ubuntu 9.04 installed on three desktop computers. Two of which I installed via gpartition and a cd. The third I used daemon tools and wubi. I have internet connection on all three. 

The main reason to network the computers is to backup files. I have a dual boot with windows on all 3. The three Windows computers can share files. I want to take my personal data from the windows partition to the Linux. The Ubuntu side of the boot can't share with any other computer, but, have internet.

---

### Post by james_newbie on 2009-09-21
I have a similar problem and hope somebody can help us.

My hard drives always have an ntfs data partition where all my downloads, photos, music etc. are stored . This allows me to reinstall an OS without losing my data. I can use this partition from either OS. Ubuntu can see all of my Windows shared files but Windows cannot see my "shared" Ubuntu folders either. 
If I want to backup those files to another computer, I boot Windows and both Ubuntu and Windows  computers on the network can see the data drive, and I can backup the files to the data drives on any other computer on the network.

Good luck to both of us!

---

### Post by GiantSpider on 2009-09-21
I turned on sharing for one file. I had to install sharing services. After I was finished turning on sharing for that one file I looked at my Vista computer. It said one unknown device was on the network which I'm pretty sure was the Ubuntu shared file. How do I set the workgroup in Ubuntu? I changed my at home network to a different name than the default for my Windows computers.

The ubuntu computer can see itself. I can access my shared documents, its just it can't see the other computers and those computers can't see it. By default it looks like it put the Ubuntu computer in the Workgroup workgroup.

---

### Post by joelgsf on 2009-09-22
The easiest way is installing Samba, if not installed, and configuring it to share files, folders, printers, and other resources.
To know if you have Samba installed or not get to a terminal and do
```
~$ smbd -V
Version 3.3.2
```
If you get a version answer such as above Samba is installed. If not install it with
```
~$ sudo apt-get install samba
```
You need now to configure it to suit your needs. This may be done just by editing its configuration file "/etc/samba/smb.conf", or using a GUI configuration program for the job. I prefer myself to configure it manually - you have full control.
See [[COLOR="Blue"]Ubuntu documentation with this respect[/COLOR]]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/windows-networking-introduction.html"). There is a short tutorial which will help you "do the trick".
Happy sharing!

---

### Post by Iowan on 2009-09-22
[Here]("http://ubuntuforums.org/showthread.php?p=7979230#post7979230") is a helpful How-To you may want to see *after* you install Samba.

---

### Post by james_newbie on 2009-09-23
Thanks for the help. I am now able to share between Ubuntu and Windows.

I edited the smb.conf file adding the line "usershare owner only = false" and changing the line "workgroup = WORKGROUP" to my own workgroup.

But now I have this extra WORKGROUP . How can I delete it?
Thanks again.

---

### Post by Iowan on 2009-09-23
My understanding is that it *should* go away, once the Master Browser eventually notices that it is not there.

---

### Post by james_newbie on 2009-09-24
Thanks Iowan. It did go away but it took some time!
Now that everything is running smoothly, I want to replace Ubuntu with XUbuntu on one of my older network computers:). That will be another challenge!

---

