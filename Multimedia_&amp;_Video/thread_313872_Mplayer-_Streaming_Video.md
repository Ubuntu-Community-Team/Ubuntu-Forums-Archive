---
title: "Mplayer- Streaming Video"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by CheeseQueen452 on 2006-12-06
I'm trying to play a streaming video that is in .mov format, using Mplayer. However, I keep getting an error message that says something like "couldn't resolve name for AF_INET6". I've also been getting an error that it couldn't initialize the video out device. I've tried different codec settings, but haven't yet found the right "combination". How do I fix this? HELP!!

---

### Post by CheeseQueen452 on 2006-12-06
Anyone?

---

### Post by shin on 2006-12-06
I dont think this is codec or mplayer related. AF_INET6 corresponds to ipv6 protocol. Maybe it is just issue with this one site?

Anyway this is what you may try. Using firefox? Check if it is disabled (or enabled) there  (go to about:config and check value of network.dns.disableIPv6). And try switching it (on or off). Also check /etc/modprobe.d/aliases if alias net-pf-10 ipv6 is commented. If not - comment it. If it is commented - try uncommenting. Reboot after those changes.

---

### Post by CheeseQueen452 on 2006-12-06
I went to about:config & enabled that setting(it was disabled), but it didn't work. I'll try your other suggestion tomorrow.

> **shin said:**
> I dont think this is codec or mplayer related. AF_INET6 corresponds to ipv6 protocol. Maybe it is just issue with this one site?

Anyway this is what you may try. Using firefox? Check if it is disabled (or enabled) there  (go to about:config and check value of network.dns.disableIPv6). And try switching it (on or off). Also check /etc/modprobe.d/aliases if alias net-pf-10 ipv6 is commented. If not - comment it. If it is commented - try uncommenting. Reboot after those changes.

---

### Post by CheeseQueen452 on 2006-12-07
Alias net-pf-10 ipv6 is listed there, what do I do? Do I just remove that line? Sorry, I don't know what you mean by comment/uncomment.

BTW, network.dns.disableIPv6 was in fact enabled by default, & I disabled it. I somehow confused "disable" & true/false :oops:

> **shin said:**
> Also check /etc/modprobe.d/aliases if alias net-pf-10 ipv6 is commented. If not - comment it. If it is commented - try uncommenting. Reboot after those changes.

---

### Post by carlal on 2006-12-11
you should edit your mplayer config file (/home/*yourlogin*/.mplayer/config) and add this at the end : 

**prefer-ipv4 = yes**

that worked for me.

---

### Post by CheeseQueen452 on 2006-12-11
Thanx, I'll try that tomorrow. Don't have time right now....

> **carlal said:**
> you should edit your mplayer config file (/home/*yourlogin*/.mplayer/config) and add this at the end : 

**prefer-ipv4 = yes**

that worked for me.

---

### Post by logos34 on 2006-12-12
i'm getting those annoying AF_INET6 popups too.  Once I click on them the content plays (sometimes).  But it usually ends up freezing and/or crashing.  

Neither of the above suggestions worked for me.  Any others?

I just did a fresh install -- compiled from sources as recommended at Mplayerhq -- and still the same old problems.

---

### Post by CheeseQueen452 on 2006-12-12
Ok, I tried this & although I don't see the error message, the videos in question are extremely choppy. One of the videos I'm trying to view is at [http://firefoxflicks.com/flick/?id=21122](http://firefoxflicks.com/flick/?id=21122) Is there some way to make it work better?

Keep in mind I'm using the MediaplayerConnectivity extension to launch the videos in the chosen player, instead of in the browser. Even though I've installed different codecs, certain streaming audio/video content just doesn't play within Firefox. That's why I'm using the extension.

> **carlal said:**
> you should edit your mplayer config file (/home/*yourlogin*/.mplayer/config) and add this at the end : 

**prefer-ipv4 = yes**

that worked for me.

---

### Post by CheeseQueen452 on 2006-12-26
Can anyone help me with this?

The videos in question are in .mov format, & extremely choppy when I attempt to play them. One of the videos I'm trying to view is at [http://firefoxflicks.com/flick/?id=21122](http://firefoxflicks.com/flick/?id=21122)
Is there some way to make it play smoothly? I've tried changing the codecs & audio/video settings, but nothing seems to work.

---

### Post by ugm6hr on 2007-12-29
I know this is an old thread, but I'm getting these MPlayer popups with Quicktime movies (played via mediaplayer connectivity Firefox plugin) in Gutsy.

Totem works OK, but the audio volume is always too quiet compared to MPlayer / VLC.  VLC displays incorrect colour bands across the top of the video.

The ipv4 edit in Mplayer config file removes the error popup, but it also stops the video from playing!

---

