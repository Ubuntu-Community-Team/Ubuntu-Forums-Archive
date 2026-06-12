---
title: "A little sound help please..."
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by Mithrander on 2006-07-20
So I've been looking everywhere on google to try and get this working myself, but I can't seem to find anything...

Anyway, I have an external USB Audigy 2 NX soundcard that functions in Ubuntu. The problem is that Firefox uses my built in laptop soundcard and speakers which of course I don't want it to (I wanna use Real Rhapsody's web-based player to play music and it sounds crappy through the laptop).

The wierd thing is that XMMS uses the correct soundcard and so does Ubuntu when I log in or out. I've tried disabling the other sound card, but then I just get an error in Firefox.

This might be related...I get this error message when I go to System>Preferences>Sound

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

Also, I get this when I run 'esd' from terminal:

"- using device hw:1
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting..."

hw:1 is the correct device, my USB Audigy 2 NX soundcard...

Anyone have any ideas? Thanks!

*edit* one last thing...I've noticed that my sound 'skips' when I'm playing  out of the USB soundcard too...any reasons for that?

---

### Post by simonn on 2006-07-20
> **Mithrander said:**
> The problem is that Firefox uses my built in laptop soundcard and speakers which of course I don't want it to (I wanna use Real Rhapsody's web-based player to play music and it sounds crappy through the laptop).


I suspect that this is not Firefox using the wrong soundcard per se, but the plugin that runs Real Rhapsody. Flash? Java?

I had a similar problem with a Java app (Soft Squeeze) using the internal sound card. The was because it used the first soundcard, which happened to be the internal one, not my Audigy (PCI, not USB).

To get around this, I added the following to the bottom of /etc/modprobe.d/alsa-base:

```

options snd-emu10k1x index=0
options snd-intel8x0 index=1

```

This forced the Audigy to be the card 0 (the first card) and the internal to be card 1 (the second card).

You need to find out what drivers your soundcards use and do something similar i.e.

```

options [audigy driver] index=0
options [internal driver] index=1

```

The reboot.

You may need to change gnome to use the Audigy driver again after doing this.

Using, the following command may help - post the results if you are not sure:

```

$ lsmod | grep snd-

```

---

### Post by Mithrander on 2006-07-21
Okay thanks, I'll try that when I get home...

---

### Post by Mithrander on 2006-07-21
I think I've got it working...I think I just made it so linux just didn't load it...thanks a lot!

XMMS doesn't work now, but I think I can fix that...

oh and does anyone have any ideas on how to fix the audio from skipping?

---

