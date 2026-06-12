---
title: "Carmen by Livio Radio"
date: 2011-06-30
forum: Multimedia Software
---

### Post by elcalamar on 2011-06-30
Hello there,
I am wondering if any in the Ubuntu community owns a Carmen Car Radio player by Livio Radio. The program to save internet radio to the device is written in Java, however I am not able to run it either using WINE or using Open JDK. 

The Carmen Player does work well with Banshee, it is the internet radio that is not working.

Any help would be truly appreciated.

---

### Post by elcalamar on 2011-09-11
Ok, I am going to post my (imperfect) solution hoping that it will help future users:
The Carmen device made by Livio Radio works as a MP3 player/usb drive with Ubuntu: the .exe file to get the software to work does not execute under Wine.

You can place all your mp3 files in the mp3 folder and the device will pick it up in the car.

For streaming radio capture, I am using Chrome, [www.tunein.com](www.tunein.com) and VLC:
1) Select the internet radio you want to record with tune in radio.
2) Look for the streaming source using Chrome's "View Page Source" option (right-click on the page to find it).
3) Copy the streaming source to VLC media player. Hit the 'record' button. It will be saved in your Music folder.

The 'real' solution would be to make the .exe work under Wine or the swf file executable. Ubuntu does not let me turn any swf on a usb drive into an executable bit.

---

