---
title: "Windows NT4 and Ubuntu: Need Help"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by RGPerson on 2009-02-27
I studied for an MCSE certificate (though I stopped testing after half the tests).  I'm a Microsoft Certified Desktop Support Technician for Windows XP. I've been in tech support for the last 10 years.

So I'm a Windows girl trying to transition to Linux.  Well, not completely.

I have tried, unsuccessfully, before to get an Ubuntu box on my domain.  Never got there, though my XP laptop will try to authenticate to the Ubuntu box sometimes, and thus fail to log in until I shut down the Ubuntu box.

Sigh.

So now we have this new Ubuntu 8.04 LTS box from Dell (Inspiron 530N) and it's doing most of what we want it to do now with a few headaches.  I can even get to Windows files through FTP.  But I'd rather not have multiple copies of files floating around. I'd rather just access a share and get the file from there, work it and save it back to there.

In fact, I'd like my Ubuntu boxes to authenticate to the NT server as well.  I've looked at [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto) but NT4 is not Active Directory so I don't know how well that applies and what needs to be tweaked.  

What I'd like:
Linux boxes connect to Windows shares and vice versa.
All computers authenticate their logons to Windows NT 4 server

I have an ethernet and wifi network.  Most computers are wired, including the Ubuntu boxes.

I have 1 NT4 server, PDC. I do not have a BDC, nor do I want one. (See problem above with my laptop trying to authenticate to Ubuntu).

I have 2 WinXP Pro pc's.
I have 1 (my husband's) Vista laptop.  It doesn't play well on the domain either but I can live with that.
I have 2 Ubuntu boxes, one old, one new. I want them to be clients primarily. Never act as domain controllers.

I know I have to configure the smb.conf file and do something with winbind and maybe pam.

Can someone help or point me to a really good document for NT4 (not ActiveDirectory) setup.  I need the whole thing: what I need to do with samba, with winbind, and with pam, and with the NT server.

Thanks
Gabrielle
Who'd also like to foray into SSH but that's another post....

---

