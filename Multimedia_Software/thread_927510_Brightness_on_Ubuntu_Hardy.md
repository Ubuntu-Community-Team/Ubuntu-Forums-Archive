---
title: "Brightness on Ubuntu Hardy"
date: 2008-09-23
forum: Multimedia Software
---

### Post by darkweaver87 on 2008-09-23
Hi everyone,

I have some troubles with my laptop LCD brightness.

During the boot and when the session starts the brightness level is at the minimum.

When I play a video the screen brightness level decreases too.

According to some reading on [http://forum.ubuntu-fr.org/viewtopic.php?id=213256](http://forum.ubuntu-fr.org/viewtopic.php?id=213256) I am not the only one.

People have the same trouble than me and didn't solve it. They have nvidia, intel or ati cards/chipsets. So I don't think it comes from the driver I use (I have an Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)).

I tried with XFCE so I don't think it comes from Gnome power manager too.

I am on Ubuntu Hardy 8.04 LTS.

I RTFW and I didn't found any solutions.

Thanks in advance for your reply.

---

### Post by swoody on 2008-09-23
Your screen just goes down to the lowest brightness setting? Or it's so low that you can barely see anything on the screen?

---

### Post by darkweaver87 on 2008-09-23
Thanks for your reply.

It goes down to the lowest settings.

Then I can up the brightness with the Fn + F6 combination key but it's very boring to do that every time the laptop starts.

---

### Post by swoody on 2008-09-23
That's very strange. I actually had the exact opposite problem, and I have the same Intel Graphics processor as you. My brigtness would start off at full-blast, and I'd have to keep turning it down at random times.

I just played around with the settings in the Gnome Power manager, and got it to work how I wanted it to. You may want to try going through all of those settings. I remember there were some pretty random ones I had to change in there. Look for anyhthing that mentions "Backlight" or "Brightness". It sounds like it's reverting back to your default brightness setting when it does this, so you may want to try changing your default brightness in the Gnome PM, and try that out. Post back on here after you try that, and let me know how it goes :) (fingers crossed)

---

### Post by swoody on 2008-09-23
> **darkweaver87 said:**
> I tried with XFCE so I don't think it comes from Gnome power manager too.

It's probably not a problem or issue with Gnome PM, but like I said, there are certain things that trigger a laptop screen to go to it's default setting for brightness, and it sounds like your default might be all the way dim. Try to see if you can change the settings for your default brightness in Gnome PM, and the post back here whether it works or not :)

---

### Post by darkweaver87 on 2008-09-24
Hi and thanks,

I tried some solutions from [http://forum.ubuntu-fr.org/viewtopic.php?id=213256](http://forum.ubuntu-fr.org/viewtopic.php?id=213256) which seems to work for some people but not for me.

To summarize I tried:
- ```

sudo gconf-editor
apps -> gnome-power-manager -> blacklight -> disable

```

- ```

apt-get install xbacklight
xbacklight -set 100

```

I wish I could try some other things but the problem appeared on my girlfriend's laptop and we will see each other not until this week-end :cry:

The more curious is it didn't do that after the installation of Ubuntu 8.04 LTS. It happened one week ago maybe after an update.:-k

Maybe I can install Ubuntu on my 8GB USB key in order to determine when and where the problem appears ?

---

### Post by darkweaver87 on 2008-09-28
Hi,

Finally and curiously I tried to remove all my .gconf* .gnome* .compiz* from my home directory and it worked ...

I am confused ... :confused:

---

### Post by swoody on 2008-10-11
That is very strange:confused: I didn't know why one of those config files would have done it, but hey! No complaints if it worked :D Any side effects from deleting them?

---

