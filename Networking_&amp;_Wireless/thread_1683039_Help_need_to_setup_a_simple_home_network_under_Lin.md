---
title: "Help need to setup a simple home network under Linux."
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by locksalordy on 2011-02-06
I have three PC's. PC-1 is a newish Dell Vostro 320 running Win 7 as the prime OS with Ubuntu Linux 10.10 dual boot under the control of EasyBCD. PC-2 is a Dell  Inspiron 6400 running Ubuntu Linux (10.10). PC-3 is an oldish Dell Inspiron 6000 laptop dual booting Win 7 and Ubuntu 10.10. All three PC's share a DSL connection to our ISP and network using the wireless router capability of the DSL box (a Billion 7401 VGP-M). All three PC's can access the internet using the DSL box both wired and wirelessly under Windows or under Linux. PC-1 is the primary PC and runs Win 7.

PC-2 (Ubuntu 10.10) is running fantastically well and can access PC-1 running Win7 as a member of WORKGROUP for print sharing and for file sharing. The primary PC-1 can also see the files on PC-2 as a member of a Windows WORKGROUP. Simple home networking is working as it should with this setup (PC-1 under Win 7 and PC-2 under Ubuntu 10.10). This has been like this since the installation of Ubuntu on PC-2, which included setting up network printing from PC-1 (Win 7) under Samba.

The problem is thus: If I boot PC-1 or PC-3 up under Linux, I lose all networking capability between the three PC's including print and file sharing, but they can all access the internet through wireless or wired connection. I have configured Samba and done all the home networking troubleshooting especially:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

All to no avail. As I said, my aim to ditch Windows and move all three PC's to Linux but I can't do this unless I can get Linux home networking working properly. By properly, I mean all PC's running Linux or two under Linux and one under Windows 7 and be able to share files and a printer attached to PC-1. 

I am  a Linux virgin and am hoping that a knowledgeable person can tell me what's going wrong and point me to setting up a simple home network under Linux. It shouldn't be this hard.

---

### Post by arjuntank on 2011-02-06
if you are absolutely sure that you followed that post, this may help:
[http://wiki.samba.org/index.php/Windows7]("http://wiki.samba.org/index.php/Windows7")

---

### Post by locksalordy on 2011-02-07
Thanks, arjuntank.

The registry on the Win 7 machine appears to need this patch and I will apply it. Two things come to mind, however. First, one Linux PC is quite happily co-existing with a Windows 7 PC using Samba, and second, I still can't get a pure Ubuntu 10.10 network file sharing and print sharing without Windows in the picture.

Regards,

locksalordy

---

### Post by arjuntank on 2011-02-07
hmm, it may be some firewall issue on windows or in ubuntu if you have one. otherwise, following the guide you presented should make it work. do you use smb.conf or system-config-samba for configuring samba?

---

### Post by locksalordy on 2011-02-08
Hi arjuntank,

"sudo ufw status" reveals status as "inactive", and enabling disabling the Windows firewall does not seem to have any effect.

I used GADMIN-SAMBA to look at the samba.conf file but other than that, I  have not used anything to configure Samba. PC-2 (Ubuntu 10.10)  configured itself on install and home networking works just fine with  PC-1 when PC-1 is under control of Win 7 Pro. The problems start when  PC-1 is booted under Ubuntu 10.10. Under a pure Linux environment, PC-1  and PC-2 don't appear to see each other.

Thanks,

locksalordy

---

### Post by arjuntank on 2011-02-08
check smb.conf again for both pc1 and pc2..may be some misconfiguration

---

### Post by P4man on 2011-02-09
See if you can connect to the shares using IP address

smb://192.168.x.y

---

### Post by locksalordy on 2011-02-11
Thanks P4man,

No joy, I am afraid.

I think I'll stop trying to fix this and come back to it when I have more time.

locksalordy

---

