---
title: "Watching amazon instant videos"
date: 2013-02-28
forum: Multimedia Software
---

### Post by oakhilltop on 2013-02-28
I am not able to search, so apologize if this has been discussed.

I am running 12.10 and have the latest updates. I tried to rent a video from amazon's instant video. I got an error about the flashplayer not being up to date.

Is it possible to watch amazon instant videos on ubuntu? 

It would be kind of funny if we can't, since ubuntu made that deal with amazon.

---

### Post by fooman on 2013-02-28
hi,  you will need to install *hal*,  search for it in the software center,  or open a terminal and run:

```
sudo apt-get install hal
```

---

### Post by oakhilltop on 2013-02-28
That worked. Thanks very much.

---

### Post by sbrenneis on 2013-04-11
I am having the same problem, but I already have HAL installed. I found a note that says that the latest version of flash for chrome has the DRM removed, so they won't play on chrome at all. Some forums have mentioned something about pepper, but I don't have that in my chrome plugins.

It was working on firefox, but suddenly quit after the last update. I have tried removing and reinstalling the plugin, but that didn't help.

Any help would be appreciated.

---

### Post by sbrenneis on 2013-04-11
Never mind. I see what the problem is. Adobe is not going to support anything past version 11.2 for Linux. I downloaded firefox for windows under wine and it works fine. The flash version there is 11.7.

Once again, Linux users get the shaft.

---

### Post by ajlewis2 on 2013-04-13
I reverted back to the earlier version of flash, putting it in my home directory. 
[http://ubuntuforums.org/showthread.php?t=2134997&highlight=amazon+flash](http://ubuntuforums.org/showthread.php?t=2134997&highlight=amazon+flash)

---

### Post by treacl on 2013-04-13
It was working just fine for me until yesterday, when it stopped working. Coincidentally, I updated Firefox to version 20.0 yesterday, so I thought that was the problem. But perhaps it was instead related to the update to Flash 11.7 that happened within the past few days: [http://helpx.adobe.com/en/flash-player/release-note/fp_117_air_37_release_notes.html](http://helpx.adobe.com/en/flash-player/release-note/fp_117_air_37_release_notes.html). Is anyone still watching successfully with Flash 11.2?

---

### Post by treacl on 2013-04-13
Just tried to install Firefox and Flash via Wine. Firefox okay, but Flash installer crashes every time. So I guess I will quit Amazon Prime now! Streaming video was the only reason I signed up for it.

---

### Post by monkeybrain2012 on 2013-04-13
Instead of doing WINE, why not try Chrome if flash version is the problem?

---

### Post by treacl on 2013-04-13
Well, I don't do Chrome because I don't do Google. (Like I don't do Windows, which is why I use Ubuntu.) But in any case, note that Amazon video no longer works on the latest Linux version of Chrome: [http://www.amazon.com/gp/help/customer/display.html?nodeId=3757](http://www.amazon.com/gp/help/customer/display.html?nodeId=3757).

---

### Post by monkeybrain2012 on 2013-04-13
> **treacl said:**
> Well, I don't do Chrome because I don't do Google. (Like I don't do Windows, which is why I use Ubuntu.) But in any case, note that Amazon video no longer works on the latest Linux version of Chrome: [http://www.amazon.com/gp/help/customer/display.html?nodeId=3757](http://www.amazon.com/gp/help/customer/display.html?nodeId=3757).

Interesting. Don't do google and don't do Windows(neither do I) but do DRM :P

---

### Post by treacl on 2013-04-14
> **monkeybrain2012 said:**
> Interesting. Don't do google and don't do Windows(neither do I) but do DRM :P

LOL. I thought of that myself after posting. What would life be like if we were all perfectly consistent all the time?

BTW I did finally get Flash installed in Wine: [http://ubuntuforums.org/showthread.php?t=2135376](http://ubuntuforums.org/showthread.php?t=2135376)

---

### Post by 10101011 on 2013-04-14
I had to manually roll back my flash version to get Amazon Prime streaming working.

I went [here]("http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#main_Archived_versions") and got version [11.2.202]("http://download.macromedia.com/pub/flashplayer/installers/archive/fp_11.2.202.275_archive.zip").

[This]("http://askubuntu.com/questions/11/how-do-i-install-adobe-flash-player/184031#184031") post explains how to manually downgrade.

For me, the Adobe directory is /usr/lib/adobe-flashplugin/, so after extracting, I did the following:

sudo cp libflashplayer.so /usr/lib/adobe-flashplugin/libflashplayer.so

sudo cp -r usr/* /usr

[restart firefox]

---

### Post by ajlewis2 on 2013-04-24
At some point Amazon must have fixed the problem. There have been no more upgrades of flash, but the version 11.2.202.280 of the plugin now updates at Amazon and works. I got word that it was now working from an Amazon help forum.

---

