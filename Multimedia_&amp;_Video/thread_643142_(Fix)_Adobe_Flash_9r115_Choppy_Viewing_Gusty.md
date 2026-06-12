---
title: "(Fix) Adobe Flash 9r115 Choppy Viewing Gusty"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by CHFFriday on 2007-12-17
If you update Flash Player to 9r115 you may have a problem. Flash Player movies may be choppy and out of sync.

To fix this I had to re-install 9.0r84

This is the how to:

1. Go to System-> administrator-> Synaptic Package Manager
Click on search
Enter Flash Player
Look for Flash Player nonfree. It should have a Green box next to it.
Click on the box and choose remove all
This will stop all flash player activity.
Reboot the PC

2. Next Go to Places-> Home->.mozola -> plugins.  You will have to turn on “Show Hidden Files” to see this.   In the Plugins folder delete flashplayer.xpt and libflashplayer.so if they are there or if you prefer rename them by changing the extentions. There is probably a why to do this in Terminal but I’m not that good let and I don’t want to mess-up anybody’s system with the incorrect coding.
   
3. Start Firefox and go to Google. Do a search of Flash Player Archive. 
Or try this Link. This is Adobe Tech Note 14266 [http://www.adobe.com/go/tn_14266](http://www.adobe.com/go/tn_14266)
Download file fp9_archive.zip to you desktop.

This is a Zip file with all the Flash Players. Open the zip file and find the Install_Flash_Player_9r48_Linux.tar.gz Then extract it to your desktop. Click on this folder. Then run the installer. 

Reboot the PC

You Flash Player should work.

CHFFriday

PS If anyone wants to make changes to this please do so!

---

### Post by s14sh3r on 2007-12-23
Thanks! I was having trouble with Youtube videos being really choppy, so I searched and found lots of people having the same problem but no solutions. Going back to the older version of Flash did the trick, flash videos play properly now. =D>

---

### Post by skullhead on 2007-12-24
ok i did everything you said up there and now the video in youtube dosent lagg but now i have no audio

---

### Post by mblind on 2008-01-10
Flash player archive
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1)

One problem.. When you downgrade you lose the ability to have fullscreen video.. 
Can anyone else get it?

check out 
[http://nightly.msnbc.com](http://nightly.msnbc.com)

play video then try full screen

---

