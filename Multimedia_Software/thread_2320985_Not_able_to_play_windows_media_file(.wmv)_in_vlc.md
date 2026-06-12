---
title: "Not able to play windows media file(.wmv) in vlc"
date: 2016-04-19
forum: Multimedia Software
---

### Post by Ajay_Dasila on 2016-04-19
Hey there! I was trying to open a **wmv** file via **vlc** but everytime I did, my computer freezes. I researched a bit and found installing ***ubuntu-restricted-extras*** might do the trick. But after installing it, the problem exists. Computer freezes completely. At first, I was able to open a terminal window using **ctrl+alt+F1(or F2)**, but after a couple of times, even that didn't worked. Any help on the issue would be appreciated.

---

### Post by QDR06VV9 on 2016-04-19
If you are still using 14.04(Trusty)
You will need FFmpeg, And this PPA for [B]Trusty
[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
[/B]Please Read the whole page for use cases**.**
Kind Regards

---

### Post by Ajay_Dasila on 2016-04-20
I am using 15.10. Though, I installed **FFmpeg** for 15.10. Still it freezes. I just found out that I didn't installed **ubuntu-restricted-extras** correctly. I downloaded them just fine but when it prompted me to press **<Ok>**, I closed my terminal without knowing the fact that it didn't installed. What are my options now?

---

### Post by SeijiSensei on 2016-04-20
Try "sudo apt-get install -f" and see if that fixes things.  If not, try "sudo dpkg --configure -a".

For a player, I suggest you install **mpv** after adding this PPA: [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests).  Then install **smplayer** which is a nice graphical front-end to mpv and its older cousin mplayer.  You can install smplayer from the Ubuntu repositories or from the developer's PPA here: [https://launchpad.net/~rvm/+archive/ubuntu/smplayer](https://launchpad.net/~rvm/+archive/ubuntu/smplayer).  I don't know what smplayer's default player is these days, so to make it mpv, go to Options > Preferences > General and make sure /usr/bin/mpv is listed as the player executable.

---

### Post by QDR06VV9 on 2016-04-20
SeijiSensei's advice is good to follow.
Just to be sure you get a good install this time
```
sudo apt-get install --reinstall ubuntu-restricted-extras
```
Leave your terminal open to accept any licensing agreements.
Let us know how you make out.
Kind Regards

---

### Post by mc4man on 2016-04-20
Try opening vlc > Tools > Preferences > Input & Codecs & disabling hardware-accelerated decoding, save settings & see if better

---

### Post by yoshii on 2016-04-21
I use VLC regularly.  I don't think you should need to install any codecs.  The whole point and design of VLC is that the user doesn't need to install codecs because they come provided inside of VLC itself.  

What might help is if you change the Video output option to "OpenGL" instead of "automatic" which is the default.  Clearly stuff like "DirectX" won't work on Linux, but I have had success fixing playback errors by changing to "OpenGL".  

Also, try some other WMV files to make sure that the files you are trying aren't corrupt.

---

