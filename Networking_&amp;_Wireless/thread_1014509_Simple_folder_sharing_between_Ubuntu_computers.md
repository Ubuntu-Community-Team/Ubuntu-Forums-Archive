---
title: "Simple folder sharing between Ubuntu computers"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by oygle on 2008-12-17
Have followed the [share files and folders with other compuers]("https://help.ubuntu.com/8.04/internet/C/networking-shares.html") , which I must say is not very comprehensive.

Are there other docs or 'how-to' to make one folder on a Ubuntu computer available (full access) to another Ubuntu Computer, across the LAN.

I tried what was stated in that link, and got the following msg:

> 'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.


I ticked the "allow other people to write into this folder'.

I have the following packages installed

libsmbclient
nautilus-share
samba-common
smbclient

The permissions on the folder are for others to 'create and delete files' at the folder access level.

Oygle

---

### Post by b9k9kiwi on 2008-12-18
> **oygle said:**
> 
...
which I must say is not very comprehensive
...


I think it is comprehensive, it just doesn't apply to Ubuntu 8.10 - which I presume you are using.

From my experience the Ubuntu community is obsessed with wireless networking so responses to wired networking problems are few and far between.  

I regard the latest version of Ubuntu to be a terrific operating system (after using Windows up until about 6 months ago and as near as dammnit from day 1, except for a short excursion into OS/2), except that networking is broken.

No matter what I do I can't get two PCs with fresh installs of 8.10 to talk to each other and share folders or, for that matter, for either if them to talk to 2 other PCs running Windows or for the Windows PCs to talk to them.  

Meanwhile the Windows PCs chat to each other quite happily.

The new network manager in Ubuntu 8.10 has been widely applauded, but it doesn't work for me.  This is no help to you, of course, but atleast you know you are not alone.

Good luck.

Ubuntu 8.1 Intrepid Ibex

AMD Athlon X2 64 4800+
Asus M2N-ME SX Plus motherboard
Samsung 500Gb HDD Sata II (drive a)
Western Digital 250Gb HDD Sata (drive b)
2x1Gb DDR2 667 RAM
Genius 5.1 Value Soundcard
nVidia GeForce 6600 256Mb PCIe graphics card

---

### Post by oygle on 2008-12-18
> **b9k9kiwi said:**
> I think it is comprehensive, it just doesn't apply to Ubuntu 8.10 - which I presume you are using.

Okay, I'm trying to get from 8.04 to 8.10 via dialup. :lolflag:

> **b9k9kiwi said:**
> 
From my experience the Ubuntu community is obsessed with wireless networking so responses to wired networking problems are few and far between.


Well, that may help me in the future. Can't get adsl here and can't get a wireless going until I upgrade to 8.10 (all the stories I have seen is that the usb wireless modem I have is a breeze with Intrepid).

