---
title: "MythTV: tuner unavailable, already in use"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by TomG24 on 2007-05-05
Hi folks,

I'm using the newest Fasty Fawn and would like to use MythTV with it. I have a Pinnacle PC TV Pro tv tuner card with a bc878 chipset.

I followed [this guide]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend") to set up MythTV.

Although setting up MythTV works fine, I'm unable to use my tv tuner card.

When I check it's status in Information Center -> System Status -> section "Tuner Status", it states "Tuner 1 is unavailable (Tuner 1 [V4L:/dev/video0] is unavailable)".

Even when try to watch TV, I get this errorr: "MythTV is already using all available inputs for the channel you selected, if you want to watch an in-progress recording select one from the playback menu. If you want to watch livetv cancel one of the in-progress recordings from the delete menu."

I added my tv card in the mythtv-setup as well (section capture cards) with default settings and added a tv source (with my country -Belgium-). I'm unable to scan channels as well, since the tv card seems to be missing in the drop down box.

Did I forget something or could there be another cause?

thanks

---

### Post by Lem on 2007-05-05
Check that you've defined a video source in the setup with your chosen capture card.

---

### Post by nbv4 on 2008-01-27
> **Lem said:**
> Check that you've defined a video source in the setup with your chosen capture card.

could you (or anyone else) be more specefic as to what this means? I'm getting the exact same error, but as far as I can tell, my "video source" section of mythtv-setup seems to be correct...

---

