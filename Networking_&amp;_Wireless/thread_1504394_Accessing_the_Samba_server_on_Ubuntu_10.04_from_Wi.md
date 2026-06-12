---
title: "Accessing the Samba server on Ubuntu 10.04 from Windows XP"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by Sven6210 on 2010-06-07
[FONT=Arial][SIZE=2]I have a media server running Samba and Ubuntu 10.04 and a laptop with Windows XP. I want to access files from an USB disk connected with the Samba Server from my Windows XP laptop.

[/SIZE][/FONT]      [FONT=Arial][SIZE=2]I managed to configure the Samba server so that I can access the files from Windows XP, however I am struggling with one issue. On Ubuntu I have two users:
[/SIZE][/FONT]   
[LIST]
[*][FONT=Arial][SIZE=2]UBUNTUUSER[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]SAMBAUSER[/SIZE][/FONT]
[/LIST]
    [FONT=Arial][SIZE=2]
[/SIZE][/FONT]   [FONT=Arial][SIZE=2]UBUNTUUSER is the main user of Ubuntu as created when installing Ubuntu. I manually added the SAMBAUSER to the Ubuntu users and I verified that SAMBAUSER has the necessary access rights to the USB disk that shall be shared via Samba

[/SIZE][/FONT]      [FONT=Arial][SIZE=2]I also added both, the UBUNTUUSER and the SAMBAUSER to Samba and enabled both.

[/SIZE][/FONT]      [FONT=Arial][SIZE=2]Now, when connecting from Windows XP to Samba I have some problem. When I use UBUNTUUSER on the windows machine (of course with the same password) I can access the shared USB disk and copy/delete/edit files. However, when I use SAMBAUSER on Windows XP I can see the folders but I can not copy/delete/edit a single file. Also in this case I use with Windows the same password as in Ubuntu/Samba.

[/SIZE][/FONT]      [FONT=Arial][SIZE=2]Summary:
[/SIZE][/FONT]   
[LIST]
[*][FONT=Arial][SIZE=2]The Samba is configured in order to share the USB disk (I can access it from Windows XP when using the UBUNTUUSER)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]It is not a problem of the user name or password on Windows XP[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]The wired connection is O.K. and there is no problem with IP addresses[/SIZE][/FONT]
[/LIST]
      [FONT=Arial][SIZE=2]
[/SIZE][/FONT]   [FONT=Arial][SIZE=2]Question:
[/SIZE][/FONT]   
[LIST]
[*][FONT=Arial][SIZE=2]Is the problem that SAMBAUSER on Ubuntu has wrong user rights and that I must review it?[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Is the problem caused by the USB disk which is mounted by UBUNTUUSER and that can not be accessed at the same time by SAMBAUSER?[/SIZE][/FONT]
[/LIST]
    [FONT=Arial][SIZE=2]
[/SIZE][/FONT]   [FONT=Arial][SIZE=2]I am quite sure I am rather close to solve the problem, however I would appreaciate any hint/advise that could save me some time.

[/SIZE][/FONT]      [FONT=Arial][SIZE=2]Thank you in advance

[/SIZE][/FONT]      [FONT=Arial][SIZE=2]Sven[/SIZE][/FONT]

---

