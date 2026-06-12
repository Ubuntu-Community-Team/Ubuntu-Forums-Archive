---
title: "Weird Intel i810 Issues"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by jkpj on 2007-09-15
Hi, all! I've been using *buntu for about 6 months now, and I'm having a problem.
I'm currently using Ubuntu, which is what I started out with.
Randomly, sometimes twice a day, sometimes twice a month, my cursor will freeze, my hard drive activity light will come on solid, and then my cursor will disappear. Then, my screen goes blank, and either stays blank, or switches to 640x480@60Hz and fills the screen with dark colored stripes that change color and move position (or blink on and off). The computer appears to function normally, and any apps that don't require X continue to run. The only way I can fix this problem is by rebooting (Ctrl+Alt+Backspace has no effect; X appears to restart but the stripes don't go away).
I used Kubuntu for a while because of this problem, and it didn't occur at all unless I was running a GTK+ app, but now I'm back to Ubuntu, because I prefer GNOME.
My video card is an Intel i810 (00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)).
I've also gone over the logs in /var/log and found nothing out of the ordinary.
Any help here would be greatly appreciated! Thanks!
-John

---

### Post by w4ett on 2007-09-15
I'd try to use the newer xorg-driver-intel:
```

sudo apt-get install xorg-driver-intel
```

Then from the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "intel" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This should get you to a GUI desktop

---

