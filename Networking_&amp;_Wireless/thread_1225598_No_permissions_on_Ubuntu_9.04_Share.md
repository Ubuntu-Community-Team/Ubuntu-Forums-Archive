---
title: "No permissions on Ubuntu 9.04 Share"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by mardop on 2009-07-28
I have a home network and am running Ubuntu 9.04 on three workstations. On one of those workstations I want to run backuppc, which is why I mount shares from different machines: There are two NAS boxes which have several shares defined that I mount via cifs. Works very fine. Further there is a Mac and a Windows Server 2003. Also those shares can also be mounted via cifs w/o any problem. Works perfectly! From all three Ubuntu 9.04 Machines!
Now I defined some shares on the Ubuntu Machines with Write-Access for others. But when I try to connect those shares I get a permission denied, doing the following:

a) Trying to connect them via Places / Connect to Server / Windows Share / Server: IP-Address of Ubuntu 9.04 Box / Share: Sharename / User Name: (my credentials on the other machine are identical) / Domain Name.
When I click the button "connect" I am promted for the password which I enter. Then I am prompted again and again and endlessly again. No errormessage....

b) Or: Places / Network / I see the Ubuntu Workstation Name with the share I wanted to connect and doubleclick it / Then I see the share !!!! and I doubleclick it / I am prompted for username, domainname and password, which I enter / After pressing enter the prompt disappears ... and pops up again and again and again ... endlessly !!

c) sudo mount -o username=(user),password=(pw) //ip-address/sharename  /home/user/mnts/Workstationname ..... result: Permission denied

d) in fstab: //ip-address of ubuntu 9.04 box/sharename  home/user/mnts/Workstationname cifs credentials=/root/.smbcredentials,iocharset=utf8,noperm,filemod=0777,dirmod=0777 0 0

When in terminal I do "sudo mount -a" I get: mount error(13) Permission denied (as above).

e) From my Mac I say Go / Connect to server / providing IP-Address and Shared ... After authentication it says, that the user or password are not valid !!!

Does anyone have an idea, what I am missing? Many thanks in advance.

---

### Post by billdotson on 2009-08-03
bump

---

