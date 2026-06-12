---
title: "flash + adultswim = ?"
date: 2009-07-24
forum: Multimedia Software
---

### Post by bionnaki on 2009-07-24
Using Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12 + Flash 10,0,22,87 from the repos.

When I play a video like this [episode]("http://www.adultswim.com/video/?episodeID=8a25c392146def1901146f1665cc0002") and then go to fullscreen, it flashes.

any idea on how to correct this? I am not using compiz or any desktop effects (if that makes any difference). anyone else having this problem?

thanks

---

### Post by Stochastic on 2009-07-24
Moved to Multimedia & Video

---

### Post by HappyFeet on 2009-07-24
Works for me. You can try my method of installing flash if you want. Go to synaptic and completely remove flash. Then go [here]("http://get.adobe.com/flashplayer/") and download the tar.gz flash file. Right click it and "extract here". Go into the folder and copy the **libflashplayer.so** file. Then go to your home folder and do ctrl-h to show your hidden folders. Open your .mozilla folder and create a new folder and name it **plugins**. Paste the libflashplayer.so file into the plugins folder. Restart firefox if open.

---

### Post by kokoshka on 2009-09-10
Same issue...manually adding the latest flash plugin didn't help.  Only 512 ram, p4 ati 9600.

Screen flickers blue with just the web page background. 

Any other ideas?

---

### Post by The Unmaker on 2009-09-23
> **kokoshka said:**
> Same issue...manually adding the latest flash plugin didn't help.  Only 512 ram, p4 ati 9600.

Screen flickers blue with just the web page background. 

Any other ideas?

This is a flash (on Adobe's side) issue. I have the same problem when viewing the videos in full screen. A lot of people open up adultswim and only view a video to see that it works, but never in full screen. This problem happens everywhere the new flash is installed (didn't occur with the nspluginwrapper, but this is a waaay better alternative).

It will just have to wait until the bugs get worked out.

---

### Post by BryanFRitt on 2011-04-12
What fixed the adultswim flashing videos for me was to check the flash option:
"Allow third-party Flash content to store data on your computer."
[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager03.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager03.html)
p.s. yes that is the actual "Global Storage Settings panel" and not just a picture of it.

---

