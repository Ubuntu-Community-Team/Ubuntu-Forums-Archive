---
title: "Switching between latop LCD and external monitor (no extended desktop)"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by tibbe on 2006-08-21
My scenario:
- Latop with 1024x768 LCD on a ATI Radeon Mobility 7500
- Work monitor, TFT @ 1280x1024

I want to be able to switch between the two (i.e. I don't want to extend my desktop). I tried a bazillion or so guides and none of them manages to get my work monitor into a resolution above 1024x768. Any ideas?

---

### Post by Ziox on 2006-08-21
> **tibbe said:**
> My scenario:
- Latop with 1024x768 LCD on a ATI Radeon Mobility 7500
- Work monitor, TFT @ 1280x1024

I want to be able to switch between the two (i.e. I don't want to extend my desktop). I tried a bazillion or so guides and none of them manages to get my work monitor into a resolution above 1024x768. Any ideas?

first of all, are you sure that the TFT can go higher than 1280x1024? (Say in Windows :evil: )

if in windows it can go higher then you should try editing the xorg.conf file to have multiple serverlayouts. whenever you boot into ubuntu, you can specify which monitor to use. The process is easy to add another server layout, but if you need instructions, I will gladly help.

However, if you are talking about switching monitor on the fly (w/out killing X), I don't think that is possible with current Xorg...:confused:

---

### Post by snowblind on 2006-08-29
Hi Ziox,

I would appreciate an how to on this. I have multiple ServerLayout running at the moment but I have to run the startx command from shell. So really I'd like to be bale to select which server layout on boot.

Thanks

---

### Post by squeaks on 2006-08-29
I too need to know how to select between multiple serverlayouts.

What I did, was rename /etc/rc2.d/S13gdm no KS13gdm so that gdm does not start at the default runlevel.

Then I do startx -- -layout Multihead and the screen goes black, then I get some log output from X.

Finally, I did telinit 3, (to make the /etc/rc3.d/S13gdm script run).

At that point I got the normal gdm login screen and both monitors displaying.

I'm pretty sure this is FAR from idea. I'd appreciate suggestions... 

I was going to make my own post, but this one is just what I need.

Thanks,
Squeaks

---

### Post by squeaks on 2006-09-04
I found that it was because ubuntuguide.org advised me to make the last line in ~/.xinitrc to execute my xmodmap. I had no .xinitrc so i made one with just that last line, and apparently that does not tell X to stay started.

---

