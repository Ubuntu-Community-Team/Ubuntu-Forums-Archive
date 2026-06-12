---
title: "How to apply xmms skins? [ubuntu hardy 8.04]"
date: 2008-06-24
forum: Multimedia Software
---

### Post by Lenz on 2008-06-24
I downloaded the new skins and I still can't apply them. I've gone through most of the forums about this but I still can't find the xmms skins folder. Ive searched in /usr/share/xmms and all i see is this XPM image. When I go to the home folder either it doesn't show any xmms folder. i only see the typical documents, pictures, music, templates, videos folders...you know what i mean...eeeks:confused:totally out of it...im still pretty new to ubuntu. help??

---

### Post by cozmicharlie on 2008-06-24
If you open xmms and in the menu go to Options>skin browser it should show the skins available and you can change them.

---

### Post by Fuzzban on 2009-06-10
.xmms/Skins the the folder, it appears to be hidden if you try looking for it in the browser since its a user config file. ie to install your skin, if its in a .tar.gz use Archive manager->Extract->(user) scroll to .xmms and put it in Skins. If its already a .wsz file open terminal and (this is what I do) sub in where you downloaded it in place of mine:

# sudo cp /home/denis/Desktop/(skin name).wsz .xmms/Skins

Hope that helps.

---

### Post by Bodrey on 2009-12-19
I'm having the same problem.  Downloaded and extracted the Winamp 5 skin for XMMS but it doesn't show up in Options|Skin Browser.  Where to place the BMPs?  There is no XMMS folder under usr/share.

---

### Post by Dennis N on 2009-12-19
XMMS skins can be placed in the .xmms/Skins directory within your home folder. You don't need to extract anything. Simply place the .tar.gz file into that directory.

I might be mistaken, but I think you may need to use WinAmp Classic skins. Mine are from WinAmp versions 2.xx - Most of those will work.

Alt+S brings up the skin chooser.

---

