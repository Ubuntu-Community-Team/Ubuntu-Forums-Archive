---
title: "Nvidia settings contrast, brightness, gamma reverts after restart"
date: 2009-04-22
forum: Multimedia Software
---

### Post by Velvet_Man on 2009-04-22
Hi, so I've been trying to find a way to adjust brightness, contrast and gamma since my laptop screen doesn't have any buttons or dials to do this with.

After some searching on this forum I found out about the nvidia settings manager app, and that works perfectly. It lets me adjust brightness, contrast and gamma as well as resolution and refresh rate.

However, after a re-start, all of these changes revert back to their default settings. I tried running it under gksu, but that didn't have any effect.

Oddly enough, the screen resolution and refresh rate hold up after a restart, just not the brightness, contrast and gamma settings. I'm guessing this is because the resolution section has a Save to Xorg.conf function that the colour correction section of the app doesn't seem to have.

Does anyone know how I can make these changes permanent so I don't have to run this app every time I start my computer?

Thanks for the help.

---

### Post by dabl on 2009-04-22
This may be more than you wanted to know, but your answer is in there:

[http://sidux.com/PNphpBB2-viewtopic-t-15061.html](http://sidux.com/PNphpBB2-viewtopic-t-15061.html)

Ubuntu is a Debian Linux, as is sidux, so don't be put off by the different distro -- all the facts about nVidia settings are the same.

---

### Post by lovinglinux on 2009-04-22
Open "System >> Preferences >> Sessions" and add a new application and use the following command for it:

```
nvidia-settings -l
```

---

### Post by Velvet_Man on 2009-04-23
> **lovinglinux said:**
> Open "System >> Preferences >> Sessions" and add a new application and use the following command for it:

```
nvidia-settings -l
```

That worked perfectly. Thank you. I had tried the adding it to sessions before, but it was driving me nuts having to close the app every time I restarted.

And thanks dabl for the great link. I've bookmarked it for future reference.

EDIT:

Hmmm I thought editing the first post with "[SOLVED]" would mark the thread, but it's not showing up on main forum page.

---

### Post by lovinglinux on 2009-04-23
> **Velvet_Man said:**
> That worked perfectly. Thank you. I had tried the adding it to sessions before, but it was driving me nuts having to close the app every time I restarted.

You are welcome. This happened to me a while ago. Was driving me nuts too. The trick is the ***-l*** in the end of the command.  ;)

---

