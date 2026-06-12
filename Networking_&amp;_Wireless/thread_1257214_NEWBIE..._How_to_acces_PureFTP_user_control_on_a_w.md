---
title: "NEWBIE... How to acces PureFTP user control on a windiws base computer??"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by heckelman on 2009-09-03
Hi
 
Before i start to write anything i have to say that i am a complete NEWBIE with Ubuntu/linux and the kind ;-)
I use a windows XP computer. The thing i want to achieve is the following. 
I have an Western Digital network harddisk (world edition) and i just inished installing PureFTP on it. Its a linux based system as i understood it. The installation wet trough a kind of "firmware update" so i didnt really do it myself. 
The server is running! I can acces it from any internet connection. 
The only thing is i dont know how to set the user controls....
 
The istallation made a map called FTPRoot on the shared folder of the HD
The only file wich i can acces and set soe kind of user control is a txt file called:
 
ftpUsers.txt (in the shared folder)
 
The file looks a bit like this:
 
ftp--username1:password1/share1
ftp--username2:password2/share2
ftp--username3:password3/share3
[blank line]
 
 
So i can set up usernaes and password and a kind of shared folder that will be made inside the FTPRoot folder.
So far so good!
The obly thing is i want to have some more controls over wo sees what, can they write, can they read only, up/download limits etc etc.
I found this programm 
 
**[SIZE=2]KDE PureFTPd User Manager[/SIZE]**
 
 
wich should work on Ubuntu. I downloaded the Ubuntu disk and installed it inside windows. and now from this point i have actually no clue what to do. How to install this User Manager, and then start to control the Users for PureFTP....
 
I hope you can give me some help, and please remenber ;-)) Complete newbie!
 
Thanks a lot guys in advance!
 
Heckelman
 
:popcorn:

---

### Post by jonobr on 2009-09-03
Hello


Welcome to the forums,

I wonder if you could take it back a bit and help me understanding what your trying to accomplish.

If you could outline something like the following,

- I have a machine running Ubuntu desktop/server version XXX.
- I want to be able to allow user to ..............(upload , download, overwrite copy etc)
- The Ubuntu desktop/server has to act like a ....... (eg file server, web server, storage repository, for me to just play around with) 
- Security for me is upmost importance, not very important, etc......
- THe users that will connect are using (winxp, ubuntu, mac)



Once you outline your requirements we can probably help you out with the setup.
You will find most people here use SSH and SFTP or SCP to copy stuff around given its more secure, but again, if we know what your trying to achieve maybe we can help more

---

### Post by heckelman on 2009-09-08
Hi Jonobr!
 
Thanx for your answer :-)
 
At the moment UBUNTU has a couple of problems to run on my WIndows XP computer. I am trying to fix this!
 
SO here your requests:
 
1 as i have problems i have to install UBUNTU new on Windows XP, all the downloadable ISO's for WinXP i tried now have an error... I hope i find a working one in the next time (any recommendations??)
 
2 i want the Users to be able to download, upload and copy, make new Maps, nut not to delete/overwrite existing maps
 
3 The PureFTP server has to act like a fileserver and firefly server. But lets concentrate here on the fileserver because the firefly is working. So an HD that is accesable trough FTP in short.
 
4 Security is important but there are not importatn files on it, so lets take it easy with that! ;-)
 
5 Most of the users who are going to connect are using WinXP and maybe a single one a MAC
 
So i am trying to find out a nice way to control the users. Wich maps can they see, etc etc. 
 
Thanx already!!
 
 
Heckelman

---

