---
title: "Firfox 3.0.10 won't play youtube."
date: 2009-11-10
forum: Multimedia Software
---

### Post by deewanagan on 2009-11-10
hello everybody,

i have problem with youtube video, it doesn't play. it used to play but suddenly it stopped playing. i can play videos at other sites, but only youtube can't play. i searched around but couldn't find anything related.
i am using ubuntu 8.10.

tanx

---

### Post by wilee-nilee on 2009-11-10
> **deewanagan said:**
> hello everybody,

i have problem with youtube video, it doesn't play. it used to play but suddenly it stopped playing. i can play videos at other sites, but only youtube can't play. i searched around but couldn't find anything related.
i am using ubuntu 8.10.

tanx

Do you know what flash you have installed.

---

### Post by deewanagan on 2009-11-10
hi,
its version 10

---

### Post by masux594 on 2009-11-10
have a look to about:plugins of your browser.. copy the lines of flash plugin..

Sysc, A

---

### Post by powertower on 2009-11-10
Have you tried to Windows approach? 

sudo apt-get remove adobe-flashplugin

then download flash again and install it.

Uninstalling and reinstalling fixes many of my issues. Firefox plugins are stored in:

/usr/lib/mozilla/plugins

---

### Post by deewanagan on 2009-11-10
> **masux594 said:**
> have a look to about:plugins of your browser.. copy the lines of flash plugin..

Sysc, A

for some strange reason, there is no flas plugin line in "about: plugins", don't know why?! and yes i have tried removing and reinstalling.

---

### Post by masux594 on 2009-11-10
No "Shockwave Flash" entry?

Sysc, A

---

### Post by deewanagan on 2009-11-10
don't know but it wasn't there, then after a reboot it came and is enabled.:confused: still not working. the version is 10.0.

---

### Post by masux594 on 2009-11-10
Post the lines after the "Shockwave Flash" entry..

Sysc, A

---

### Post by deewanagan on 2009-11-10
the lines are as follow:```
    
File name: libflashplayer.so
Shockwave Flash 10.0 r32
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

---

### Post by masux594 on 2009-11-10
Oki.. Run this command..
```
sudo apt-get remove flashplugin-installer && sudo apt-get install flashplugin-nonfree
```.. restart firefox and after check youtube if it works.. ..

Sysc, A

---

### Post by maddojf on 2009-11-10
I was having the same problem and that fixed it for me.  Thanks.

---

### Post by deewanagan on 2009-11-11
hi,

it didn't worked that way,cause i don't have the "flashplugin-installer" installed, and i have the "flashplugin-nonfree" installed but it works now, the problem is the flashblock add-on. now that i have disabled it, the videos play. I don't know the reason, but i have been using the flashblock add on for along time, it worked before and it still works on other sites::confused::

tanx

---

### Post by yus253 on 2009-11-11
Why not change Firefox 3.5

---

### Post by deewanagan on 2009-11-11
> **deewanagan said:**
> hi,

it didn't worked that way,cause i don't have the "flashplugin-installer" installed, and i have the "flashplugin-nonfree" installed but it works now, the problem is the flashblock add-on. now that i have disabled it, the videos play. I don't know the reason, but i have been using the flashblock add on for along time, it worked before and it still works on other sites::confused::

tanx

i just read that its a bug, ff3 with flashblock version 1.5.11.2, it won't play youtube vidoes. They say its a bug from LINUX!! [https://addons.mozilla.org/en-US/firefox/addon/433]("https://addons.mozilla.org/en-US/firefox/addon/433")
it will work if the website is whitelisted though.

tanx

---

