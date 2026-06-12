---
title: "realplayer 11 won't install in 8.04"
date: 2008-04-29
forum: Multimedia Software
---

### Post by andrewc2005 on 2008-04-29
This is kind of bizarre; I downloaded RealPlayer 11 but can't install it on 8.04.  Downloaded RealPlayer11GOLD.bin, changed the permissions to make it executable, but the system still won't recognize it:

# ./RealPlayer11GOLD.bin 
bash: ./RealPlayer11GOLD.bin: No such file or directory
# chmod 755 RealPlayer11GOLD.bin 
# ls -ltra
total 60916
-rw-r--r--  1 andy andy  1328058 2008-04-29 14:49 lame-3.97.tar.gz
-rwxr-xr-x  1 andy andy 53459141 2008-04-29 15:26 ati-driver-installer-8-4-x86.x86_64.run
drwxr-xr-x 35 andy andy     4096 2008-04-29 17:12 ..
-rwxr-xr-x  1 andy andy  7502048 2008-04-29 17:17 RealPlayer11GOLD.bin
drwxr-xr-x  2 andy andy     4096 2008-04-29 17:17 .
# ./RealPlayer11GOLD.bin 
bash: ./RealPlayer11GOLD.bin: No such file or directory
 
Any suggestions anyone?

---

### Post by lancern on 2008-04-30
Just found a .deb for it right here on the forum
made by jen1963..just tried it and its working.:)..
Thank you jen1963

[http://ubuntuforums.org/showthread.php?p=4737528](http://ubuntuforums.org/showthread.php?p=4737528)


[http://i164.photobucket.com/albums/u13/unlancer/snapshot16.jpg](http://i164.photobucket.com/albums/u13/unlancer/snapshot16.jpg)

---

### Post by riyasmp on 2008-04-30
hi guys

i recently upgraded to 8.04 and my real player stoped working.i used to listen to [www.raaga.com](www.raaga.com) which is a online audio streaming site based on real player (jukebox).

i tried installing .bin file and .deb file (http:/www.tuxwerx.com/realplayer_11.0.0.4028-20080226_i386.deb). the latter gor installed alright but seems that there is a plugin problems. mozilla will never play the real audio songs. especially [www.raaga.com](www.raaga.com) which syas loading.

can anyone help me.

R

---

### Post by lancern on 2008-04-30
I just tried that site and did not work for me..
it would start to load..then the player would say stopped..no clue..

The only streaming audio I listen to is 
[http://www.di.fm/](http://www.di.fm/) 
I just dload the .pls files and drag and drop them into realplayer or right/click them and open with a player I want to use..

---

### Post by riyasmp on 2008-04-30
downloading the fils is not possible in sites like raaga. u can listen to but cannot download.

i was wondering if ther is any fix for it or to believe that windows is winning 

:-(

---

