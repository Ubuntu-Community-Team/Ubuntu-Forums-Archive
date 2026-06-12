---
title: "streaming media"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by jason82 on 2010-01-18
i have been streaming media from my pc (vista) to my wii using mplayer ce i want to set it up to do the same in ubuntu (9.10).  i have samba installed and the drive with my media is set to read only/visible/allow access to everyone the directory is /media/STUFF and the share name is STUFF.

the wiki for mplayer is [http://wiibrew.org/wiki/MPlayer_CE#V0.1_Christmas_Edition](http://wiibrew.org/wiki/MPlayer_CE#V0.1_Christmas_Edition) 



[I]this is my smb config on the wii sd card,  smb 1 is the working one for vista,  and smb 2 are my different attempts to get it to work with ubuntu
[/I]

[I]Samba share1  (smb1:/)
ip1=192.168.**.*
share1=j 
user1=jason
pass1=#$%^&*

Samba share2  (smb2:/)
ip2=192.168.**.*
share2=/media/STUFF
user2=
pass2=


[/I][I]
Samba share2  (smb2:/)
ip2=192.168.**.*
share2=STUFF
user2=
pass2=

[/I][I]
Samba share2  (smb2:/)
ip2=192.168.**.*
share2=/media/STUFF
user2=jason
pass2=
[/I]
[I]
Samba share2  (smb2:/)
ip2=192.168.**.*
share2=/STUFF
user2=jason
pass2=
[/I]
also tryed it with my ubuntu admin password  with both share directories
 the **.* in ip is the same every time (i know im paranoid )   j is is the drive letter in window , also the drive is set to auto mount in ubuntu 

any help would be great 


thanks

---

### Post by Lars Noodén on 2010-01-18
If you mean file sharing, also known as networked storage, then Samba is the way to go. 

If you want streaming, then look at vlc, icecast2 or ffmpeg.  They all do streaming nicely, so it's a matter of picking one.

---

### Post by jason82 on 2010-01-18
> **Lars Noodén said:**
> If you mean file sharing, also known as networked storage, then Samba is the way to go. 

If you want streaming, then look at vlc, icecast2 or ffmpeg.  They all do streaming nicely, so it's a matter of picking one.



yeah i guess  its file sharing, but why cant i get it to work,  like i said samba is installed on my ubuntu machine and obviously the wii uses samba as well so it should be simple i must be missing something,  my ip is the same in windows and ubuntu right ?

---

### Post by blackened on 2010-01-18
> **jason82 said:**
> ...my ip is the same in windows and ubuntu right ?

Not unless you have set up the same static ip address for each operating system. If you've not, then your ip changes with each reboot/network reconnect.

---

### Post by jason82 on 2010-01-18
aaaa i see so what do i got to do to make it match my windows ip (just save me time searching)

---

### Post by blackened on 2010-01-18
This assumes that you have already set a static ip in Windows and you know what that ip is. 

In Ubuntu, right-click on the network manager icon in the system tray and select "Edit Connections" from the list. In the subsequent dialog, select the tab appropriate to your connection type, then select your connection from the list and press the "Edit" button on the right. In the subsequent dialog, go to the "IPv4 Settings" tab, in the "Method" dropdown menu select "Manual", press the "Add" button on the right, enter all the information pertaining to your connection, then press the "Apply" button at the bottom.

Make sure the connection information you enter is the same as what you've set in Windows.

---

### Post by jason82 on 2010-01-18
cool thank you all give it a go tomorrow thanks

---

### Post by jason82 on 2010-01-19
that didnt work it just made my internet connection not work

---

### Post by blackened on 2010-01-19
Heh, then you didn't do it right. 

Google setting up a static ip in ubuntu. I'm not patient enough to hunt down screenshots as visual aids whilst posting from my telephone.

---

### Post by jason82 on 2010-01-19
> **blackened said:**
> Heh, then you didn't do it right. 

Google setting up a static ip in ubuntu. I'm not patient enough to hunt down screenshots as visual aids whilst posting from my telephone.



lol well ill give it another try thanks

---

