---
title: "Samba help, windows asking for password that doesn't exist"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by linkpalmer on 2011-12-14
Hi guys, I'm new to ubuntu but have been at this problem for 3 days now, scoured the net, and am basically out of ideas. I have installed Samba sharing on my ubuntu 11.10 machine, but my Windows XP and Windows 7 machines cannot access the share folder. My linux machine is static IPd to 192.168.0.101, and the windows machines can see what folders are shared on the linux machine, but cannot open them. trying to double click the folders gets the message: 

"Enter your password to connect to SEANUBUNTUPC [that is the name of my linux computer]

then it has a field for my username and password, then says "domain: SEANLENOVO" SEANLENOVO being the name of my windows7 pc on which I'm trying to access.

what's odd is that I am attempting to share a folder on an external harddrive on my linux machine, and I can hear the drive spin up each time I try to access it. I have also shared a folder in the smb.conf file called "doesnotexist" just to see how it behaves. it shows up in the folder list of shared folders on my windows machines, but double clicking it gives me a "cannot find specified path" message. So it appears to me that the problem is on the Linux end of things with regard to the mysterious password. Oh, also, I use the same password as my login and sys password for both my Windows7 and Linux machine, and my WinXP system has no password. I have tried no password AND that password, neither work.

here are my .conf settings.

[global]
    workgroup = BRYNET
    security = SHARE
    guest account = nobody
    client lanman auth = yes
    name resolve order = lmhosts wins bcast host
[testing_samba]
    path = /media/Music15/testing_samba
    ;browseable = yes
    read only = yes
    guest ok = yes
    public = yes
    ;create mask = 0644
    ;directory mask = 0755
    ;force user = sean
[doesnotexist]
    path = /media/Music15/doesnotexist
    browseable = yes
    read only = yes
    guest ok = yes
    public = yes
    ;create mask = 0644
    ;directory mask = 0755
    ;force user = sean




any pointing in the right direction would be wonderful. I have done the 

sudo restart smbd
sudo restart nmbd

commands after each attempted change, and nothing seems to make a difference. The computers are on the same Workgroup (BRYNET)
the only thing I could think of was when I went to change the workgroup for my win7 computer, it mentioned something about setting a workgroup or a domain. I'm not entirely sure how the domains work in Windows, or if that could be a part of the issue.

Thanks for reading! Going crazy with this!

---

### Post by Ryadt on 2011-12-15
Hi,

This reminds me of my headaches](*,)](*,)](*,).

Try this thread [http://ubuntuforums.org/showthread.php?t=1474593]("http://http//ubuntuforums.org/showthread.php?t=1474593")

---

### Post by Morbius1 on 2011-12-15
[1] Note: This is more a rant than anything useful but ...
I really don't know why some users go out of their way to take the default smb.conf file and distort so that it no longer resembles the way it should work.

[2] I'm a little rusty on SHARE level security since it hasn't been used since Jimmy Carter was president but is this external hard drive formatted in NTFS or FAT32 by any chance?

If it is you might have the answer in your own smb.conf but you commented it out:
> [doesnotexist]
    path = /media/Music15/doesnotexist
    browseable = yes
    read only = yes
    guest ok = yes
    public = yes
    ;create mask = 0644
    ;directory mask = 0755
    [COLOR=Blue]**;force user = sean**[/COLOR]Get rid of the leading "[COLOR=Blue]**;**[/COLOR]" and restart samba

---

### Post by linkpalmer on 2011-12-16
Hey, thank you guys so much, should have come here sooner.
What I ended up doing was a combo of both your replies. I typed in 

```
sudo smbpasswd -a username
``` 
with the username I use for ubuntu, which also happens to be the name I use on my windows 7 computer. This allowed me to access the files on Windows 7, but not on my Windows xp computer (which uses a different username, but I suspect that was not the issue)

On my windowsXP computer, it tried to default the username to \guest
which would not accept any password with the account. I was able to successfully map it as a network drive, and then force it to login with the login Sean. 

Taking out that ; character to uncomment the force user line though made it so that I didn't need to map it as a network drive


Morbius: as to why I removed the default structure of the conf file - another guide suggested starting fresh, and I figured that any conflicting services would then hopefully be wiped out of the file. That way I would know EXACTLY where I was having problems. I wanted to simplify it down to the basics, since I don't require any passwords on any of my shares.
And it is an NTFS drive, but the testing_samba folder was recently created within Linux, just in case I was having some weird permissions problems with the folders not being owned by the new Linux user.


cheers, thanks again guys!

---

