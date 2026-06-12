---
title: "Kubuntu, nvidia drivers, refresh rate and Beryl"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by raymacey on 2007-04-15
I've had a hell of a time trying to get my resolution and refresh rate set properly in KDE.  I tried manually altering my xorg.conf in a thousand different ways, and none of them worked.  I kept finding myself stuck with 65Hz refresh rates.  Eventually, I discovered that setting the specific monitor I'm using in the Monitor and Display section of the KDE system settings did the trick.  That allowed me to get my refresh rates correct.  

The problem is, it would only do it with the nv drivers.  When I changed to the proprietary nvidia drivers, X would load at all.  (I'm using an FX5200) I had to edit xorg.conf back to using the nv drivers.  Eventually I discovered a way around this problem.  I had to remove nvidia-glx and use nvidia-glx-new instead.  That let me get X working.  The problem is, it broke my ability to set my refresh and resolution via KDE's built in system settings.  For some reason, my refresh rate was forced back to 65Hz, and wouldn't go much higher.

Enter nvidia-settings.  This did the trick.  It let me set my refresh rate and resolution just fine.  The problem is, it doesn't stick between sessions.  So I have to reload and tweak the damned thing each time.  

This is a fresh install of Feisty on a box that was previously running Edgy, and for some reason Beryl won't work on the Feisty setup either in spite of running just fine on Edgy and Dapper.  It simply won't load the window controls around each window. I'm willing to leave the Beryl issue for another thread though if it's not related to the refresh/resolution issue.

So can anybody help me?  How do I get the refresh rate to stick?  And why won't the KDE GUI interface work with the proprietary drivers?  It's got me bashing my head against a wall, because it all worked just fine under Dapper and Edgy...

---

### Post by tseliot on 2007-04-15
> **raymacey said:**
> Enter nvidia-settings.  This did the trick.  It let me set my refresh rate and resolution just fine.  The problem is, it doesn't stick between sessions.  So I have to reload and tweak the damned thing each time.
launch nvidia-settings with sudo:
```
sudo nvidia-settings
```

and make sure you save your settings

---

### Post by raymacey on 2007-04-15
> **tseliot said:**
> launch nvidia-settings with sudo:

That's how I've been doing it from the start...

---

### Post by raymacey on 2007-04-17
Any more ideas?  The settings simply won't stick between sessions no matter what I do...

---

### Post by rgd55 on 2007-04-17
Can the Nvidia Settings GUI saved as a permanent tool?

---

### Post by sygin on 2007-04-17
Hi,

I had a problem with nvidia drivers and having to change the refreshrate using the app nvidia-settings. The KDE Monitor & Display configuration only shows weird values for refresh rate. Every time X11 restarted I had to run nvidia-settings to restore the refresh rate.

I solved this by using the KDE  Systems Settings, Monitor & Display config application, to change the refresh rate to the lowest (51 Hz) setting and my problem went away.  It seems that the KDE monitor configuration application does not work well with the nvidia driver. 

To fix the Beryl problem you need to enable some options in xorg.conf. Try:
sudo nvidia-xconfig --add-argb-glx-visuals


I hope this helps,
Sygin

---

### Post by strave on 2007-04-20
Hi,

you might want to have a look at this bug:
[https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/88431](https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/88431)

Deleting ~/.kde/share/config/displayconfigrc should help!

Stephan

---

### Post by oliwally on 2007-04-24
> **strave said:**
> Hi,

you might want to have a look at this bug:
[https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/88431](https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/88431)

Deleting ~/.kde/share/config/displayconfigrc should help!

Stephan

I've got the same problem. I tried deleting displayconfigrc, but it seems to get recreated.

How to we make the Nvidia settings stick?

---

### Post by oliwally on 2007-04-26
> **oliwally said:**
> I've got the same problem. I tried deleting displayconfigrc, but it seems to get recreated.

How to we make the Nvidia settings stick?

Can anyone help with this problem?

---

### Post by shlomi on 2007-12-22
I have the same problem too! any of you managed to solve that??

---

