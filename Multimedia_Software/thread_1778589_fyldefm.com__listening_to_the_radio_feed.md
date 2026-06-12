---
title: "fyldefm.com / listening to the radio feed"
date: 2011-06-09
forum: Multimedia Software
---

### Post by geidorei on 2011-06-09
Hi - trying to help some friends over at fyldefm.com - however, in linux (Ubuntu) when loading the site the radio station does not play, aok on Windows and Apple.

Says is needs a plugin - tried Chromium, Firefox and Epiphany.

Any help greatly appreciated - need to put info on site for linux users so they can listed to the station.

Says it needs a plugin but doesnt find anything - text/html decoder

Karl

---

### Post by howefield on 2011-06-09
Try VLC > Open Network Stream > and use the following in the URL path

```
http://174.142.192.209/castcontrol/playlist.php?id=174@type=ram
```

Watch out for the forum software truncating some of the above link. (sorted)

---

### Post by howefield on 2011-06-09
The only quick link button on the "Listen Live" that doesn't work for me is the Windows Media Player one, the others pop up an open/save box and all play in the player of choice.

---

### Post by geidorei on 2011-06-09
ahah - me being thick lol yes they do work, however anyway to get rid of the browsers asking for that plugin????

---

### Post by howefield on 2011-06-09
I'd guess that is because the page starts streaming the default choice playing which is the only one that doesn't seem to work.

Suppose you could identify the operating system before it starts playing and serve the most relevant option or not play at all until the visitor to the site decides they want it to play (which may be more usual) ?

---

### Post by andrew.46 on 2011-06-09
There is a vlc Streaming Radio Player extension that would suit you I believe. I attach a screenshot showing it in action with vlc + goom and the radio station you have mentioned, the menu allows for multiple radio stations and is easy enough to setup. Some discussion here:

if you use VLC and like classical music... or just radio
[http://ubuntuforums.org/showthread.php?t=1774325](http://ubuntuforums.org/showthread.php?t=1774325)

---

### Post by geidorei on 2011-06-10
many thanks for into - will get this sorted over weekend.

---

