---
title: "Mouse pointer intermittently appears when watching videos with mplayer"
date: 2009-05-04
forum: Mythbuntu
---

### Post by pickledfish on 2009-05-04
Hi. I think this should be simple to fix but I can't find an answer.
The problem is that I reinstalled mplayer and now the mouse pointer appears on the screen every few minutes. It only appears for a second and disappears again. Not a major problem but annoying.
I'm assuming it's only a matter of adding something to the mplayer conf file to fix this? Any help would be much appreciated.

---

### Post by miau1010 on 2009-11-09
I'm having this same problem.

---

### Post by Stason on 2010-02-24
Menu (or right click) ==> Video ==> Stay on top ==> While playing


This would hide the pointer, which pops up when the "disable screensaver" script moves the mouse every now and then.

---

### Post by papibe on 2010-06-21
That didn't do it for me. Not even "Always on top".
Any other idea?

Regards.

---

### Post by wilee-nilee on 2010-06-21
If you bump the mouse or it gets a vibration it will show.

---

### Post by andree_b on 2010-06-22
It's a bug in mplayer... installing mplayer from smplayer PPA fixed it for me in 9.10.
(mplayer moves the mousepointer randomly to disable mousepointer)

But sadly in 10.04 the mplayer internal disable-screensaver stuff did not work anymore and i had to add heartbeat-cmd stuff to mplayer.conf to keep the screensaver disabled.

---

### Post by papibe on 2010-06-22
> **andree_b said:**
> 
But sadly in 10.04 the mplayer internal disable-screensaver stuff did not work anymore and i had to add heartbeat-cmd stuff to mplayer.conf to keep the screensaver disabled.

Did it work?  Would you share how?
Regards.

---

### Post by LowSky on 2010-06-23
you can install unclutter

---

### Post by papibe on 2010-06-23
@ LowSky: thanks, I tried unclutter, but it didn't do the job. Since mplayer itself keeps moving the mouse, unclutter never engages. May be playing with the -jitter option could have worked.

I went andree_b's way. I unchecked the "Disable screensaver" option (smplayer), and I add this line to my ~/.mplayer/config

```
heartbeat-cmd="gnome-screensaver-command -p"
```

It's working now ):P , that is: mouse is not visible after a few seconds, and the screen saver does not start.

:rolleyes: Obs: the screen saver's idle setting has to be > 1 minute.

Regards.

---

### Post by andree_b on 2010-06-24
[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]or if you use xscreensaver instead of gnome-screensaver:
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]```
heartbeat-cmd="[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]xscreensaver-command -deactivate &"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
```[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]
Without the "&" (sending command to background) i experienced small stutter everytime the command executed
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by jyavenard on 2010-06-24
add the following to your xorg.conf device section:

Option "HWCursor" "false"

Or in nvidia-settings, disable the hardware mouse pointer acceleration

---

