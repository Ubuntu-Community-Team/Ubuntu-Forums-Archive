---
title: "need help with settings after ATI driver install"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by yellowband on 2006-07-10
Hello
well i think i finally got the newest AtI drivers installed for my mobileX300 (dell inspiron). When i run glxgears, the gears spin but no framerate numbers are shown.

anyways, my main problem is that i have a dell monitor hooked up to my computer, and i can't see any video on it. Teh laptop screen and monitor are identical except when i play a video. When i do, the laptop screen plays it, but the monitor just shows a blank box where the video should be.  How do i fix this?

Also, the resolution on the monitor is really high and i would like to lower it.When i do, things don't get bigger and fill the screen, Insted the screen size gets smaller and evertying stays the same size (in other words, there is ablack border around a smaller screen). How do i adjust this?

thanks for the help.

---

### Post by Craig Watson on 2006-07-10
In a terminal, type 'aticonfig -h' to get the list of possible commands (I can't remember all the ones you need, and uninstalled the driver...) But for the video, that's because the video overlay is set to your laptop screen (screen 0). If you want to change that, type 'sudo aticonfig --video-overlay-on=1' (I think)
Sorry about the resolution though, I don't know anything about that...
Good luck...

---

### Post by Prefader on 2006-07-10
The resolution problem is most likely a BIOS setting.

While the laptop is POSTing, hit F2 to enter setup.  On one of the pages in setup, you should see a setting called "video expand" or something to that effect - make sure it's enabled.  What that does is force the system to scale lower resolutions up to the native resolution of your LCD, where right now it's displaying pixel for pixel.

---

### Post by yellowband on 2006-07-10
thanks for the replies

i don't think the resolution thing is a bios problem as low resolutions fill the screen when the ATI driver isn't installed, and when i'm using win XP.  I'll have a look anyways though when i get home.

---

