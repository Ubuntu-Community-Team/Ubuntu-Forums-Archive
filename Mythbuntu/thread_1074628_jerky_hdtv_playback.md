---
title: "jerky hdtv playback"
date: 2009-02-19
forum: Mythbuntu
---

### Post by itlarson on 2009-02-19
I have a newly built mythbuntu box based on the AMD x2 4850e, Asus motherboard with nvidia 8xxx, and 4g ddr2 800.  When playing hdtv it periodically stutters.  Changing resolutions or playback settings has little effect.  Does anyone have any suggestions?

---

### Post by Monsieur Gonzalez on 2009-02-19
[http://ubuntuforums.org/showthread.php?t=1063102]("http://ubuntuforums.org/showthread.php?t=1063102")

---

### Post by newlinux on 2009-02-19
> **itlarson said:**
> I have a newly built mythbuntu box based on the AMD x2 4850e, Asus motherboard with nvidia 8xxx, and 4g ddr2 800.  When playing hdtv it periodically stutters.  Changing resolutions or playback settings has little effect.  Does anyone have any suggestions?
Tell us what settings you modified. Tell us the format of the HDTV streams you are trying to playback. Show us the logs from mythfrontend when you have the stuttering problems. It can be a lot of different things. More info will help us help you.

---

### Post by itlarson on 2009-02-19
I am playing back atsc of the air.  1080i is most problematic.  I have tried most deinterlace combinations under playback at 1080p and 720p.  Logs will have to wait untill I am home.  I had good playback on a less powerful system before it died.

---

### Post by itlarson on 2009-02-19
Hmm-  It's better after a reboot.  Weird that it's worse if interlace is off.  Nothing to report from the logs.

---

### Post by newlinux on 2009-02-19
if you want more detailed information from the frontend log do:

```

mythfrontend -v playback -l <logfilename>

```

That will give you more if you have problems again.

---

