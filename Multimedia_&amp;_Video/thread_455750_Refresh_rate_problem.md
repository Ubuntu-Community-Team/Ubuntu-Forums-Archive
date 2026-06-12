---
title: "Refresh rate problem"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by Rebeldawg on 2007-05-26
I've got a problem with my refresh rate, I've tried the nvidia-glx-new, nvidia-glx, nvidia-glx-legacy, and both 100.14.0x series drivers and when I try to change my refresh rate to something higher than 50, the only choices it gives me is from 50-57... I've got a nvidia geforce fx 5500 video card, and my monitor is detected as a compaq 7500 monitor which is what windows xp detected it as too before I switched... I know the HorizSync is 30-70 and the VertRefresh is 50-140, but I still get crappy refresh rates.... I've included my Xorg.0.conf file so any help would be appreciated.. if you need any more info I'll do my best to provide it.... thanks in advance..




P.S. - I had to zip it so that I could upload it since it was too big

---

### Post by Nythain on 2007-05-26
gksudo nvidia-settings
change refresh rate there
for some reason ubuntu has issues with refresh rate detection and nvidia cards... im running at like 75hz and it thinks im at like 50something

---

### Post by MeathooK427 on 2007-05-27
Is there anyway to verify for sure what refresh rate is being run? Reason being, nvidia-settings on my system says it's running at 60 (which I'm going for) however KControl is saying 50. I'm still also getting tearing problem in videos. Sorry for the threadjack.

---

### Post by Rebeldawg on 2007-05-27
I've actually used the gksudo nvidia-settings and set my refresh rate to 85 but whenever I play
world of warcraft it only allows me to play at 60 with a multisample of  51???.... I like ubuntu for the
most part except for the video driver issues... I'll add my xorg.conf file to see if it helps any..

---

