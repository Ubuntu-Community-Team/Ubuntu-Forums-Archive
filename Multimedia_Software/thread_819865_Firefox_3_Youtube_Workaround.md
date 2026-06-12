---
title: "Firefox 3 Youtube Workaround"
date: 2008-06-05
forum: Multimedia Software
---

### Post by EMCGFX on 2008-06-05
I have this weird but ever since I've installed Ubuntu 8.04 final When I open my Firefox 3 and go to youtube to watch a video, it plays three seconds and stops. If you know how to fix this, please due reply. Meanwhile, I found small workaround ;)

Find any youtube video you like to watch, for exp. [http://www.youtube.com/watch?v=XPaOtetuoU4](http://www.youtube.com/watch?v=XPaOtetuoU4)

Open VideoDL.org site and paste your link in there, then simply download it by righ-click > save or click on download to watch the video in your default player.

---

### Post by SouthernPott on 2008-06-05
My problem was a little different.  The video would run for a bit then stop as it was buffering.  It would repeat this several times.

I just clicked on Pause and let the video download completely, then ran it.  

This is on a wireless desktop (Ubuntu 8.04) I set up for my neighbor this past weekend so that they could use my network.  I attributed it to the distance from the access point.

---

### Post by mastermindg on 2008-06-05
Sounds like an issue with your network connectivity. I've got Firefox 3 Beta on Hardy (stock) with Flash and I'm not having any issues.

---

### Post by FuturePilot on 2008-06-05
> **EMCGFX said:**
> I have this weird but ever since I've installed Ubuntu 8.04 final When I open my Firefox 3 and go to youtube to watch a video, it plays three seconds and stops. If you know how to fix this, please due reply. Meanwhile, I found small workaround ;)

Find any youtube video you like to watch, for exp. [http://www.youtube.com/watch?v=XPaOtetuoU4](http://www.youtube.com/watch?v=XPaOtetuoU4)

Open VideoDL.org site and paste your link in there, then simply download it by righ-click > save or click on download to watch the video in your default player.

Do you have any other application try to access the sound system? I've found that sometimes this happens when there is a conflict with PulseAudio and another application since Flash doesn't play nice with PulseAudio. Try giving Firefox a restart. That fixes it when it happens to me.

---

### Post by bossa on 2008-06-05
Hi Guys 
I have been having a similar problem where Firefox (beta) Closes on many Youtube vids . I found this thread that helped me [http://ubuntuforums.org/showthread.php?t=747590](http://ubuntuforums.org/showthread.php?t=747590)
I ended up using the swfdec-mozilla plugin .Works well.
Hope this helps

PS I find Downloadhelper (Firefox add on) great for downloading FLV

---

### Post by rock4christ on 2008-06-05
im having an issue where I cant pause or change volume, and the loading circle stays in the center of the vid even while playing

---

### Post by knavarathna92 on 2008-06-05
use swiftweasel :-)  It's faster and it has debs for RC1 out alrady (32 and 64 bit) that wont break xulrunner.  It also imports your settings from Firefox so it's practically painless.  I've also found that it handles youtube flawlessly when compared to how Firefox does, it always works.

---

### Post by EMCGFX on 2008-06-07
None of this fixes work for me, just my workaround ;-) It's funny I did not have this problem in 7.10 final.

---

### Post by CREEPING DEATH on 2008-06-07
My Pidgin sounds go away after any flash sites in addition to the above mentioned problems...

CD

---

### Post by EMCGFX on 2008-06-09
Yeah, when I've reinstalled my flash sound disapered too. This is the most anoying bugs in 8.04.1 that I have. If anyone knows how to fix it, please reply.

---

### Post by Steve M on 2008-06-09
I am also having problems with FireFox closing when trying to play videos on You Tube?

:confused:

---

### Post by cariboo on 2008-06-09
Thanks to odinfromvalhalla for this link:

[http://www.myscienceisbetter.info/projects/install_flash_player_10_ubuntu64bit](http://www.myscienceisbetter.info/projects/install_flash_player_10_ubuntu64bit)

Just download the script save it, then make it executable

```
chmod +x saved_filename
``` the run it as root.

```
sudo ./saved_filename
```

I been running flash10 for about a month now and have no problems.

Jim

---

### Post by EMCGFX on 2008-06-10
Thank you, cariboo907 will defently try this out ;-)

---

