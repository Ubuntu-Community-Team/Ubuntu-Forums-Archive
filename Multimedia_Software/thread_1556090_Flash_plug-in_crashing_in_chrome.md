---
title: "Flash plug-in crashing in chrome"
date: 2010-08-18
forum: Multimedia Software
---

### Post by beliyyal on 2010-08-18
Ok, been having this problem lately with the flashplayer in google chrome. It ALWAYS crashes, just about every time I try to watch a video. This is the message I get:
```
the following plugin has crashed: /opt/google/chrome/libflashplayer.so
```

I was wondering if someone knew of a way to remedy the problem?

---

### Post by lovinglinux on 2010-08-19
Try to disable Chrome built-in flash, which is the one you are using, and use the one from [Adobe](apt:flashplugin-nonfree) (repositories). Don't know how to disable it tho, since I don't use Chrome.

---

### Post by beliyyal on 2010-08-19
> **lovinglinux said:**
> Try to disable Chrome built-in flash, which is the one you are using, and use the one from [Adobe](apt:flashplugin-nonfree) (repositories). Don't know how to disable it tho, since I don't use Chrome.
:lolflag: me neither, unfortunately. I was looking in the options, couldn't find any option to disable or change flash players. I would just use firefox but I have all my logins and bookmarks in chrome....plus I've just grown used to it.

---

### Post by lovinglinux on 2010-08-19
> **beliyyal said:**
> :lolflag: me neither, unfortunately. I was looking in the options, couldn't find any option to disable or change flash players. I would just use firefox but I have all my logins and bookmarks in chrome....plus I've just grown used to it.

I have found some articles on [how-to]("http://itsalltech.com/2010/07/10/how-to-disable-google-chromes-built-in-flash-player-plugin/"). Not sure that is the correct way tho, since that would disable flash completely if done in Firefox.

Have you tried Firefox, at least to see if the problem is with Chrome built-in version of flash or Chrome itself?

In regard to your bookmarks and passwords, you could sync them with Xmarks.

[https://chrome.google.com/extensions/detail/ajpgkpeckebdhofmmjfgcjjiiejpodla](https://chrome.google.com/extensions/detail/ajpgkpeckebdhofmmjfgcjjiiejpodla)
[https://addons.mozilla.org/en-US/firefox/addon/2410/](https://addons.mozilla.org/en-US/firefox/addon/2410/)

---

### Post by LewisDre4m on 2010-08-20
Follow bellow post

---

### Post by LewisDre4m on 2010-08-20
FIXED! 

I followed the link above posted by "lovinglinux" and followed the instructions which said to . . .

*Type in chrome://plugins in the the Google Chrome address bar.

*Now you will see a list of plugins, click disable on the [COLOR=#000000][FONT=Times New Roman][FONT=Arial]**Shockwave Flash **[/FONT][/FONT][/COLOR]plugin. 

NOW please note,

When I then went to view Youtube (using flash) it said missing plug-in and when I went to download it from Adobe it said something about how my browser already has the latest Flash.

As this was a new version of Ubuntu I had not even yet installed the "restricted extras package" found in Ubuntu software center simply by typing restric... then it shows. After I did that I went to Youtube and it played.

Interestingly while writing this post I noticed I now have TWO [COLOR=#000000][FONT=Times New Roman][FONT=Arial]**Shockwave Flash **[/FONT][/FONT][/COLOR]plugins which are exactly the same, the ONLY difference is one is disabled (obviously) but the location path is [COLOR=#000000][FONT=Times New Roman][COLOR=#A0A0A0][FONT=Arial]/opt/google/chrome/libgcflashplayer.so[/FONT][/COLOR][/FONT][/COLOR] and the one that works which IS and should be enabled is [COLOR=#000000][FONT=Times New Roman][FONT=Arial]/usr/lib/flashplugin-installer/libflashplayer.so[/FONT][/FONT][/COLOR]

This has FIXED the problem, seems Chrome doesn't like running that plug-in from that location.

Thanks LewisDre4m

---

### Post by beliyyal on 2010-08-23
> **LewisDre4m said:**
> FIXED! 

I followed the link above posted by "lovinglinux" and followed the instructions which said to . . .

*Type in chrome://plugins in the the Google Chrome address bar.

*Now you will see a list of plugins, click disable on the [COLOR=#000000][FONT=Times New Roman][FONT=Arial]**Shockwave Flash **[/FONT][/FONT][/COLOR]plugin. 

NOW please note,

When I then went to view Youtube (using flash) it said missing plug-in and when I went to download it from Adobe it said something about how my browser already has the latest Flash.

As this was a new version of Ubuntu I had not even yet installed the "restricted extras package" found in Ubuntu software center simply by typing restric... then it shows. After I did that I went to Youtube and it played.

Interestingly while writing this post I noticed I now have TWO [COLOR=#000000][FONT=Times New Roman][FONT=Arial]**Shockwave Flash **[/FONT][/FONT][/COLOR]plugins which are exactly the same, the ONLY difference is one is disabled (obviously) but the location path is [COLOR=#000000][FONT=Times New Roman][COLOR=#A0A0A0][FONT=Arial]/opt/google/chrome/libgcflashplayer.so[/FONT][/COLOR][/FONT][/COLOR] and the one that works which IS and should be enabled is [COLOR=#000000][FONT=Times New Roman][FONT=Arial]/usr/lib/flashplugin-installer/libflashplayer.so[/FONT][/FONT][/COLOR]

This has FIXED the problem, seems Chrome doesn't like running that plug-in from that location.

Thanks LewisDre4m
I did this, works for me. Thanks dude, you are f*cking awesome. Props.

---

### Post by beliyyal on 2010-08-30
> **beliyyal said:**
> I did this, works for me. Thanks dude, you are f*cking awesome. Props.

Actually, turns out it didn't really work. I mean yeah, it doesn't crash *as* much as it used to, but it still crashes from time to time. So....still looking for a true fix.

---

