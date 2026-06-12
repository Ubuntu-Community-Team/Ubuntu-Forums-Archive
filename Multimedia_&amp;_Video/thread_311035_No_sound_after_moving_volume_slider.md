---
title: "No sound after moving volume slider"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by napg on 2006-12-02
Hi, I've been using Ubuntu for some time on my desktop PC, now I bought a notebook (Asus A8JS w/ HDA Intel) and after trying to understand why I was losing sound I reached the following conclusion, I have sound indeed, but:
 - If I open the volume control and move ANY slider the sound just mutes and never comes back again until I do a real Restart on Ubuntu (Ctrl+Alt+Backspace won't do it);
 - In a music player if I move the volume slider, the sound mutes, and I must do the same as above;
 - If I use the notebook's keys to control the volume the same happens;
 - If I move the slider of the volume control on the top right of the screen, it is at 100% and after trying to move it it just goes back to 100%.

I've searched the forums for something similar to this but didn't find anything, if someone has any idea what this could be, I would appreciate some help. Thank you.

Nuno Gomes

---

### Post by straxus on 2006-12-02
I don't have a solution for you, but I just got the same laptop, and I'm having the [same problem]("http://ubuntuforums.org/showthread.php?t=309707").  As a tip, you don't have to reboot to get the sound back up.  If you type: "*sudo /etc/init.d/alsasound reload*" in a terminal window, the sound system will reload and you'll have sound back.

---

### Post by straxus on 2006-12-03
Found the fix for us. Add the following line to /etc/modprobe.d/alsa-base

*options snd-hda-intel position_fix=1 model=3stack*

---

### Post by live4fun on 2007-03-18
Hi,

I also use the above described settings:
```
options snd-hda-intel position_fix=1 model=3stack
```

But I am still facing one problem. When I plug in an external microfone e.g. my headset, not the pluged in mic is used but still the laptops build in.

Does anybody off you have the same experience or even better a solution for that?

Best Regards,
Chris

---

