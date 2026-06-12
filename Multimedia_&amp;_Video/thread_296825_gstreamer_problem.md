---
title: "gstreamer problem"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by eastern_strider on 2006-11-10
How can I set up gstreamer to listen to radio streams in Edgy?

I installed the following packages:

```
gstreamer0.8-plugins
totem-gstreamer
```

hoping that I'll have a totem-gstreamer executable. But apparently that is not the case. I don't have any application called totem-gstreamer.

Any suggestions?

Thanks,
eastern_strider

---

### Post by catlett on 2006-11-17
Hi e_s,
I saw this thread unanswered and recognised it was you. Are you still having trouble streaming music? I will assume you are and if you aren't, all the better. :D 
Enter these commands to install "streamtuner" and "streamripper". (streamtuner shows up in the menu under Applications<Sound & Video) 
```
sudo apt-get install streamtuner
```
```
sudo apt-get install streamripper
```
Add this command to install mp3 support and ogg vorbis support
```
sudo apt-get install mpg321 vorbis-tools
```
Enter this to update your menu.
```
update-menus
```

---

### Post by eastern_strider on 2006-11-20
Thank you very much. My problem was still unsolved, but not anymore :)

Cheers
eastern_strider

---

