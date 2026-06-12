---
title: "shockwave player"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by satimis on 2008-04-17
Hi folks,


Where can I find shockwave player for 64bit Ubuntu 7.04?  TIA


B.R.
satimis

---

### Post by tamoneya on 2008-04-18
i am pretty sure that there is no shockwave player for linux.  This included 32 and 64 bit systems.

---

### Post by satimis on 2008-04-18
> **tamoneya said:**
> i am pretty sure that there is no shockwave player for linux.  This included 32 and 64 bit systems.
Thanks for your advice.


I have been googling around without discovery.


$ apt-cache search mplayerplug-in```

mozilla-mplayer - MPlayer-Plugin for Mozilla

```


I tried to install it in anticipation it can help.  But the installation failed;


$ sudo apt-get install mozilla-mplayer```

Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-mplayer: Depends: mplayer (>= 1.0~pre5)
E: Broken packages

```


Reading;
MPlayer-Plugin for Mozilla
[http://packages.ubuntu.com/feisty/mozilla-mplayer](http://packages.ubuntu.com/feisty/mozilla-mplayer)


Then I found;
The Ultimate Movie Player For Linux
[http://packages.ubuntu.com/feisty/mplayer](http://packages.ubuntu.com/feisty/mplayer)


I already uncomment```

deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```


I can't figure out how to fix the problem.  Any advice?  TIA


B.R.
satimis

---

### Post by cor2y on 2008-04-18
there is no shockwave player for linux because adobe never created one and its proprietary.
your best bet if you really do need shockwave playback for gaming or to view some media online or locally is to install shockwave either via the wine browser (while not difficult has too many steps for newbie users) or use ie4linux which is just a friendlier way of using wine with ie.
```
http://www.tatanka.com.br/ies4linux/page/Main_Page
```Then simply install the media plugin by visiting the relevant adobe page.

---

### Post by satimis on 2008-04-20
> **cor2y said:**
> Then simply install the media plugin by visiting the relevant adobe page.
Thanks for your advice.


I only need Shockwave Player visiting some websites on Internet.  Adobe has media plugin on 32bit only.  But I'm running 64bit browser.


B.R.
satimis

---

### Post by willtell on 2008-04-23
Is this a shockwave player, or something else.  This came installed on Gutsy so I have no idea where to get it, but about:plugins in firefox brought this up.  Hope it helps.    

File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by satimis on 2008-04-23
> **willtell said:**
> Is this a shockwave player, or something else.  This came installed on Gutsy so I have no idea where to get it, but about:plugins in firefox brought this up.  Hope it helps.    

File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Hi willtell,


I don't know.  I already have this file.

$ sudo find / -name npwrapper.libflashplayer.so```

Password:
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so

```
However on visiting some websites they still request me to download Shockwave Player


satimis

---

### Post by cor2y on 2008-04-24
The flash media plugin and the shockwave media player are two different things.
Even back in windows you have to download two different apps.
Shockwave has yet to make it to linux, although it is available for the mac.

---

### Post by satimis on 2008-04-24
> **cor2y said:**
> The flash media plugin and the shockwave media player are two different things.
Even back in windows you have to download two different apps.
Shockwave has yet to make it to linux, although it is available for the mac.
Noted with thanks


satimis

---

