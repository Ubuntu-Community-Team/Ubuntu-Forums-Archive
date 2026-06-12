---
title: "[SOLVED] Monitor goes to sleep while playing DVDs"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by flamingsole on 2008-04-20
I've recently started using Ubuntu for playing DVDs. I've been experimenting between Totem and VLC, for the most part. I've also tried MPlayer.

My issue is that my monitor always goes to sleep while a DVD is playing. It's definitely not the screensaver, as I picked one of the screensavers that is not just a black screen. I don't think it's the power management either, though. It happens after 10 minutes or so (and the settings say that the display should turn off after 40 minutes), and the monitor keeps its green light on.

I have checked the box in all the DVD programs to disable the screensaver. I even tried the Screen Actions, and creating a hotspot where the screensaver would be disabled.

Is there any kind of solution for this? Or maybe another DVD-playing software that does actually send a sign of activity to the system so that it doesn't think it's idle?

Thanks so much for any help,
Jonathan

---

### Post by bran on 2008-04-20
I use Kpowersave instead of the gnome powermanager for a lot of reasons but one is that it allows you to create blacklists of programs which will keep the system from suspending or turning off the display if they are running.

kpowersave is available in the applications add/remove or synaptic.

disable  the native powermanager  system > preferences > sessions   and uncheck power manager

---

### Post by flamingsole on 2008-04-20
That seems to work very nicely. I set up a blacklist, and added Totem to it. Thanks for the advice.

---

### Post by flamingsole on 2008-04-20
Also had to remove a setting in xorg.conf, which wasn't a default setting anyway. Apparently, the gnome power manager was ignoring the setting, but the kde one paid attention to it. Thanks for the help!

---

### Post by Phil465 on 2008-05-06
I have the exact same problem.

                I installed kpowersave to run as default instead of                       gnome-power-manager. However, whenever I click the power-down button I can't access anything and no options to power-down come up. My mouse moves around though, but can't access anything with it. The only solution seems is to have **both** gnome-power-manager and kpowersave running simultaneously.

In either case, I have the same problem. Any suggestions?

Also,

[I]flamingsole said:

"Also had to remove a setting in xorg.conf, which wasn't a default setting anyway. Apparently, the gnome power manager was ignoring the setting, but the kde one paid attention to it. Thanks for the help!"
[/I]
What was the setting flamingsole?

---

### Post by flamingsole on 2008-05-11
I apologize; I think I marked it solved a bit prematurely when the settings were present in the KDE power manager. It didn't seem to fix it after all, upon playing a DVD it still went to sleep after a while. I also ran into the issue with the KDE power manager, and I like having a red button I can click that actually does something, so I went back to gnome.

Sorry about that. Please do update, if you find out anything.

Jon

---

### Post by BlueSkyNIS on 2008-05-17
Well, many users are having this problem (including me also)


I have found some similar threads, but no solution: :(
[*black screen every 10 minutes on playing video*]("http://ubuntuforums.org/showthread.php?t=773873")
[*screen goes blank after 15 minutes, no screensaver/power management*]("http://ubuntuforums.org/showthread.php?t=719314")
[*Power management Issues*]("http://ubuntuforums.org/showthread.php?t=702877")
[*Disable xscreensaver while playing movie*]("http://ubuntuforums.org/showthread.php?t=691560")
[*screen turning off when watching movies?*]("http://ubuntuforums.org/showthread.php?t=187313")

:confused:
Does anyone have an solution? :confused: :(

---

