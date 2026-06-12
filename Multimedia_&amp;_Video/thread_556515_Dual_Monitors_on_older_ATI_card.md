---
title: "Dual Monitors on older ATI card?"
date: 2007-09-21
forum: Multimedia &amp; Video
---

### Post by ElEdwards on 2007-09-21
I have an older ATI-1000 dual vga card.  I never had problems in XP with two independent displays but when I became a Ubuntu user, I could have only two duplicate displays, not two independent displays.

I then went to openSuse and YAY! I had two independent displays with a few button clicks.... but I don't like openSuse.... for me, it isn't as user-friendly as Ubuntu, so I'm coming back.  I'll install Ubuntu this weekend and get rid of openSuse.

Since I now know that independent dual monitors are possible with my older ATI card in Linux (openSuse had no issue), what must I do to have this capability in Ubuntu?

FYI, I know for a fact (read: crashes) that the newer ATI drivers in Envy don't work my older card..... and yes, I know I could get a newer card but if it works in one distro, then there must be a way to get it to work in another.

Thanks! :)

---

### Post by w4ett on 2007-09-21
Here's an answer from Launchpad using the 9200 card (using the open source drivers same as yours)

[https://answers.launchpad.net/ubuntu/+question/7031](https://answers.launchpad.net/ubuntu/+question/7031)

Gutsy has a GUI configurator to set this up, so in 3 weeks you'll be all set.

---

### Post by airtonix on 2007-09-24
the gui does not work, always borks the xorg and never detects the cards or the monitors....

---

### Post by smurfit on 2007-09-30
I have this same problem.

I had dual monitors working great until I updated to Gutsy, I used the same xorg.conf as was working pre upgrade & I  have also tried a standard xorg.conf.

I have a 7000 dual head card too.

The second monitor just switches to standby when x starts.

Also, the display is soooo slow, no where near the performance that was there.

---

### Post by w4ett on 2007-09-30
> **smurfit said:**
> I have this same problem.

I had dual monitors working great until I updated to Gutsy, I used the same xorg.conf as was working pre upgrade & I  have also tried a standard xorg.conf.

I have a 7000 dual head card too.

The second monitor just switches to standby when x starts.

Also, the display is soooo slow, no where near the performance that was there.

Have you tried using the Screens and Graphics application under System.Administration?  You also have to remember that Gutsy is still Beta, and won't be fully "Stable" until the final release.

All hardware configurations are different, and the Beta Xorg modifies your .conf differently than what you are familiar with in Feisty (xorg now writes modelines automatically, and is MUCH better at reading the EDID data from the monitor).

I am running a 9200 card on my Gutsy install, and have found the opposite to be true...my GFX are more stable than in Feisty,....BUT you mileage will vary due to the fact that Gutsy is still unfinished.  Case in point I had 70+ updates both yesterday and today, and BOTH  included updates to Xorg and video drivers.

---

### Post by smurfit on 2007-09-30
I'm sure that when its at release stage it will be great, I am already impressed & love the changes I can see.

I was a bit disappointed when I lost dual monitor, its was extremely useful. My display is running very slow but as you say should improve as updates are released.

I was hoping a quick tweak to my .conf would sort it.

---

