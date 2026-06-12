---
title: "video vsync vblank fix"
date: 2010-01-21
forum: Multimedia Software
---

### Post by Cresho on 2010-01-21
Hello!

I don't know if anybody has any better but I'm posting this for anybody who is concerned about video tearing issues in kubuntu or ubuntu karmic koala 9.10.

My problem was I couldnt view high definition videos nor Flash videos without it tearing but now it works fine.  Here is the method and I'm posting this info because I would like to know of a different way of sync video instead of the one I'm posting.

I'm assuming you installed the nvidia drivers and you already checked mark in nvidia-settings the opengl sync (this also fixes desktop tearing) and in video the vblank sync is checked.  ALso in system settings in kde, make sure you have in system settings->desktop effects->advanced
comp type: opengl
openglmode: pixmap texture
texture filter:bilineear
put checkmarks on both enabled direct rendering and use vsync.



now open kate up and past this into it.

```
#!/bin/bash
sleep 3 && killall kwin;
sleep 2 && nvidia-settings -l;
sleep 2 && kwin;
```

and save the file as nvidia-settings-load.sh and then right click on it then properties,  and under permissions, give exec rights.

now you want this to load up and make sure you put it somehwere where you cant delete it or dont want to delete it...like a scripts folder.

open system settings->advanced tab->autostart
then you add script, navigate to your sh script you created add it and have it startup normally and not as a pre kde startup.

save, reboot and go to vimeo and enjoy flash video free of flickering or video tearing.

---

