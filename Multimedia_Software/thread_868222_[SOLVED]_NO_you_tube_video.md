---
title: "[SOLVED] NO you tube video"
date: 2008-07-23
forum: Multimedia Software
---

### Post by el diego on 2008-07-23
Can anyone help.??? I cannot view YOUTUBE videos.The ads are all fine.Programmes seem to be loaded OK..I get a flash of a video then a blank....I have Adobe flash 9 , FireFox 3 and Ubuntu8.
Cheers 
Paul

---

### Post by NilsE on 2008-07-23
Try to remove (if it is installed) then reinstall flashplugin-nonfree in Synaptic

---

### Post by collinp on 2008-07-23
in terminal run 
```
sudo apt-get remove flashplugin-nonfree
```
then run ```
sudo apt-get install flashplugin-nonfree
```

If it still messes up, download the plugin from [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash), extract the archive, then navigate into there with terminal and run ./flashplayer-installer.

---

### Post by dentaku65 on 2008-07-23
I would say to try
```
sudo apt-get --purge remove flashplugin-nonfree
```

Then reinstall as suggested by Hellow

---

### Post by el diego on 2008-07-24
> **el diego said:**
> Can anyone help.??? I cannot view YOUTUBE videos.The ads are all fine.Programmes seem to be loaded OK..I get a flash of a video then a blank....I have Adobe flash 9 , FireFox 3 and Ubuntu8.
Cheers 
Paul

Thanx for advice....Problem solved by deleting GNASH from the system and then installing the latest Adobe Flash.....Plenty of help in forums...
Paul

---

