---
title: "Secondary monitor goes to sleep while atching movies no matter what i do"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2007-05-09
Hi,

I'm using an ATI Radeon X1300 with the restricted drivers.  I am also using the default settings for tvout that get set when installing those where my tv is just a clone of the primary monitor.  

Whenever I use vlc or any other program for that matter to watch a movie after a while (30 mins?... maybe less?)  the tv goes black.  I'm assuming it's just going to sleep because if I press a button or move the mouse it comes back and the sound continues while the tv goes out.

I've tried setting the power management so the pc is never idle and turned off screensavers but none of that worked.  Does anyone know how to make it so it won't go to sleep.  Otherwise no movie watching on linux :(


Thanks

---

### Post by _hawk_ on 2007-05-10
If you are using beryl, it overwrites the gnome-settings for screensaver. If that is the case, do

sudo nano /etc/X11/xorg.conf

then simply go to the bottom and add

Section "ServerFlags"
    Option      "blank time" "140"
    Option      "standby time" "140"
    Option      "suspend time" "140"
    Option      "off time" "0"
EndSection

Or whatever other time you want to set, given in minutes

---

### Post by djrobthaman on 2007-05-10
Thanks for the info.

I'm kind of using beryl.  Have it installed and am using the base decorations but not running beryl-manager because of the white cube problem and no using emerald because of the missing window borders problems that I still haven't found a fix for using an ATI card.

I guess I'll do that, but is there any other way I could fix it so that the screensaver and powersave have their regular times 10 mins, 40 mins, etc but vlc forces the tv to stay on whenever it is running?

---

### Post by djrobthaman on 2007-05-10
By the way,

A little bit off topic.  I've noticed that whenever the screensaver is activated the screen just fades to black and in order for me to view the screensaver I have to very carefully move the mouse just a little bit.

You wouldn't happen to know how to fix that would you?

---

### Post by _hawk_ on 2007-05-14
No idea, really. You could try to change the parameters given in the file, play around some =)

---

