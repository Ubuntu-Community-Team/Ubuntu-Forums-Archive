---
title: "[SOLVED] Graphics card"
date: 2008-05-02
forum: Multimedia Software
---

### Post by Darkade on 2008-05-02
back on Gutsy there used to be a graphic tool to configure the driver you used for the graphics card.(Under System>administration>and something like screen or monitors) but on 8.04 I just can't find it. Where has it been moved or how can I configure this on graphics mode

---

### Post by DandyDon on 2008-05-02
> **Darkade said:**
> back on Gutsy there used to be a graphic tool to configure the driver you used for the graphics card.(Under System>administration>and something like screen or monitors) but on 8.04 I just can't find it. Where has it been moved or how can I configure this on graphics mode

It should be under System-Administration-XServer Settings.

If its not,(Mine wasn't) Google EnvyNG, follow his scripts to uninstall what you have, install EnvyNG; and get the correct driver. EnvyNG works for both ATI and Nvidia cards. It will install under Applications-System Tools.

Then go to System-Administration you should see it there.

This is what worked for me.

---

### Post by Darkade on 2008-05-02
thanks, that would work if I had a nvidia or ati graphics card to install. but I'm trying to install an intel graphics card. I changed the driver about two weeks ago, just playing you know how this is :lolflag:, (before upgrading) and now I have a terrible resolution. Today I finally decided to fix it but I just didn't found the tool I used to configure (or to broke) my graphics card. :(

---

### Post by Darkade on 2008-05-08
I got it solved starting in recovery mode and selecting "fix X11" or something like that. Thank you :lolflag:

---

