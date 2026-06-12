---
title: "Banshee keyboard shortcuts"
date: 2009-04-25
forum: Multimedia Software
---

### Post by defaria on 2009-04-25
I have a multi media keyboard - Logitech Cordless Keyboard in fact. I was pleasantly surprised that Jaunty recognized it and that most of the multimedia functions just worked. For example there's next/prev track, play/pause, stop, sleep, email buttons and all of them worked - with rhythmbox. The Shopping, iTouch and Favorites buttons didn't work but I didn't care.

So I switched to banshee and none of the specialized keys of Next/Prev, Play/Pause work anymore! :(

Anybody know how to get them working?

---

### Post by eskwayrd on 2009-05-29
I'm having the same problem with Banshee, but also with Rhythmbox.

I can confirm that the multimedia keys on my keyboard are being detected properly; in System > Preferences > Keyboard Shortcuts, I can click on the key definition for a particular sound shortcut, press a multimedia key, and have it appropriately recognized.

Firefox does respond to the browser-specific keys, and the volume up/down keys adjust the overall system volume, however the mute button does not mute/unmute.

For me, I hardly use the multimedia keys, but mute/unmute and play/pause are useful and it would be nice to get them enabled.

I'm using 9.04-amd64.

---

### Post by eskwayrd on 2009-06-16
Here's an update, based on suggestions offered in similar threads:

The multimedia keys on my keyboard are recognized by the kernel and Gnome. If I open the Keyboard Shortcuts preferences, I can assign any of the multimedia keys to, for example, Window Management commands such as 'Activate the window menu'. Then, pressing the assigned multimedia key opens the window menu.

The problem would therefore seem to be in the processing of the commands 'Volume mute', 'Next track', 'Previous track', 'Play (or play/pause)'. The commands to not appear to communicate with any media app I have tried: Banshee, Rhythmbox, Amarok, Totem, VLC, etc.

I see bugs registered on launchpad and bugzilla.gnome, but so far, nothing promising (if there's anything, it's mostly attempts to diagnose kernel or dbus messaging).

---

