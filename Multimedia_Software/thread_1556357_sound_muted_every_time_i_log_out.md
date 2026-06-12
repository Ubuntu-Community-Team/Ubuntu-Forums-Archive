---
title: "sound muted every time i log out"
date: 2010-08-19
forum: Multimedia Software
---

### Post by el_baby on 2010-08-19
Hi,

I don't know if this is happening since I installed/upgraded or later on (I use 3 different machines and this only happens in one).

Whenever I log into gnome, the sound is muted and the slider is quite low (that is, every time I have to unmute it and then slide the control to the right).

I've been trying to solve this for some time but couldn't. I followed the instructions on [thread=1298630]this thread[/thread] and other similar ones and it still doesn't work.

If I save the settings using ```
sudo alsactl store 0
``` the settings are actually saved on **/var/lib/alsa/asound.state**, but they're not restored when I log in.

If I log in, open an xterm window and manually run ```
alsactl restore
``` the settings are restored.

However if I add ```
/sbin/alsactl restore
``` to the **Startup Applications** they are not.

The last thing I noticed, by turning my speaker volume knob all the way up is that sound is actually muted when I log OUT, not when I log IN. In fact, I don't know if it's my gnome session closing or gdm starting.

I'm using Lucid 64 bits on a plain desktop (HP DX2400 with on-board intel audio card).

---

### Post by jabeavers on 2010-08-19
I had a similar problem and fixed it by adding alsa-utils (if I remember the name correctly) as a start up script to /etc/rc*.d/ directories. The "$alsa-utils start" command restores the mixer settings that alsactl store sets. If I remember... there should also be a shutdown script in, ummmmm, somewhere. When I get a chance to look at my pc, I'll tell you. See if putting alsa-utils into the /etc/rc*.d/ directories helps (you usually link to alsa-utils (wherever that is, I think it's in /bin but can't remember), by typing sudo ln -s /bin/alsa-utils /etc/rc5.d/S50alsa-utils: the name needs to be prepended with S50. Oh, and I always mess up the "ln" command and putting the arguments in the wrong order. If it tells you that file already exists, try switching the args). You might only need to put it in /etc/rcS.s/ directory. When I get in fromt on my linux box, I'll check all these things and give you a more definite answer. It might be about 4 hours from now.

---

### Post by jabeavers on 2010-08-19
Ok, alsa-utils is in my /sbin folder (you can do a "$which alsa-utils" to see where it is on yours. I did a soft link to that script in /etc/rc0.d/K50alsa-utils and /etc/rc6.d/K50alsa-utils. I also did a soft link to alsa-utils in /etc/rcS.d/S50alsa-utils. The K## files are files called to kill programs (thus "K") during shutdown/restart, and the S## files are called to start a program when the os boots. When done like this, K50alsa-utils stores the current settings and S50alsa-utils restores the settings on the devices. This worked for me, but I have seen threads that used this method and it did not work for them.

John

---

### Post by el_baby on 2010-08-20
John,

thanx for your help, but messing with /etc/rc* scripts does not help since the problem is not the first time I log in (after booting) but logging out and then logging in again.

As I wrote above, I noticed that the mutting happens during the log out process (I don't know why or where) and I don't know how to restore it while re-logging.

---

### Post by jabeavers on 2010-08-20
Ohhhh, so you boot up, log in, set your levels, log out and back in and the levels are messed up?

---

### Post by el_baby on 2010-08-20
yes, in fact, I don't have to set the levels the first time I log in after booting. 

That is, the *first* time I log in after booting, everything works fine (the sound isn't muted and it is at the level I set and saved).

When I log *OUT* the sound is muted (if I have the physical knob on the speakers all the way up I *hear* when it is muted).

After that, when I log back in, the sound is muted.

---

### Post by jabeavers on 2010-08-20
Can you try putting "alsa-utils start" in your startup applications and see if that does anything? Do the startup applications run at login or bootup? Isn't there a .bashrc file in the home directory that runs at login? Can you add alsa-utils start or alsactl restore from that script?

Just some thoughts.

---

### Post by el_baby on 2010-08-20
> **jabeavers said:**
> Can you try putting "alsa-utils start" in your startup applications and see if that does anything? Do the startup applications run at login or bootup? Isn't there a .bashrc file in the home directory that runs at login? Can you add alsa-utils start or alsactl restore from that script?

Well... I tried changing **alsactl start** for **alsa-utils start** or **alsa-utils reset** in the *Startup Applications* without success.

I do have a **.bashrc**, but it is only invoked if and when I open a bash session (e.g. when I open an xterm). When I start the gnome session and, say, I only open the browser, **.bashrc** doesn't get run.

---

### Post by jabeavers on 2010-08-20
Ohh, I'm not real knowledgable about the startup sequence yet, and .bashrc was my best guess. Is there an equivalent to rc.local that is run when a user logs in?

I wonder if you can check the /var/log/messages log file for anything, or dmesg. I know only what I've troubleshot on my own pc's, and I'm only just now learning sound in linux.

---

