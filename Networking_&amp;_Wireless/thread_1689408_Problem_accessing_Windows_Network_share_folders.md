---
title: "Problem accessing Windows Network share folders"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by Bastik on 2011-02-16
Hello,

I'm using Ubuntu 10.10 since 2-3 weeks. First I tried live CD and the OS seems to be very good. So i installed it on my laptop. 
So far i had no problems until I tried to access the shared network folders of my Server running on MS Windows Vista and another trial PC running WindowsXP. I'm trying to solve this since 2-3 days, I haven't found a solution.

1st of all my network works fine. All computers can ping each other and as the laptop had Windows XP installed the server was accessable.

1st I installed the SMB4k tool with this program. I could see the computer names, but as soon as I select a Windows computer the tool searches and nothing happens.

After this I tried the mount the Windows share folders with the bash terminal.
My shared folder is called "public"
Command:  
sudo mount.cifs //192.168.111.242/public /home/bastik/public
Error:
sudo: /etc/sudoers is mode 0640, should be 0440
sudo: no valid sudoers sources found, quitting

I tried a lot of different variations of this command but in the end I receive this kind of error. I also tried to add -o user=username pass=password, nothing changed.

After this I searched information about this error, some forum threads I googled are telling the SMB4K tool modifies the /etc/sudoers file and cause this error. So i tried to change it back with some kind of sudo chmod 0640 etc/sudoers but this won't work it seems I can not modify or edit thisw file using sudo.

With the pyNeighbourhood tool I could only see my Laptop but not the Windows PCs.

At the end I will install Linux systems on all of my PCs, but only if all my tests will pass :).

Thanks for tips and help

Best regards

Bastian

---

### Post by piedro on 2011-02-26
Hi! 

It's simple to fix ... and yes: smb4k is broken! 

lokk here to fix your problem: 
solution & more links 

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10434031](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10434031)

good luck, 
piedro

---

