---
title: "Screen resolution problem"
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by igrachev on 2006-07-05
hello i am using kubuntu and i got normal screen resulution about 1280/1024 and it was good buy i dont know how i havent change or modify any graphical files but my resolution now is 640/400 and i can make it better from desplay options i dont know why i cant move screen size button to make my resolution better i didnt change any hardwaer and i log to screen resolution as su ...
Do you know why my resolution have changed and how can i have it back to normal ???

---

### Post by Raistlin355 on 2006-07-05
[QUOTE=igrachev]hello i am using kubuntu and i got normal screen resulution about 1280/1024 and it was good buy i dont know how i havent change or modify any graphical files but my resolution now is 640/400 and i can make it better from desplay options i dont know why i cant move screen size button to make my resolution better i didnt change any hardwaer and i log to screen resolution as su ...
Do you know why my resolution have changed and how can i have it back to normal ???[/QUOTE]

Not sure what the problem is from this post, I am assuming that your screen res WAS 1280/1024 and then changed to 640/400??  If this is happening then you might take a look in the file /etc/X11/xorg.conf

Type into console: sudo gedit /etc/X11/xorg.conf

Your looking for the part where it lists all the screen resolutions.  See if the res you want is in there, if not add it.  Then reboot and you should be able to change back to it.  If your having a problem with it STAYING on the setting to specify take all the screen resolutions out of the xorg.conf file except the one you want, that'll force it to that screen res.

---

### Post by Gustav on 2006-07-05
You can try to issue this command:```
sudo dpkg-reconfigure xserver-xorg
```and answer the questions (if you don't know the answer just go for the suggestions).

It might be smart to back up the file /etc/X11/xorg.conf first.

---

### Post by igrachev on 2006-07-05
well my problem seems to be a bit diferent i open the xorg.conf file and saw that all is in proper order and should work fine but i decided to reconfigure it by GustaV's command but it is still same. i actually find a couple of ways to change the resolution and it changes it but i see only 640/480 picsels of my screen and is i make biger resolution as 1280/1024 i start at the bottom left corner and i can move my screen through the desktop (when i move my mouse cursor to right end of the screen i scroll through the desktop) i think this is not problem of resolution i must fix my screen fit into the monitor frame but i dont have any idea how .... Do you ?

---

### Post by Gustav on 2006-07-06
Look at this thread for an good howto on how to solve your problem (it raised my resolution from 1280x1024 to 1600x1200)

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

