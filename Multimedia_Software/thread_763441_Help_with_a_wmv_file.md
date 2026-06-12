---
title: "Help with a wmv file?"
date: 2008-04-23
forum: Multimedia Software
---

### Post by baksiidaa on 2008-04-23
I'm trying to open the video stream at [http://byubwmv.byu.edu/byudevo/2008/03/devo03252008.wmv](http://byubwmv.byu.edu/byudevo/2008/03/devo03252008.wmv)
It's not working in VLC, Totem, or mplayer.  
I can play the video on a Windows machine, so it's not a server-side problem.  

Any suggestions?

---

### Post by Bubba64 on 2008-04-23
Go to add remove and open up all available and type in gstreamer which will bring up gstreamer extras I installed all of them and the Ubuntu extras. This is on Hardy I don't remember if these are all in other distributions.

---

### Post by baksiidaa on 2008-04-23
Totem now gives me an error message saying "Could not demultiplex stream."

---

### Post by Bubba64 on 2008-04-23
You probably have to have medibuntu in the repositories list for the upgrades I suggested here is a link on how to install them.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by baksiidaa on 2008-04-23
I already had Medibuntu included in my sources list.  Does the video work for you?

---

### Post by Bubba64 on 2008-04-23
[QUOTE=baksiidaa;4770918]I already had Medibuntu included in my sources list.  Does the video work for you?[/QUOT

Yes, but check out this post which is good but you can install most of this stuff by add remove rather than hassle with the terminal if your not familiar with it yet.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by cor2y on 2008-04-24
Its a bad setup of the server and perhaps how it was encoded.
To view this you will need totem-xine for streaming playback.
If you wish to download it then the commandline mms downloader mimms (its in synaptic)
from the terminal ```
 mimms mms://byubwmv.byu.edu/byudevo/2008/03/devo03252008.wmv
```
replace the http with mms in the source address. 
So for totem-xine or any of the libxine media players just use mms://byubwmv.byu.edu/byudevo/2008/03/devo03252008.wmv

---

