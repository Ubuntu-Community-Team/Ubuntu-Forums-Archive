---
title: "No sound intermittent problem in Karmic"
date: 2010-02-26
forum: Multimedia Software
---

### Post by HalfWord on 2010-02-26
This is my first post, so let me first say: Hello everybody :)
To introduce myself a bit, I'm from Croatia and use Ubuntu since 7.04 or 7.10 (Xubuntu then, on an older laptop). Now I have Ubuntu Karmic (AMD64) on my ThinkPad R61i, I think I started with 8.04 on it. I must commend Ubuntu for being my first day-to-day-use Linux system, I've been playing mostly with Debian (that helps a lot here) before, and started with Slackware in 1997, after being introduced  a bit to Unix when I was using Solaris in 1996. I am at this time a Windoze admin, and a Linux user, but would like to become both with Linux ;)

Now, to get back to my problem, on my ThinkPad I mentioned I have had a strange problem with sound for a while, I believe it first occurred when kernel version was 2.6.31-14. Namely, sometimes after I log in to the Gnome desktop, I get no sound at all, and in the Sound Preferences applet no sound hardware gets listed. There is no rule as to when it happens, sometimes I get the sound device, sometimes I don't, unfortunately sometimes I can reboot for ten times and not get it. 

However, the sound is present when I get to GDM (that "clink" sound) even if I don't get it when I log in. Sometimes (but not always!) I can get sound if I sudo some player, so it seems root can get sound even when my normal user cannot. I've even tried playing sound from the console before logging into the GDM, and as an ordinary user i couldn't hear anything, but if I played it as a root, I could. 

Sometimes I'd lose sound again when I hibernate and awake the machine. That stopped happening somewhere between kernel revisions *-17 and *-19.

I've tried changing outputs in playing applications, from PulseAudio to ALSA, and even to OSS, that gave no effect. I've also tried adjusting ALSAmixer in console and X, also to no effect. Tried loading/unloading snd- modules (this is a HDA codec on an Intel ICH8 chipset), also nothing.

I'm not sure where exactly the problem could be, and looking at various logs, nothing special caught my eye. If anyone has ideas what could this be, which logs to see etc. I'd really appreciate it...

---

### Post by HalfWord on 2010-03-07
Bump, anyone?
If someone has some idea where the culprit might be, I might at least post a bug report for it...

---

### Post by HalfWord on 2010-03-08
Ok, now I'm pretty sure it's Pulseaudio.

I've uninstalled PA, and after reboot I was at least able to play sound normally through ALSA. When I reinstalled Pulseaudio, Sound applets again showed no audio device, while the sound was still normal with ALSA. After reboot (with pulseaudio), no hardware was reported again, but this time ALSA wouldn't give sound too.

I should recheck by uninstalling pulseaudio again and rebooting a few times, but if I get normal sound with ALSA again, I guess I should report a bug against Pulseaudio.

---

### Post by HalfWord on 2010-03-10
> **HalfWord said:**
> 
I should recheck by uninstalling pulseaudio again and rebooting a few times, but if I get normal sound with ALSA again, I guess I should report a bug against Pulseaudio.

So far, seems that's it...
Without Pulseaudio, everything works normally through ALSA interface, even the system sounds work! I could simply leave it this way, the only problem being the Gnome/Ubuntu Sound Control Panel doesn't work without Pulseaudio. Of course, PA has better mixing, oh well... I guess I'll reinstall PA so Apport can collect data on it and then report a bug against it. And then uninstall it again to get sound back until the bug is fixed (or more data needed)...

---

