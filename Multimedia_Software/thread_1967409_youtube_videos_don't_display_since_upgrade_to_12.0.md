---
title: "youtube videos don't display since upgrade to 12.04"
date: 2012-04-28
forum: Multimedia Software
---

### Post by volkerbradley on 2012-04-28
My system is 64-bit Ubuntu 12.04 using a Nvidia GeForce GTX 285M Graphics with 1GB GDDR3 Video Memory.
Since upgrading to Ubuntu 12.04, I can no longer see youtube videos in Firefox, Totem or Minitube.
I've included screenshots of what I see in Firefox.
When I right-click on the Firefox section of where the video should display, I see the following options: Copy, Open with "Movie Player", Fullscreen. When I choose Open with Movie Player, Totem opens and displays an error message which says: An Error occured.  Location not found. Ive included a screenshot of the Totem error message as well.
Any suggestions on how I can determine why I can no longer see youtube videos?

---

### Post by xyzzyman on 2012-04-28
Verify flash itself is installed: 

sudo apt-get install adobe-flashplugin

If it is installed, remove the totem firefox plugin:

sudo apt-get remove totem-mozilla

Most likely you used to use the 32bit flash, the upgrade then removed it, but never installed the 64bit flash.

---

### Post by volkerbradley on 2012-04-28
> **xyzzyman said:**
> Verify flash itself is installed: 

sudo apt-get install adobe-flashplugin

If it is installed, remove the totem firefox plugin:

sudo apt-get remove totem-mozilla

Most likely you used to use the 32bit flash, the upgrade then removed it, but never installed the 64bit flash.
Thank you very much for your response.  Your suggestions solved my problem.
Here is what happened:
sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
adobe-flashplugin is already the newest version.
Then did apt-get remove totem-mozilla.  
Then tried to play the video again and still saw the same error messages.
Then rebooted.
Now youtube videos play again

---

### Post by lovinglinux on 2012-04-28
Now replace totem-mozilla with gecko-mediaplayer, so you can play other types of videos.

```
sudo apt-get install gecko-mediaplayer
```

---

### Post by volkerbradley on 2012-04-28
Done!
Thanks again.

---

