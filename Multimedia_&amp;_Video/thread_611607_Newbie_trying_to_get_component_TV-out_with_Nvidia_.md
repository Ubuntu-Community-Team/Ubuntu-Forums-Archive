---
title: "Newbie trying to get component TV-out with Nvidia 6600 GT"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by simgrant on 2007-11-13
Hi all,

  I am new to Ubuntu (7.10 x89_64) and in fact more or less new to Linux (Haven't used it since it was first popular). I find it fairly straightforward to use but I am baffled by one thing. I want to have Tv out through Component cable to my PAL widescreen tv (576i). the xorg.conf file is a bit over my head and I am having no luck with the nvidia-setting utility. I know 576i is supported by my card as it works in windows XP. Is there an easy way to do this?

Regards, Simon.

---

### Post by Scorpuk on 2007-11-13
Have you tried booting your computer up with the S-Video cable connected to your TV's S-Video in port to see what happens?


It really should just work. Unless you want to do something fancy other than cloning your 1st screen.


If your TV doesnt have an S-Video port does it have an S-Video option for a scart socket. ie: AV2S (note the S at the end). Then use a Scart adaptor with an S-video port on it.

---

### Post by smithman89 on 2007-11-13
If the display does not automatically work, run:```
gksu nvidia-settings
```to open up the nvidia user control panel.  Click X server display configuration, and it will show you your currently active (and non active) screens.  If TV-O is not shown, click Detect Displays to refresh the list.  On my computer, TV-O is detected even if it is not plugged in.  Now you can click Save to X Configuration File, then either configure it in nvidia-settings or screens and graphics.

---

### Post by simgrant on 2007-11-14
Thanks for replying Scorpuk and smithman89,

  actually TV only has component or composite, no Svideo, and for movies composite is lousy. I do see the boot up text but the Ubuntu loading screen is grainy and black and white.  In an Xsession there is garbage or no signal on tv screen. Any attempt to reconfigure in nvidia-setting or screens and graphics results in X crashing, besides which I can't choose a correct resolution for the TV. 

  Occasionally if there is a desktop on my TV is is a funny colour and shimmering. I don't think it is receiving a component signal of the correct resolution. There have been other solutions to this problem on this forum, could I just copy the last section of their xorg.conf file? am not very knowledgeable so a bit stuck. I heard someone else on another thread say they go it to work with Mythbuntu control centre so will try installing this and see if this works.

  I am liking how Ubuntu has intuitive GUI to configure programs but it appears in this case manual editing may be the only solution. Hope I don't have to rely on windows for watching movies.

Regards,

Simon.

---

