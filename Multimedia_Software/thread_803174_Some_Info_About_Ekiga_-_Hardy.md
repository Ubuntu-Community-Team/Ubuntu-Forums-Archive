---
title: "Some Info About Ekiga - Hardy"
date: 2008-05-22
forum: Multimedia Software
---

### Post by d-man97 on 2008-05-22
I have heard about ekiga trying to register before NetworkManager (nm-applet) activates the users internet connection.
I have also heard about people saying that ekiga will not re-register/reconnect when their system changes ip configuration.
Just for the record, this behavior is not a bug. It just has not been implemented yet.
	See: [Detection of dynamic IP address changes and coming up and going down of network interfaces]("http://wiki.ekiga.org/index.php/Roadmap_to_3.00#Hardware_Features").

For now, since I have this problem, I created a simple sleep script, starting via Sys>Pref>Sessions, to load this and some other programs. (I made them start in a certain order, so their icons would always be in the same position on the system tray.)
```
#! /bin/sh
# ~/startup.sh

sleep 10
tracker-applet &
sleep 2
pidgin &
sleep 2
ekiga &
exit 0
```

And finally, I had to disable my screen-saver, but was able to keep it running, and my monitor still turns off without any negatives. Prior to this change, Ekiga would hang in a peculiar manner after returning from screen saver/locked desktop, if you have this problem it has to do with the way ALSA plays with pulseaudio, and I have not seen a fix for it yet. I have even seen an Ekiga dev posting on ALSA bug tracker about the problems. PulseAudio has a special feature for handling RTP streams as their own inputs, but I doubt Ekiga can use it as of now.

Anyways, sorry for the side-tracking, Back to the point. Until Ekiga 3.0, it seems like we will have to live with making sure our internet is ready before Ekiga registers, and reset them manually with the check boxes under Accounts when there is a problem.

I'm sure you could make a pre/post screen saver script to disable Ekiga, but then you will miss calls. Plus, there is a lock screen item you can put in the panels for easy access to the security of locking.

-Derek White

---

### Post by erlguta on 2008-06-27
Very useful. Thank you

---

