---
title: "Audio skips/repeats every couple minutes."
date: 2013-10-16
forum: Multimedia Software
---

### Post by denjay on 2013-10-16
So when I'm playing an audio file on VLC or rhythmbox, every few minutes the audio repeats for about a second and then returns to the file as if it had been playing the whole time. So let's say it starts repeating (very fast) at time 1:05 for 2 seconds, the audio will return to normal at 1:07. So the file is still playing but the audio is just messed up in that short time. I'm assuming its a problem with pulseaudio but I'm not sure what to do to try to fix it. I've tried reinstalling it and doing what's in this thread [http://ubuntuforums.org/showthread.php?t=2146443](http://ubuntuforums.org/showthread.php?t=2146443). Neither fixed the problem so I'm not sure what to do.

---

### Post by zombienerd1 on 2013-10-16
Does it start playing again by itself with no interaction?  Or does it start playing again once you move the mouse or press a key?

---

### Post by zombienerd1 on 2013-10-16
If you need to press a key or move the mouse to get it to start playing again, it could be an issue with the clocksource.  I had the same issue with my Toshiba netbook.  

Here's my fix:

[COLOR=#000000]>sudo gedit /etc/default/grub[/COLOR]

[COLOR=#000000]Find the line:[/COLOR]
[COLOR=#000000][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/COLOR][/COLOR]
[COLOR=#000000]Change it to:[/COLOR]
[COLOR=#000000][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer clocksource=jiffies"
[/COLOR][/COLOR]
[COLOR=#000000]Save file, exit gEdit.[/COLOR]
[COLOR=#000000]then:[/COLOR]
[COLOR=#000000]>sudo update-grub[/COLOR]
[COLOR=#000000]>sudo reboot[/COLOR]

---

### Post by denjay on 2013-10-16
No, it goes back to playing as normal even if I don't do anything. I'll try that fix anyway and see what happens.

---

### Post by denjay on 2013-10-16
Nah, still have the same problem.

---

