---
title: "Flash plays but can't click on buttons?"
date: 2010-05-02
forum: Multimedia Software
---

### Post by Vanillalite on 2010-05-02
So yeah I've seen threads on getting flash installed, and it appears to be installed. Youtube videos play and all that jazz. You got to Adobe's webpage and it says I have the latest released version installed.

Problem is I can't click on any of the buttons IN the videos. Like in youtube I can't click pause, change the video resolution, or move the bar to fast forward or rewind.

I'm kind of at a loss cause it IS installed, and reinstalling doesn't do anything in FF. I mean if I uninstall videos don't play, and if I reinstall they play. Still can't click on anything though.

EDIT:Also it DOES work just in youtube if I get the new interface. It won't work in the old interface... WTF

SPECS: Lucid Lynx 10.04 AMD64 + Gnome 2.3 + FF 3.6.3 + ATI Drivers + Compwiz 

PS: Thanks in advance as I'm sort of a Linux n00b, and if you need more info let me know!! :)

---

### Post by Jackson024 on 2010-05-02
Same issue, flash plays and that is about it, cannot do anything else.

---

### Post by WinterRain on 2010-05-02
Remove any flash you have installed, and get the 64bit flash file here [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Then extract it and put it in /usr/lib64/mozilla/plugins and restart firefox. Works perfect for me.

If you are unsure how to do this, to extract the file, just right click and "extract here". Make sure it's on your desktop. Then do in terminal: (you can copy and paste it)
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Restart firefox, done.

---

### Post by bark50 on 2010-05-03
Someone posted a handy utility for getting rid of your old flash and installing the new one:  [http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595").  Click on "Download" in the first post.  From the window that opens up, download the 64-bit Ubuntu flash and save it to your desktop.  Right-click on the downloaded file and choose properties.  In the box that comes up, click on the "Permissions" tab.  Near the bottom of the tab, put a check mark in the box "Allow executing file as program" and close the box.  Now double-click on the downloaded file and a box will open up that will allow you to "Remove flash" (do this first) and then "install flash (X64)".  This worked for me.  I didn't mess with the "Install Flash Beta" option.

---

### Post by WinterRain on 2010-05-03
> **bark50 said:**
> Someone posted a handy utility for getting rid of your old flash and installing the new one:  [http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595").  Click on "Download" in the first post.  From the window that opens up, download the 64-bit Ubuntu flash and save it to your desktop.  Right-click on the downloaded file and choose properties.  In the box that comes up, click on the "Permissions" tab.  Near the bottom of the tab, put a check mark in the box "Allow executing file as program" and close the box.  Now double-click on the downloaded file and a box will open up that will allow you to "Remove flash" (do this first) and then "install flash (X64)".  This worked for me.  I didn't mess with the "Install Flash Beta" option.

Actually, my method has less steps, and is brainless. I'm sure the other method works, but why screw around with scripts and permissions? Right click the [flash.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz") file and *extract here*. Run the one line I gave above, and you're done.

---

### Post by Jackson024 on 2010-05-03
> **WinterRain said:**
> Remove any flash you have installed, and get the 64bit flash file here [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Then extract it and put it in /usr/lib64/mozilla/plugins and restart firefox. Works perfect for me.

If you are unsure how to do this, to extract the file, just right click and "extract here". Make sure it's on your desktop. Then do in terminal: (you can copy and paste it)
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```Restart firefox, done.

Worked perfect, thanks!

---

### Post by Maximus_ARNP on 2010-05-09
Thanks. Worked just perfect.

---

### Post by treyk4 on 2010-05-13
> **WinterRain said:**
> Remove any flash you have installed, and get the 64bit flash file here [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Then extract it and put it in /usr/lib64/mozilla/plugins and restart firefox. Works perfect for me.

If you are unsure how to do this, to extract the file, just right click and "extract here". Make sure it's on your desktop. Then do in terminal: (you can copy and paste it)
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Restart firefox, done.

Worked great, thanks! I'm remembering why I love Ubuntu so much... the community!

---

### Post by Zaizeku on 2010-05-15
> **WinterRain said:**
> Remove any flash you have installed, and get the 64bit flash file here [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Then extract it and put it in /usr/lib64/mozilla/plugins and restart firefox. Works perfect for me.

If you are unsure how to do this, to extract the file, just right click and "extract here". Make sure it's on your desktop. Then do in terminal: (you can copy and paste it)
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Restart firefox, done.

Thanks a lot this worked for me :P

---

### Post by Terc on 2010-07-22
Sounds great, but I'm on 32bit Ubuntu because I'm running older Pentium M hardware.  Any fix for people like me?

---

### Post by Joe Darkless on 2010-07-24
> **Terc said:**
> Sounds great, but I'm on 32bit Ubuntu because I'm running older Pentium M hardware.  Any fix for people like me?
You should run:
```
sudo apt-get install flashplugin-nonfree
```to make it working properly on x86 system

---

