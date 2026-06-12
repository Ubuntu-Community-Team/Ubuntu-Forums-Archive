---
title: "Samba Read Only permissions driving me insane..."
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by tracyandskye on 2010-02-20
I have an Ubuntu server (Mythbuntu 9.10 actually), an Ubuntu 9.10 workstation, and an XP workstation.  

The buntu boxes are networked with nfs and everything works fine.

The XP-buntu networking is with Samba of course.  Browsing is fine, but the files created in these machines are read only from the other machine (that didn't create the file).  I assume my smb.conf file is to blame.  I cut all of the comments out & am posting it below.  Can someone please tell me what I need?



#======================= Global Settings =======================

[global]


   workgroup = voodoonet

   server string = %h server (Samba, Ubuntu)

   dns proxy = no

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m

   max log size = 1000

   syslog = 0

   panic action = /usr/share/samba/panic-action %d


####### Authentication #######


  security = share

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes

   map to guest = bad user

########## Domains ###########


########## Printing ##########


############ Misc ############

   usershare allow guests = yes

#======================= Share Definitions =======================



wins support = yes
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no




[server]
path = /data/server
available = yes
browsable = yes
public = yes
writable = yes
comment = Samba Share

---

### Post by Morbius1 on 2010-02-20
Try adding 2 more lines to the [server] share definition:
> 
create mask = 0777
directory mask = 0777OR
> create mask = 0666
directory mask = 0777BTW, if you ever need to post the smb.conf file without comments, issue the following command in a terminal:
**testparm -s**

---

### Post by tracyandskye on 2010-02-20
The results seem the same for both options; new files created in XP are now available for editing, but existing files are still read only, and new and existing files are still read only for the files created in Ubuntu.

---

### Post by pdc on 2010-02-20
is there anything in these tutorials that is of use to you?

[http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

I believe swerdna is happy for you to email him 

rpm versions are also provided 

[http://opensuse.swerdna.org/susesambaserver.html](http://opensuse.swerdna.org/susesambaserver.html)

---

### Post by Morbius1 on 2010-02-21
> The results seem the same for both optionsI wasn't sure about the intended use of the share. The term "create mask" will force the permissions on newly transfered "files" into the share. 

create mask = 0666 will mark them as read/write to everyone. 
create mask = 0777 will mark them as read/write/execute for everyone. 
The directory mask needs a 777 to allow everyone to open any newly transfered "folder".

> new files created in XP are now available for editing, but existing files are still read only, and new and existing files are still read only for the files created in Ubuntu.What you are describing is the standard way new - locally created - files work for a directory formatted in a linux filesystem. This has nothing to do with Samba. Look at any of the directories in your own home directory, they all have permissions set to something like this: **drwxr-xr-x**
The owner (you) can read and write and all others can only read.

For the existing files/folders in your shared folder you need to issue the following command to set them to read/write for everyone:

Open **Terminal**
Type [B]sudo chmod -R 0777 /data/server

[/B]You will need to do that every time you add anything to that directory from your local machine.

---

### Post by tracyandskye on 2010-02-21
Thanks!  That tutorial was exactly what I was looking for.  Really simplified things &, along with Morbius1, helped me understand how this stuff works.

So all of the new files work well & all of the existing stuff too.  If I understand correctly, if I create a file, save it on a workstation, then move it to the server (instead of saving it on the server in the first place), I will need to run that chmod command if I want it to not be read only.  That should work fine.

One small issue I'm having now is that I don't see these folders when I want to upload files to my website.  There is no network folder in the browser, even though there normally is, and even links placed in my Documents folder don't work for this.  Is there a simple fix for this?

---

