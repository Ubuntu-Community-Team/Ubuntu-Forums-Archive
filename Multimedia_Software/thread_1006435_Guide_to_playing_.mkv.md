---
title: "Guide to playing .mkv"
date: 2008-12-09
forum: Multimedia Software
---

### Post by came2die on 2008-12-09
Ok, this will sound a little bossy, but please have in mind that I really want to get a solution...

Can some very helpful and friendly person help me solve those problems
(because they are driving me nuts and I am even thinking of buying an external device for that)... I believe you would also contribute to the community a lot :)

1. How to make my not so weak(quad core, 2GM ram, 512..) machine to play smoothly HDrips(.mkv). I've already read some stuff about that, but it doesn't help much. Or at least give me info what other solutions do I have or why thats not possible :)

2. Help to solve some silly DVD playing problem - some stupid anomaly is showing up when slight movement occurs in the middle of  the screen(for an instance: moving of a hand)

3. I will be really, really, very grateful :)

---

### Post by piratebill on 2008-12-09
do you have all the latest gstreamer plugins installed?

---

### Post by cb951303 on 2008-12-09
get the latest SMplayer from here [https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)
i never had a problem with it

---

### Post by came2die on 2008-12-09
I've had the gstreamer plugins installed, but I uninstalled them when I installed Smplayer and its dependencies :)

It is A LOT better but some problems still occur :)

1. That silly line in the middle of the screen(more visible in fullscreen)

2. At some point sound starts lagging(I've tested it in the Matrix revolutions-ONLY 720p!, last fight. What surprises me is that it laggs only in some particular moments, and not where that would seem logical(too much work for cpu).

3. I would like to remove all packets that I don't need anymore. I can remove all media related packets which are not those which are needed by Smplayer?

---

### Post by cb951303 on 2008-12-09
> **came2die said:**
> I've had the gstreamer plugins installed, but I uninstalled them when I installed Smplayer and its dependencies :)

It is A LOT better but some problems still occur :)

1. That silly line in the middle of the screen(more visible in fullscreen)

2. At some point sound starts lagging(I've tested it in the Matrix revolutions-ONLY 720p!, last fight. What surprises me is that it laggs only in some particular moments, and not where that would seem logical(too much work for cpu).

3. I would like to remove all packets that I don't need anymore. I can remove all media related packets which are not those which are needed by Smplayer?

you might try changing video driver for getting rid of the line. default is "xv" but I use "gl". it's in smplayer preferences

---

### Post by came2die on 2008-12-10
The line appears no more, but video is still laggy :)

Any ideas how to solve this? This is only 720p...

---

### Post by cb951303 on 2008-12-10
> **came2die said:**
> The line appears no more, but video is still laggy :)

Any ideas how to solve this? This is only 720p...

what is your graphics card?

---

### Post by came2die on 2008-12-10
pny geforce 8800 GT 512MB

---

### Post by cb951303 on 2008-12-10
> **came2die said:**
> pny geforce 8800 GT 512MB
do you use nvidia driver 177? what's your ubuntu version?

---

### Post by came2die on 2008-12-10
No, I've installed drivers via Envy(latest driver is 173.14.12), how do I check which version I have?
8.04 hardy

---

### Post by came2die on 2008-12-10
Thank you so far!

So, I've installed 177. Both 720p and 1080p are working fine atm !

Any ideas how to get real HD's working(picture seems fine to me, but audio is totally screwed up ) Can someone just get me some info about it 

Thank you again, for your help :p

---

