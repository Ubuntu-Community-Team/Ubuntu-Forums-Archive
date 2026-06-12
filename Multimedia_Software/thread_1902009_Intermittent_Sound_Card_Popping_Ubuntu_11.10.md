---
title: "Intermittent Sound Card Popping Ubuntu 11.10"
date: 2011-12-29
forum: Multimedia Software
---

### Post by maverick918 on 2011-12-29
Hello all,

I have searched the Internet for my issue and I haven't found anything describing exactly what I'm experiencing. Ubuntu 11.10 (64-bit) is installed on my computer with the following specs.

Motherboard - Asus PZ68-V-Pro (on board sound)
CPU - Intel i7 2600 
RAM - 16 GB

My issue is as follows: When ever I listen to an audio file I get this popping sound almost like the audio is "flickering". Its very strange. 

I work as a Systems Administrator so I know the basic steps to troubleshooting an issue and I have found that this is Operating System related due to the following.

- I have tried 2 sets of speakers on the same operating system and the same issue has happened.
- I have tried the same speakers on Windows 7 booted from a different Hard drive on the same computer and no popping. 

The reason I believe this to be Ubuntu 11.10 specific is because you can visually see the audio icon flickering from muted to unmuted. Thats the best way I can describe it. 

So its not the mp3's or the shell. I believe this to be a driver issue. My question is has anyone experienced this or know to fix something like this.

Thanks!

---

### Post by lidex on 2011-12-31
Try purging your pulse configuration files:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*
No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

