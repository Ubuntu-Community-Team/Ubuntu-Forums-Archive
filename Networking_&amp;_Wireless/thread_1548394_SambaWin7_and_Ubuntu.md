---
title: "Samba/Win7 and Ubuntu"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by lb4406 on 2010-08-08
I'm tearing my hair out now having spent almost 2 days trying to access Windows 7 Home Premium shares from Ubuntu.

I have several laptops/netbooks all running 10.04 which can see and share with each other and two Windows 7 Home Premium machines which don't see the Ubuntu machines. They are all connected via a wireless internet router.

The Ubuntu machines can see the Windows 7 but get "failed to retrieve share list from server". 

Originally they just kept refusing to accept a username or password but I tried this:

"HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Contro l\

In the left, click on the folder named: Lsa

In the right, double-click "LmCompatibilityLevel"
Type the number 1 and press enter
Restart your computer"

Which seemed to fix that part of the problem.

I've added WINS to the name resolve order line in smb.conf so it looks like this:

"= lmhosts host wins bcast"

I've disabled IPv6 on the Win 7 box,and I've added these two registry keys from the Samba Wiki:

"HKLM\System\CCS\Services\LanmanWorkstation\Parameters
            DWORD  DomainCompatibilityMode = 1
            DWORD  DNSNameResolutionRequired = 0"

I have also disabled the Win7 Firewall on the Home side.

The Win7 Machine is /HOME, 192.168.1.42. 
In Ubuntu when I type PING HOME it pings 192.168.1.**44** which obviously never resolves to anything as that IP doesnt exist on my network.
If I PING 192.168.1.42 then PING works fine so its obviously seeing the other machine and vice versa.

The workgroup name is "WORKGROUP" and is set correctly on each machine.

Does anyone have any more suggestions before I throw the whole lot out the window?!:popcorn:

---

### Post by Menthu_Rae on 2010-08-08
Do you have the windows live sign in assistant installed by any chance?

[http://ubuntuforums.org/showpost.php?p=8556295&postcount=14](http://ubuntuforums.org/showpost.php?p=8556295&postcount=14)

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/458637](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/458637)

[http://social.technet.microsoft.com/Forums/en-US/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en-US/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

---

### Post by lb4406 on 2010-08-08
I did - (Dunno how I missed that thought I had read every page on Win7 vs Ubuntu!) , however Have just removed it and it makes no difference. Still failed to retrieve share list from server. :(

Thought that was going to be the fix when I read that as well!

---

### Post by lb4406 on 2010-08-09
bump

---

### Post by wookieshaver on 2010-08-09
I would turn off password protected sharing in your windows 7 box. Here are the windows instructions: 
 
[http://maximumpcguides.com/windows-7/disable-password-protected-sharing/](http://maximumpcguides.com/windows-7/disable-password-protected-sharing/)
 
 
(I had the same issue with my ubuntu boxes and my windows 7 enterprise box)

---

### Post by lb4406 on 2010-08-10
Just turned off password protected sharing - still unable to get to it, and I've also ensure that the "everyone" Group has full access as well!

---

### Post by lb4406 on 2010-08-10
Fixed "The Win7 Machine is /HOME, 192.168.1.42. 
In Ubuntu when I type PING HOME it pings 192.168.1.44 which obviously never resolves to anything as that IP doesnt exist on my network.
If I PING 192.168.1.42 then PING works fine so its obviously seeing the other machine and vice versa."

Removed the Wins line from Smb.conf which one potential solution told me add - name resolution works fine now, however When I goto Windows Shares on the Workgroup I can't even see the Windows 7 machine!

---

### Post by lb4406 on 2010-08-10
Its now working!

no idea what actually fixed it as I did so much!  but will post my thoughts in case someone else finds the thread who needs similar help.

Removing Wins from the smb.conf along with disabling password required to log on, and adding the everyone group to the folder may have done it *except*

It still won't log on from Ubunutu without a password but once the password of the windows user was put in it logged on ok, I only added the everyone group full rights to one folder but I can see all the shared folders.

---

