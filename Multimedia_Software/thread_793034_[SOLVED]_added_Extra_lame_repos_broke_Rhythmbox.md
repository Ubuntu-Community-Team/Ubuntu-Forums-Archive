---
title: "[SOLVED] added Extra lame repos broke Rhythmbox"
date: 2008-05-13
forum: Multimedia Software
---

### Post by DarinB on 2008-05-13
Running Hardy. I run a second HD that mounts automatically with my music.
I use Rhythmbox. I added the Lame restricted repos and now>>>>
Rhythmbox doesn't see my music!!!! the total songs goes backward to 0
i have to import my music folder at each boot takes for ever (10070 songs)
What do i do??????????????????????????????????????????????????
to tried to fix it i installed the lame package,,,now at least i can rip to mp3 with audio cd extractor
still same problem at boot??????????????????????????????????
no music at boot

---

### Post by NightwishFan on 2008-05-13
The hard drive automounts of that you are sure? Perhaps try another Music player such as Amarok.

---

### Post by DarinB on 2008-05-13
how do i check if it is?
where do i look after reboot to check???

---

### Post by DarinB on 2008-05-13
ok it mounts now what????????

---

### Post by DarinB on 2008-05-13
OK I fixed it!
I made sure that edit>preferences>music>Watch my library for new music

didn't work so i re installed rhythmbox and now I'm back 

i have no idea what happened or what fixed it but who cares.

---

### Post by Eddie Wilson on 2008-05-13
In my case this problem has to do with the the mounting of my drive with all my music on it. After I started Ubuntu I would have to go to Places and double click my second disk drive. After it mounted I would have no problem with Rhythmbox. If I did not mount the drive before I started Rhythmbox all of my songs would disappear. The first time it happened it scared the hell out of me.:shock: I saw the songs count down to 0. Auto mounting the drive will take care of the problem.

Eddie

---

### Post by NightwishFan on 2008-05-13
Glad it works good sir. Enjoy.

---

### Post by DarinB on 2008-05-14
thanks Nightwishfan!

re the auto mount search the forum on step by step how to. 
i did it a few months ago its easy...I will see if i can find it as well

---

### Post by DarinB on 2008-05-14
auto mount problem
basically what you need to do is create  mkdir a mount point
like /media/music

then look up your hd info mine is 
/dev/sdc1	/media/music     auto    defaults        0       2

then add it in fstab at the end
gksu gedit /etc/fstab

this is a good place to start
if i find the original info i'll post it

---

