---
title: "[SOLVED] Samba net shares don't work with Media Player"
date: 2008-10-12
forum: Multimedia Software
---

### Post by jimmah6786 on 2008-10-12
Has anyone had an issue with samba shares not working with Totem, VLC, or any other player. 
I have a mount in my fstab for a smb share on another computer. I can browse the directory and I see all my media files(mp3, flac, avi,etc), however when i open them with vlc,totem,mplayer, or xine it does not play them. Interesting enough a couple of the players I have tried will load the file length, for example songs I try to open will show 0:00/3:42 The player just never plays them. I have paused/unpaused, seeked, nothing works. I do have the ubuntu-restricted-packages installed so I know the codecs are not a problem. The computer sharing my media files is allowing full-access, this I am sure of.

Here is my /etc/fstab line
\\192.168.254.250\music /home/jim/Music/netMusic/	cifs user=#####,password=#####	0	0

I have not included the username and password, obviously. 192.168.254.250 is IP of the computer with my music and videos on it.

I open Rhythmbox and have it scan my mounted folder for music. It adds my entire library, with all the correct information. It just doesn't play them, sits at 0:00 seconds.

Thank you for your help, I am stumped.:(

---

### Post by jimmah6786 on 2008-10-13
Alright so I reinstalled the ubuntu-restricted-extras package, restarted my computer and it is automagically working.

---

