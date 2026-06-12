---
title: "Mystifying refresh rate problem"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-06-15
I think this is one for someone who wants a challenge, and it's going to take a while to explain. I've just had a fresh install today, so I can explain from the beginning.

When I first made this install, my refresh rate was 60Hz @ 1024x768. This was obviously unacceptable. So installed nvidia-glx and specified to KDE exactly what monitor I was using (a Samsung SyncMaster 793s). This gave me a Horizontal Range of 30-71 and a Vertical Refresh of 50-160, doing some calculations, this leaves me with a maximum refresh rate of 87Hz for 1024x768, which is good since I only intend to use 85Hz at the resolution.

So I reboot, and the login screen is at 1024x768@85Hz. No problem. But then I login, and it immediately changes to 1024x768@75Hz. KControl insists the maximum my monitor can do is 72Hz.

Now for the weird bit. If I change the monitor to something else, then change it back, I can select up to 87Hz. If I then select 85Hz and apply changes, I immediately get 1024x768@85Hz, which works splendidly. I can also do this with nvidia-settings.

So that should be the end of it. But it's not. If I logout then login again, I'm back to 1024x768@75Hz. KControl and nvidia-settings have forgotten what happened, and it's as if I never changed the settings.

Checking xorg.conf reveals it knows exactly what my HorizSync and VertRefresh are, and it makes at least two references to "1024x768@85". This, together with the login screen being at 1024x768@85Hz is saying to me that this is something specific to KDE.

Does anyone even have the slightest clue what's going on here?

---

### Post by tanelt on 2007-06-16
The answer is simple. The developers just keep ignoring this issue. Maybe it will get fixed in the next 10 years, who knows.

Until then you're probably better off with Windows. Like I am.

---

### Post by pandion on 2007-07-31
There is a checkbox to set the current resolution as the System Default Resolution.  Try that and see if that takes care of it.  There is also an option to save the current session as the Default.

---

