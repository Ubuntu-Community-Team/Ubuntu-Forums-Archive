---
title: "Flash installed successfully, plugin crashing on use"
date: 2012-05-06
forum: Multimedia Software
---

### Post by MrBucket101 on 2012-05-06
[http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html](http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html)

According to that page I've successfully installed flash 11.2.202.235, I'm running Linux 3.2.0-24-generic (64-bit) and my browser of choice is google chrome-beta.

When I first installed chrome, flash wasn't working. So i purged flashplugin-installer and went to manually install flash. I downloaded the tar.gz and copied the contents of the /usr/ folder into my own, and then I created the directory /opt/google/chrome/plugins and placed libflashplayer.so inside the folder.

I checked the plugins settings inside chrome and only one flashplayer is installed, the one manually by me. I then followed up with the version check website and didn't see any problems.

I tried to play a flash video and the flash plugin crashed.

I did some more research and came across an addon for firefox called flash-aid. I removed the files copied over manually by me, and then installed firefox, ran the flashaid wizard and installed the beta version of adobe flash. When i first ran the addon/script it err'd with a directory doesn't exist /usr/lib/mozilla/plugins/ message, so I created the directory, reran the addon with success. 

at this point I rechecked the adobe flash version checker, and it listed the installed version in firefox as 11.2.202.233.

I then went to a website with flash on it and the flash plugin again crashed.

I then did echo "OverrideGPUValidation=true" >~/mms.cfg and still nothing worked

So basically I've installed flash 3 different ways, attempted to use 2 different browsers, and viewed different flash content. All the while, the plugin repeatedly crashes on just about everything.

I've exhausted my options googling around looking for various solutions, and so I'm hoping someone here can provide a viable solution

Thanks in advance

---

