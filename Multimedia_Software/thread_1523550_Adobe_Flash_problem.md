---
title: "Adobe Flash problem"
date: 2010-07-03
forum: Multimedia Software
---

### Post by Legion81 on 2010-07-03
I just installed 10.04 on an old computer (900 MHz AMD Athlon) and flash is acting weird. When I go to Youtube or any other page with flash, I get audio just fine but the video freezes on the first image and my processor load shoots up to 100%. I've installed and re-installed libflashplayer.so in the /.mozilla/plugins folder and even tried it with Google Chrome. I still can't get any videos to play (just the audio and the first image).

Some details:

lspci
00:0d.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (rev 5c)

glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

[LEFT]about:plugins
File:  libflashplayer.soVersion:Shockwave Flash 10.1 r53[/LEFT]

Any ideas why this might be freezing? I tried the internet connection with another computer running ubuntu and it worked perfect so it has to be something from this installation. Any help will be much 
appreciated.

Thanks in advance.

---

### Post by bcfieldi on 2010-07-04
I'm having similar problems with flash. I have 32bit lucid and flash 10.1 I've done a search on the forum and found the adobe tools that uninstalls flash and installs latest version of AIR and flash but still seem to be getting the same problems. 

I can play youtube videos and certain flash works fine, but some flash like pandora and some ads as well as the adobe settings panel are not visible. 

I get this error within chromes javascript console. 
```
Unsafe JavaScript attempt to access frame with URL http://www.pandora.com/ from frame with URL http://www.facebook.com/extern/login_status.php?api_key=ca44798cf7067942a82579c2c720f7dd&extern=2&channel=http%3A%2F%2Fwww.pandora.com%2Ffacebook%2Fxd_receiver.htm&locale=en_US. Domains, protocols and ports must match.
```

and a Failed to load resource, when attempting to access the settings panel. 

Any ideas?

---

### Post by Crypto90 on 2010-07-04
I have this problem too.

lspci
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]

glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

Shockwave Flash 10.1 r53

I try this AIR no change.I use Mozilla 3.6.6,Chrome but still cant watch video on youtube and other sites.I use Ubuntu 10.04 32bit

---

### Post by Yellow Pasque on 2010-07-04
Linux Flash video is CPU-intensive and old systems will struggle to keep up. Using an older version may help, but will be more of a security risk).

---

### Post by redb on 2010-07-04
I found a grease monkey script worked great for me. 

Script Summary:
Watch YouTube with embedded player such as Totem, Mplayer or VLC (now Flash is not needed) 

[http://userscripts.org/scripts/show/55619](http://userscripts.org/scripts/show/55619)


Hope it works for you,

Cheers

---

### Post by Crypto90 on 2010-07-04
For me work! Thx man :)

---

### Post by lovinglinux on 2010-07-04
> **redb said:**
> I found a grease monkey script worked great for me. 

Script Summary:
Watch YouTube with embedded player such as Totem, Mplayer or VLC (now Flash is not needed) 

[http://userscripts.org/scripts/show/55619](http://userscripts.org/scripts/show/55619)


Hope it works for you,

Cheers

I develop an extension that does that and support YouTube, Vimeo and Blip.tv. More sites will be supported on the next version, which will be released soon.

[http://flvideoreplacer-extension.blogspot.com](http://flvideoreplacer-extension.blogspot.com)
[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

---

### Post by Legion81 on 2010-07-04
> **Temüjin said:**
> Linux Flash video is CPU-intensive and old systems will struggle to keep up. Using an older version may help, but will be more of a security risk).

Are you suggesting to use an older version of Linux or an older version of flash? To be able to watch most videos, don't you need at least flash 9?

---

