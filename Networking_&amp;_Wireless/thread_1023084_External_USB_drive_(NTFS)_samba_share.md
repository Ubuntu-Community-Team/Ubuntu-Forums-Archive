---
title: "External USB drive (NTFS) samba share"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by JBetts on 2008-12-27
Hi all. 

Very new to linux (like a month), but loving it so far. Its taken some steps to learn the basics of the terminal (I come from a Windows network admin background with lots of GUIs) but I LOVE the overall look, feel, and functionality of the kernel/distro. That said, documentation is definitely lacking!...Samba3 HOW-TO and Samba3-by Example are great resources, but a little rough on the learning curve. I have a new Ubuntu 8.10 box. Intel D945GCLF mobo (that I LOVE) that worked right out of the box with no additional drivers. 



OK, Here's my issue:

I have an external 500 GB drive that I want to share out from the linux server to a multi-user, multi-OS wireless network. It was already formatted NTFS, and already has more space used than free space on the linux server's HDD. I have read a TON of forums on the subject, but I am confused as to what the possible solution could be. 


The drive is located at /media/JBetts\ HDD/. I have installed the ntfs-3g driver (via Ultamatix), and can read the drive locally (and checked "enable write to external drive"). I also installed samba and have done a fairly basic setup. Here's the testparm:

[global] 

server string = Jon's Linux Server
security = share
printcap name = cups
show add printer wizard = no 
guest ok = yes

[external drive]

comment = guest access share
path = media/JBetts\ HDD/Archive/

[test] 
comment = test share
path = /home/jon/Documents

[printers]

comment = All Printers
path = var/spool/samba
printable = yes
use client driver = yes
browseable = no


So. I am fully able to read write and execute the test share, print to the attached printer, and view (but not OPEN) the ntfs share of the external USB drive. doing ls -l in /media reveals that the external drive has the following permissions:

drwxrwxrwx 1 root root 4096 ...etc. 

This is true of all the subfolders as well. So, my understanding is that "other" should have full rwx permissions. When I access it from within "Places", I can rwx any file, and have had zero hiccups from day 1. When I go through Network --> Server Name --> Share name, I get the error "Failed to mount Windows share". When I browse to it from a Windows machine on the network, I get the following error: "\\jon-server\External Drive is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.       The network path was not found." 

Do I need to change the owner of the drive location? What the hell are fstab and umask? 



What am I doing wrong? Please explain it to my like I'm a windows user that just happened to fall down the rabbit hole into the world of linux...And if you have any links to any GOOD resources (that don't assume you are already a wiz at terminal commands and *explains* them), I would greatly appreciate it. 


Thanks SOOOO much, and trust me - new users to linux (from Windows) could definitely use this information. 

THANKS!

---

### Post by JBetts on 2008-12-27
Very similar to issue here!

[http://ubuntuforums.org/showthread.php?p=6447686#post6447686](http://ubuntuforums.org/showthread.php?p=6447686#post6447686)


Right after I posted that, I apparently found a solution! I changed three things, and I'm not sure which solved my problem. My current smb.conf (the pertinent part):

[External]

comment = stuff
path = /media/JBetts HDD/Archive
writeable = no
browseable = yes
guest ok = yes

1) I changed path = *from* /media/JBetts\ HDD/Archive 
Maybe path doesn't accept escapes? 
2) I added the writeable = no. 
Maybe this has to be dictated yes or no, as its an external drive? 
3) I checked the "Enable write support for external device" on the NTFS configuration tool (I think accompanied with the ntfs-3g driver). 
Maybe basic write access was keeping me from opening the path? 


It is strange, because my scenario was *verbatim* like yours - able to access locally, with the same error messages. 

Hope that helps!

---

### Post by moeness86 on 2010-09-27
[Here]("http://nixliving.blogspot.com/2009/12/permissions-samba-sharing-external-ntfs.html") is a guide for normal people who dont want to go through the FSTAB permissions file after they have had enough headache from the SAMBA setup

:popcorn:

---

