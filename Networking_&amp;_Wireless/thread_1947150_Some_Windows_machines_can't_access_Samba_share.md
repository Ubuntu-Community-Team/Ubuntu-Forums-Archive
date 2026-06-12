---
title: "Some Windows machines can't access Samba share"
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by Parrallax on 2012-03-26
Hi Everyone,

So I have a media centre running Ubuntu 10.4 with the files on a portable hard drive that I'm trying to share over the network using Samba.

I set it up and everything seemed to work fine, my own laptop can easily find the Ubuntu machine on the network, and access the shared folders.

However when other people try to access it using their Windows laptops it doesn't work. When they click on the network they can find the computer, and they can see the shared folders. But when they try to open one of the shared folders they get the error:

"Network Error
Windows cannot access \\computername\sharename

Check the spelling of the name. Otherwise, there might a problem with your netowrk. To try to identify and resolve network problems, click Diagnose."

Diagnose is predictably unhelpful.

Also oddly they can access a shared folder that's on the hard drive that ubuntu is on, but not the shared folders that are on the portable hard drive.

Any ideas what the problem is here? Why would it work for one laptop and not others? Are there any files I should post here to help figure out what the problem is?

Thanks in advance of any help guys.

Bob

---

### Post by Morbius1 on 2012-03-26
>  So I have a media centre running Ubuntu 10.4 with the files on a  portable hard drive that I'm trying to share over the network using  Samba.What are the permissions on the partition that you are trying to share?
Run the following command to see who owns and what permissions are on that folder:
```
ls -al /path-to-shared-folder
```How is this external HDD formatted - NTFS, FAT32, ext4, ... ?

---

### Post by Insomn1a on 2012-03-26
> **Parrallax said:**
> Hi Everyone,

So I have a media centre running Ubuntu 10.4 with the files on a portable hard drive that I'm trying to share over the network using Samba.

I set it up and everything seemed to work fine, my own laptop can easily find the Ubuntu machine on the network, and access the shared folders.

However when other people try to access it using their Windows laptops it doesn't work. When they click on the network they can find the computer, and they can see the shared folders. But when they try to open one of the shared folders they get the error:

"Network Error
Windows cannot access \\computername\sharename

Check the spelling of the name. Otherwise, there might a problem with your netowrk. To try to identify and resolve network problems, click Diagnose."

Diagnose is predictably unhelpful.

Also oddly they can access a shared folder that's on the hard drive that ubuntu is on, but not the shared folders that are on the portable hard drive.

Any ideas what the problem is here? Why would it work for one laptop and not others? Are there any files I should post here to help figure out what the problem is?

Thanks in advance of any help guys.

Bob


see if you can access the share using the IP address of the machine,

\\IPaddress\sharefoldername

---

### Post by Parrallax on 2012-03-26
Thanks for the replies guys.

Morbius1: all the folders that I'm trying to share have the following permissions:

drwx------ 1 sally sally  57344 2012-03-23 13:41 Movies

sally is obviously the name of the user that's the admin on the machine. Is that what you need?

Insomn1a: thanks for the suggestion. I tried that and got exactly the same result.

---

### Post by Morbius1 on 2012-03-27
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line in the [global] section - right under the workgroup line is where I'd put it:
```
force user = sally
```Save the file and then restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down after a samba restart and see if that resolves the issue.

All remote users after authentication or even if they are guests will be converted to sally as far as your shares are concerned and Linux is allowing only sally access.

---

### Post by Parrallax on 2012-03-27
Brilliant. Thanks so much for that. That fixed the problem :D

---

