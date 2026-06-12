---
title: "Switching between laptop LCD and external LCD"
date: 2009-11-04
forum: Multimedia Software
---

### Post by bovender on 2009-11-04
Hi all,

I have a problem with switching between my laptop's display and an external screen. This is with Ubuntu 9.10, fresh install (last weekend) on a Thinkpad T61 laptop computer.

I need to be able to plug a projector or external LCD screen into the VGA port and press Fn+F7 to switch to that display. However this does not work. When I press Fn+F7 (the usual Thinkpad combination), the screen goes black for a second, and then comes back on again. Occasionally I briefly see the message "Could not set the configuration for CRTC 321" in the top-right corner.

Using sudo nvidia-settings, I can manage to detect the two screens, set the X server mode to TwinView, and have an extended desktop. I've also used the tool "disper" to switch between displays using the terminal

When giving presentations at work, I can't possibly fumble with a terminal or nvidia-settings. It must be possible to press a key and start the presentation (either in extended desktop, or with a cloned screen).

If anyone has an idea how to make this work, I would really appreciate it. (BTW, what does 'CRTC 321' mean? Windows could not have produced a better error message than that...)

Thank a million!

---

### Post by cybertesla on 2010-03-27
I have the same laptop and the same problem.  My project management roll requires me to do a lot of presentations in meetings.  Using the nvidia gui tool to switch between displays every time is highly impractical.  I need the Fn+F7 to work to switch display settings.  It seems no one has a solution, so I may have to try and hack something.  I haven't messed with display settings in a while so I'm not making any promises.

---

### Post by teejmya on 2010-03-27
Run the following command to autodetect displays and set the extended desktop

> disper --displays=auto -e

You've probably done that already, but that should autodetect displays when disper detects a new monitor.

You've said that you used disper, but I didn't know to what extent. Hope this works for you.

---

### Post by NoBugs! on 2010-03-29
If you install the advanced [CompizConfig]("apt://compizconfig-settings-manager") Settings Manager, you can go in to the Commands section and assign up to 12 commands with key-combinations, then run the command with the shortcut. For example, you could assign these commands to key-shortcuts and run the shortcut to set dual or single screen:

xrandr --output VGA1 --off

xrandr --output VGA1 --mode 1024x768

---

