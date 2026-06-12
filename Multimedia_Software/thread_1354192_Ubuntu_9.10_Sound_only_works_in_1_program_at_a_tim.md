---
title: "Ubuntu 9.10 Sound only works in 1 program at a time"
date: 2009-12-13
forum: Multimedia Software
---

### Post by warrenreese on 2009-12-13
I have looked for a few hours for a solution to this problem, I found some people who had similar problems; however, none of their solutions were successful for me. 

Some information:

The sound works in whichever program that is opened first- even if the first program is muted.

--------------------

I restarted and found I was unable to load my current kernel, switched to a previous one and everything worked fine. Still unsure why the first one was unable to load but... I'm happy, everything works fine so far.

---

### Post by lidex on 2009-12-13
Try running pulseaudio device chooser. Enter ```
padevchooser
``` in Alt+F2 run dialog. Click on the icon in systray and select "Configure local sound server" then select "Simutaneous Output" tab. Make sure box is checked.

---

### Post by lidex on 2009-12-13
The three most popular issues I've seen with Karmic audio problems are 1) not loading correct kernel 2) alsa mixer outputs muted and 3) modem stealing output.

You may want to update your system and then update grub and reboot to make sure you're using proper kernel.

```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

---

### Post by warrenreese on 2009-12-13
Thank you, it appears that the kernel was the problem. 

I ran those commands you provided.

---

