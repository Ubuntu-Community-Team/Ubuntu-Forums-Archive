---
title: "Youtube Video Downloader"
date: 2009-08-27
forum: Multimedia Software
---

### Post by kanagaraj.rk on 2009-08-27
Hi friends I want the APT line for any youtube Downloader, Wine doors for ubuntu9.04 becas i hve to add in my sources.list file so that i can access it from my Synaptic package manager. pls reply me to my mail its very urgent.

[email]kanagaraj.rk@gmail.com[/email]

---

### Post by scragar on 2009-08-27
Ignore. See post below.

---

### Post by Penguin Guy on 2009-08-27
> **scragar said:**
> ```
sudo -i;
wget http://bitbucket.org/rg3/youtube-dl/raw/d941fe3d2cde/youtube-dl
chmod a+rx youtube-dl
chown root:root youtube-dl
mv youtube-dl /usr/bin/youtube-dl
exit
```
Run those one after the other. It will download and install youtube-dl for you. Use it like so:
```
youtube-dl http://www.youtube.com/watch?v=RfV--Av5otg
```
(youtube link was the first one on the recently watched list).
Alternatively you can simply click [[COLOR="Blue"]here[/COLOR]]("apt:youtube-dl") or run [COLOR="Green"]sudo apt-get install youtube-dl[/COLOR]. Anyway, I would use a firefox extension like '[[COLOR="Blue"]Embedded Objects[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/5258")' instead.

---

### Post by scragar on 2009-08-27
> **Penguin Guy said:**
> Alternatively you can simply click [[COLOR="Blue"]here[/COLOR]]("apt:youtube-dl") or run [COLOR="Green"]sudo apt-get install youtube-dl[/COLOR]. Anyway, I would use a firefox extension like '[[COLOR="Blue"]Embedded Objects[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/5258")' instead.

I didn't realise it was added to the ubuntu repo's. So sorry.

---

### Post by elkhelper on 2009-08-27
[SIZE=4]*[FONT=Comic Sans MS]I too am having problems. I have tried all of the fixes suggested here to no avail. Help please.[/FONT]*[/SIZE] :confused:

---

### Post by Simian Man on 2009-08-27
There is also clive.

---

### Post by itisbasi on 2009-08-27
Why not go to the /tmp folder and copy the video after it buffers? Why is an add on required?

---

