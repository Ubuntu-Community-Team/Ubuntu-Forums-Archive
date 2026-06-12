---
title: "???what file???"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by windowsfree on 2009-12-02
What file do I edit to change the network name for my PC to become part of a network I want it to.  It defaults to WORKGROUP but I need it to be another name?
Thanks

---

### Post by ibuclaw on 2009-12-02
You mean the hostname?

Or the type of network group the machine is in...

edit:
```
/etc/samba/smb.conf
```
Regards
Iain

---

### Post by windowsfree on 2009-12-02
thanks!

---

### Post by windowsfree on 2009-12-02
do i have to restart all the computers, i modified the file, but still dont see either computer on the network.

one is running 9.04 - the other 9.10

---

### Post by sgosnell on 2009-12-02
Yes, you need to reboot the computers.

---

### Post by windowsfree on 2009-12-02
perhaps I am missing something.
here is the ubuntu 9.10 first part of the samba file:
global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = HOME
        netbios name = Main

The laptop is the same except the netbios name = laptopz   (ubuntu 9.04)

I have a Windows XP computer that has some file shares on it that I need and the 2 printers connected to it that I use for the laptop and the other Linux PC.  I want them to be able to see each other.  As of right now, neither Linux computer sees each other although I can see the windows shares.  I have files on both the laptop and the PC that need to be shared.
Thanks.

---

### Post by Iowan on 2009-12-02
[This]("http://ubuntuforums.org/showthread.php?t=1169149") *might* help with some of the sharing problems. 
(If the problem remains, you may wish to un-mark the thread as solved (also under Thread Tools).

---

### Post by windowsfree on 2009-12-02
Thank you  *- I have it working as much as on the Linux Desktop, the shares I have marked are accesible by the Linux Laptop and the Windows Desktop, when I try to connect to the Linux Laptop from the Linux Desktop I get a login:bob  Domain:HOME* *Password:* Box, *when I put the password it in, I still cannot access the laptop files. I have permissions set the same on both linux machines file shares.*

---

