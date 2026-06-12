---
title: "Xine fullscreen problem in Feisty"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by pricorp on 2007-05-01
After upgrading from Edgy to Feisty, the xine command windows (Open file, Controls...) appears in the background and not on top when xine is in fullscreen mode. Each time, I have to leave the fullscreen mode to visualize the window. Do anyone know how to make the windows appear on top ?

For example, in fullscreen mode, when hitting the "g" key it's not possible to visualize the control panel. Same thing with "ctrl+o", the open file window appears in the background.

Thank you for your help,

---

### Post by Pragmatist on 2007-05-18
I'm having the exact same problem.  Unfortunately I haven't found a solution yet :(  Just thought misery loves company! :)  I will post solution IF I find one.  Any help is welcome.

---

### Post by Pragmatist on 2007-05-18
Good news!  I've narrowed down the problem.  I installed fluxbox, a lightweight window manager, and was able to run xine without our problem!!

So, it is NOT:

1.) a X configuration issue
2.) a Xine configuration issue (I checked this by using an older xine config file that  worked for me in the past)

The problem almost certainly has to do with gnome and/or metacity.  Probably metacity as that is the window manager, and our problem is a window problem.

Enough for one day!  I will post again when I, hopefully, narrow the problem still further.

---

### Post by Pragmatist on 2007-05-18
The problem is definitely due to metacity.  I did the following experiment:

1. I entered a virtual terminal
2. I stopped gdm
3. I restarted just X
4. I started metacity (so now there is just X with metacity (no GNOME))

The problem still occurs in this situation.  So, it is not a problem with GNOME.

Now all we have to do is figure out how to fix the metacity problem!  I've examined the various gconf settings for metacity and none of the changes I tried would solve the problem.

Help!

---

### Post by Pragmatist on 2007-05-18
I've decided to use openbox as my window manager rather than metacity.  I followed these simple instructions in the wiki:

[https://help.ubuntu.com/community/ReplaceMetacityWithOpenbox](https://help.ubuntu.com/community/ReplaceMetacityWithOpenbox)

If you don't like it, you just change one line in a file and you'll have metacity start by default again.

Of course, the xine problem no longer exists!!  This is unquestionably a metacity problem.

Since I've decided not to use metacity for now, I won't be working on this.  However, if anybody finds a solution I'd be interested to know it.

Thanks.

---

