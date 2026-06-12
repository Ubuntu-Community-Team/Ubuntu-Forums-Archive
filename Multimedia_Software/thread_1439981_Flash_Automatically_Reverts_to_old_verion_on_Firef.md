---
title: "Flash Automatically Reverts to old verion on Firefox"
date: 2010-03-26
forum: Multimedia Software
---

### Post by KaiDog on 2010-03-26
I think I have multiple versions of flash installed on my computer, because each time I restart Firefox it reverts back to Flash 9 and I can't view hulu videos and youtube videos don't play at all. The youtube videos show up, but there's no sound and they freeze after a few seconds and firefox freezes and gets the error message "failed to allocate memory" in the command line. I'm not sure how to approach this since I'm still trying to get the hang of linux. Any suggestions?

---

### Post by fixitdude on 2010-03-27
Flash is put in many places and you might have a old version in there someplace.

Try the stuff I posted in this thread:
[http://ubuntuforums.org/showthread.php?t=1193479](http://ubuntuforums.org/showthread.php?t=1193479)

---

### Post by wojox on 2010-03-27
You could have a look here as well [URL="http://ubuntuforums.org/showthread.php?t=1193567"] Firefox optimization and troubleshooting thread
[/URL]

---

### Post by KaiDog on 2010-03-28
I looked through the links and none of the uninstall flash options worked. But I think I identified the problem.

Initially, I typed about:plugins into the address bar. I had Flash 10 and Flash 9 installed. I tried all the uninstall commands to remove flash that I could find.

After uninstalling flash, I looked at about:plugins again. Flash 10 was gone but flash 9 was still there. When I tried to purge flash using the command

```
sudo apt-get remove --purge flashplugin-nonfree
```

I get the result:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
```

So, I need to remove flash 9 and none of the commands work and I don't even see it installed in synaptic. Should I manually delete libflashplayer.so and then install flash 10?

---

### Post by lovinglinux on 2010-03-28
> **KaiDog said:**
> I looked through the links and none of the uninstall flash options worked. But I think I identified the problem.

Initially, I typed about:plugins into the address bar. I had Flash 10 and Flash 9 installed. I tried all the uninstall commands to remove flash that I could find.

After uninstalling flash, I looked at about:plugins again. Flash 10 was gone but flash 9 was still there. When I tried to purge flash using the command

```
sudo apt-get remove --purge flashplugin-nonfree
```

I get the result:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
```

So, I need to remove flash 9 and none of the commands work and I don't even see it installed in synaptic. Should I manually delete libflashplayer.so and then install flash 10?

Flash 9 is usually swfdec or gnash. See the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) as already suggested.

It could also be a version of flash 9 installed manually under ~/.mozilla folder. Deleting it should solve the problem, but I doubt this is the case.

BTW, have you restarted Firefox after removing the plugin?

---

### Post by KaiDog on 2010-03-29
I tried all the uninstalls of flash suggested in the Firefox Optimization thread. It didn't work, none of the uninstalls seemed to work. So just to see what would happen I deleted libflashplayer.so from the mozilla/plugins folder and the mozilla_backup/plugins folder and installed flash 10 via the Software Center.

After doing that the problem was resolved. I'm now able to view Hulu videos and play youtube with no problems. Thanks everyone for your help, I learned a lot. You can consider this problem solved.

---

