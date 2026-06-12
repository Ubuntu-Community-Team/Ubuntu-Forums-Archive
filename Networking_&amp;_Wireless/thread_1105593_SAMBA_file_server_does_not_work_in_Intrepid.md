---
title: "SAMBA file server does not work in Intrepid"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2009-03-24
I just put Ubuntu 8.10 on my machine recently, as I was really sick of openSUSE and wanted to see if Ubuntu would work on my machine now. The good news is Ubuntu works, however Samba is not working correctly. I should preface all this by saying I have an AMD 64-bit system, SATA hard drive.

OK, so I installed all the SAMBA server packages: cifs, smbfs, samba, all that stuff. Initially I set the folder to shared from the user level of nautilus (I'm sharing my home folder). I then read something about having to open nautilus as root, then sharing the folder, so I did that as well, so the folder is shared on the user and root level. I also entered ```
smbpasswd -a dan
``` to set my username and all that. However, when I use my laptop and browse the network, my desktop machine does not show up at all, meaning my SAMBA service is not running for some reason. The shared printer works fine, however, using CUPS. What is the issue here and how can I go about troubleshooting and resolving it?

Thanks,
Dan

---

### Post by dajasc on 2009-03-24
Just because you can't see it when browsing doesn't necessarily mean the service isn't running.  I'm having a similar problem.  It's running, I can connect from a windows machine by typing in \\192.168.100.202 (the address of the Ubuntu machine) and see all the shares.  But, when browsing it never shows up.

I've put my problem out on the forum, no one seems to know what the problem is. 

I'm not saying yours is definitely running but from your description it could be like mine, running but not easily visible.

---

### Post by dbsoundman on 2009-03-25
Thanks, that seemed to be at least part of the problem. Now, on the actual server, I can view the share. However I still can't connect from another machine. Right now I have the folder shared only at the root level (not at the user level) as dan-home. So I go to another linux machine and type in: ```
smb://192.168.2.2/dan-home
``` in the nautilus location bar, and I get nothing. I tried pinging the IP and it's all good, and print sharing works fine. Is there something I'm missing on the server's configuration files that I need to address maybe?

-Dan

---

### Post by inobe on 2009-03-25
samba setup is a lot different in ubuntu, i have had opensuse since 9.2 !

it's a whole new ball game [https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

several steps to have a fully functional network

---

### Post by dbsoundman on 2009-03-25
I undid my previous share attempts and tried using the "shares-admin" tool as described, but it still doesn't work. I have restarted samba each time I change things as well to make sure it's set up properly.

-Dan

---

### Post by dajasc on 2009-03-25
When you try to connect from another machine what does it do?  Prompt for a password or just never find the samba server?

---

### Post by dbsoundman on 2009-03-25
It never finds the server, just times out eventually.

-Dan

---