But, yes, not much wired help. I did find a bug, see [Bug #128548 in samba (Ubuntu): “Enable net usershare?”]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/128548")

> **b9k9kiwi said:**
> 
I regard the latest version of Ubuntu to be a terrific operating system (after using Windows up until about 6 months ago and as near as dammnit from day 1, except for a short excursion into OS/2), except that networking is broken.


I'm trying to get XP going on a dodgy HDD, and 8.04 can see it okay, using workgroups and windows networking. But that 8.04 computer can't see the other 8.04 computer, so yes, LAN networking is not real good between 2 Ubuntu boxes.

> **b9k9kiwi said:**
> 
No matter what I do I can't get two PCs with fresh installs of 8.10 to talk to each other and share folders or, for that matter, for either if them to talk to 2 other PCs running Windows or for the Windows PCs to talk to them.


When I wanted Ubuntu 7.? to talk to Windooze, all I installed was:

samba-common
smbclient

I think. The 'trick' was to specify the windows workgroup name in the file smb.conf. Then I could see any Win shares in Nautilus. 

There seem to be many threads on 'peer to peer' between Win boxes, but not much, as you say, on doing it with Ubuntu.

> **b9k9kiwi said:**
> 
The new network manager in Ubuntu 8.10 has been widely applauded, but it doesn't work for me.  This is no help to you, of course, but at least you know you are not alone.


That new network manager has been applauded, yes, and I hope it works to get the wireless going (when I get all the .debs for Intrepid that is) soon.

Are there any messages in syslog or similar, when you try to access a Ubuntu share ? From memory, when I was having some Samba problems, installing smb4k solved a lot, and I _think_ I had to have it running, to get any of the Samba stuff going.

Oygle

---

### Post by b9k9kiwi on 2008-12-18
I have cruised a number of Ubuntu techno-geek sites and discovered the following (which worked for me);

Go to Places/Computer.

Open the 'Go' menu and click on 'Location...'.

Type in smb://x.x.x.x (where x.x.x.x is the ip number of the computer you wish to connect with) and press Enter.

The Shares on the other computer should now appear in Nautilus and, it seems, will persist (i.e. remain displayed in Places/Computer after a reboot).

This will do for me for now, I wonder if it will do for you.

---

### Post by horacle on 2008-12-18
as oygle said, the trick is to specify the workgroup name in smb.conf. I have 2 dualboxes, one with fedora/xp and the other with ubuntu/xp and with all the os' in the same workgroup, I have almust no network problems with any combination... I say almust because I cant print when the printing host is xp and the guest is ubuntu, but I can browse the shares from any box with no problems.

---

### Post by lswb on 2008-12-18
For file sharing between linux (or other unix-like) systems a very simple method is to install openssh-server on the system with the desired files (or on all systems). Then from other systems you can access the files by Main Menu/Places/Connect to Server, select SSH as server type, fill in host name or ip address of the target system & click Connect. You will be prompted for a user name & password and will then get a file browser window opened as if you were a user logged in on the target system.

Another program, sshfs, if installed on all client systems, will allow a remote system running ssh server to be mounted to a local mountpoint directory similar to how a disk is mounted. It can then be accessed through that mountpoint just like a local disk, using any command line program or file browser.

Lots of people like nfs for filesharing between unix/linux systems also.

---

### Post by Iowan on 2008-12-18
[SSHFS]("https://help.ubuntu.com/community/SSHFS")
[NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
[Mount CIFS shares]("http://ubuntuforums.org/showthread.php?t=288534").

---

### Post by oygle on 2008-12-18
> **b9k9kiwi said:**
> I have cruised a number of Ubuntu techno-geek sites and discovered the following (which worked for me);

Go to Places/Computer.

Open the 'Go' menu and click on 'Location...'.

Type in smb://x.x.x.x (where x.x.x.x is the ip number of the computer you wish to connect with) and press Enter.

The Shares on the other computer should now appear in Nautilus and, it seems, will persist (i.e. remain displayed in Places/Computer after a reboot).


This does work, and for me, has always worked for doing this ..

Ubuntu  ------>  Windows share

I can use the format 'smb://x.x.x.x' in Nautilus, Konqueror, KDiff3 and other tools, to access a Windows share, no problems.

BUT, I'm trying to access a Ubuntu share, well, back one step, I need to first setup a Ubuntu share, which I can't.  :(

From that bug page, it seemed to be an ACL problem. The Samba people seemed to have it fixed, but it either hasn't filtered down to Ubuntu, or I'm missing something.  :D

Oygle

---

### Post by oygle on 2008-12-18
> **horacle said:**
> as oygle said, the trick is to specify the workgroup name in smb.conf. I have 2 dualboxes, one with fedora/xp and the other with ubuntu/xp and with all the os' in the same workgroup, I have almust no network problems with any combination... I say almust because I cant print when the printing host is xp and the guest is ubuntu, but I can browse the shares from any box with no problems.

horacle, so you can browse between fedora and Ubuntu, no problems, that's interesting.

Pity that all this relies on a name like a 'workgroup', it's so, errr, .. Windows. I would have thought that if it was Linux <---> Linux sharing, then it would not have to rely on such terminolgy.  :)

I know one Ubuntu box has the workgroup name the same as the XP, and I can browse a shared XP folder. I will check smb.conf in the other Ubuntu computer, and make sure the workgroup is the same.

---

### Post by oygle on 2008-12-18
lswb - Thanks for the info on openssh-server and sshfs. I have to 'login' to the Windows share now from Ubuntu, so it's no extra to have to do so with a tool like the ones you mentioned.

Iowan - Thanks for those links, I will check them out.

---

### Post by albinootje on 2008-12-18
> **oygle said:**
> Have followed the [share files and folders with other compuers]("https://help.ubuntu.com/8.04/internet/C/networking-shares.html") , which I must say is not very comprehensive.

Are there other docs or 'how-to' to make one folder on a Ubuntu computer available (full access) to another Ubuntu Computer, across the LAN.
I ticked the "allow other people to write into this folder'.

I just tested it with my 8.10 desktop.
Did choose the "allow other" option, then the question was whether i wanted to allow nautilus to make those changes, i clicked yes.

Then i checked the permissions of that folder, and it was now 777.
(Not very cool, the 777 hmmm :|

And.. it worked. From my netbook with 8.04 i could connect and create a new folder in it.

(I assume you connected succesfully before ? 
I had to make a samba user before it worked at all,
didn't see that in the howto you linked to.)

---

### Post by oygle on 2008-12-20
> **albinootje said:**
> 
(I assume you connected succesfully before ? 


No, I have only been able to view Windows shares, I have not been able to view Ubuntu shares. I have not been able to setup a Ubuntu share (see previous post about error message, and reference to a bug)

> **albinootje said:**
> 
I had to make a samba user before it worked at all, didn't see that in the howto you linked to.)

Did you create this Samba user by using the Ubuntu 'users/groups' admin function, or was it something you did under 'Samba' itself ?

Looking at the Samba site, it seems it is only for Linux <--> Windows , and not Linux <---> Linux , or maybe I have misunderstodd somthing about Samba,

---

### Post by albinootje on 2008-12-20
> **oygle said:**
> No, I have only been able to view Windows shares, I have not been able to view Ubuntu shares. I have not been able to setup a Ubuntu share (see previous post about error message, and reference to a bug)



Did you create this Samba user by using the Ubuntu 'users/groups' admin function, or was it something you did under 'Samba' itself ?

Looking at the Samba site, it seems it is only for Linux <--> Windows , and not Linux <---> Linux , or maybe I have misunderstodd somthing about Samba,

I use the smbpasswd command, which is part of the samba-common package.
Example for creating a new samba-user :
```

sudo smbpasswd -a marianne

```
Try for more info on smbpasswd : smbpasswd -h

Beware, like this, you can only create a samba-user if the username for it already exists as a Ubuntu user.
After successfully creating a new samba-user, use those credentials for the shares you've made with Nautilus.

---

### Post by albinootje on 2008-12-20
> **oygle said:**
> 
Looking at the Samba site, it seems it is only for Linux <--> Windows , and not Linux <---> Linux , or maybe I have misunderstodd somthing about Samba,

No, i'm using Samba in Linux <--> Linux setups since years. :)
... Linux is flexible ;-)

---

### Post by LavianoTS386 on 2008-12-21
Yeah I've got this same problem. If I use call to my netbook from my desktop using the IP meathod I can see shares. However, that does me no good on my netbook when I want to connect to my desktop, because my desktop doesn't let me share folders.

---

### Post by oygle on 2008-12-21
> **albinootje said:**
> I use the smbpasswd command, which is part of the samba-common package.
Example for creating a new samba-user :
```

sudo smbpasswd -a marianne

```
Try for more info on smbpasswd : smbpasswd -h

Beware, like this, you can only create a samba-user if the username for it already exists as a Ubuntu user.
After successfully creating a new samba-user, use those credentials for the shares you've made with Nautilus.

Okay thanks. I will try that.

> **albinootje said:**
> No, i'm using Samba in Linux <--> Linux setups since years. :)
... Linux is flexible ;-)

Yes, Linux is great. It would be good to have a good 'how to' on sharing files between two Ubuntu computers though.  ;)

---

### Post by dmizer on 2008-12-22
For sharing files between two Ubuntu computers, please see the 4th link in my sig. :)

It's important to realize that in Linux, the server and client portions of file sharing are separate. This means that if you correctly configure a SAMBA server, you will still not be able to connect to another computer's SAMBA shares.

For example:
"----" = a network connection
"<" = direction of connection
"computer2" = any Windows computer

**Configure a samba server on "computer1"**

computer1 <---- computer2

**Configure a samba client on "computer1"**

computer1 ----> computer2

**Configure a samba server AND a samba client on "computer1"**

computer1 <----> computer2

Now, if both computer1 and computer2 are Linux computers, AND you want two way communication between both Linux computers, you will have to setup BOTH computers as both a server and a client. This is true of all protocols I can think of, including SAMBA, FTP, NFS, and fuse. Some clients are easier to set up than others, and some servers are easier to set up than others.

---

### Post by oygle on 2008-12-22
> **dmizer said:**
> For sharing files between two Ubuntu computers, please see the 4th link in my sig. :)

Thanks for the tips on Samba. Had a quick look at that tutorial from the link in your sig; it seems NFS is easier to setup than Samba, and doesn't need usernames either. But then, how does the authentication side of things work with NFS ?

Thanks,

Oygle

---

### Post by dmizer on 2008-12-22
> **oygle said:**
> Thanks for the tips on Samba. Had a quick look at that tutorial from the link in your sig; it seems NFS is easier to setup than Samba, and doesn't need usernames either. But then, how does the authentication side of things work with NFS ?

Thanks,

Oygle

The howto I referenced assumes you are connected to a trusted local network and does not use authentication.

---

