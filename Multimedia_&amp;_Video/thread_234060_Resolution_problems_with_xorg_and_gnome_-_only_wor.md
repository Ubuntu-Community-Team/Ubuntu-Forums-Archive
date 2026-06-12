---
title: "Resolution problems with xorg and gnome - only works as root?"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by mattlesko on 2006-08-10
Hello,

After happily discovering that my laptop (Toshiba Satelite A105-S4001, video card "Intel Corp Integrated Graphics Controller", using "vesa" driver) did 1024x800, I decided to test it out.

I updated my /etc/X11/xorg.conf, adding "1280x800" to the Display section, right before the previous value (1024x768). Since this causes errors a lot of times, I try a 'startx' as root. Everything comes up fine, including a complete gnome-session; I can even see it as an option for System->Preferences->Screen Resolution.

Next I try exiting out and restarting gdm from /etc/init.d/gdm restart. I try to login as my usual non-root account and it bounces back. To try and figure out the problem, I login as my usual account and try a manual 'startx'. It dies with a Signal 11 error. I try an xinit, followed by a 'fluxbox' command. The resolution looks like 1280x800 to me, without an problems. Trying to start 'gnome-session' instead of 'fluxbox' from xinit kills the machine (or at least my patience, since I reboot it).

Changing the xorg.conf file back to the original state (no "1280x800" lines anywhere lets gdm/gnome log in a normal user just fine. 

Choosing KDE as the type of session from GDM works just fine. My guess is something wrong with gnome, but I've tried an apt-get upgrade and all was fine. Anyone have any ideas? Or at least where to look?

---

