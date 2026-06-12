---
title: "Mythbuntu specific keymap in relation to multimedia keys"
date: 2015-02-26
forum: Mythbuntu
---

### Post by derek29 on 2015-02-26
On a stock Ubuntu installation the "volume up" and "volume down" multimedia key events adjust the volume, which is displayed by a graphic overlay on the screen.  The keycode IS reported by xev as a KeyRelease event but not as a KeymapNotify event.  That is because KeymapNotify is intercepted by something, maybe the mixer, so it doesn’t reach xev, I don't know.  Other important media keys such as play/pause, stop, back, forward are inactive by default and both KeyRlease and KeymapNotify events show scancode.  There is no keybinding for them by default.

With Mythbuntu both KeyRlease and KeymapNotify events are intercepted for volume as well as play/pause, stop, back, forward, next track, previous track.  An overlay is displayed.  The events are being intercepted and interpreted by something in Mythbuntu before xev can grab the keycode.  By Mythbuntu, I am referring to whatever customization and plugins that makes Mythbuntu out of Ubuntu.  

In a default Mythbuntu install, when I press a media key on my wireless keyboard, such as the "play" or "volume up" key, I see a graphic overlay on the screen.  For the first, a "no disc" indicator and for the second a graphic representation of the volume level.
Although Mythbuntu wouldn’t show keycode for any of these media key events, if I hold down the SHIFT key and press a multimedia key, such as volume down, I see both the scancode for SHIFT and the scancode for volume down.  (SHIFT + media key)  However, holding shift also prevents the action, it is merely pointed out as a test result.

My goal is to **map some of the media keys**, specifically, the play/pause, stop, forward and back KeymapNotify events to regular characters, such as P, Escape, back arrow, forward arrow.  This way I can control the MythTV media player with the media keys.  By default on Mythbuntu the media keys serve the DVD drive, which I don’t use. 

Please note:  Before suggesting using the MythTV Backend keybindings setup, the media keys discussed are not detected by the backend configuration program.
I thoroughly read "Keyboard Special Keys" on the MythTV Wiki at [http://www.mythtv.org/wiki/Keyboard_Special_Keys](http://www.mythtv.org/wiki/Keyboard_Special_Keys)
However, was unsuccessful as the KeymapNotify event is perhaps being intercepted before Xbindkeys, or maybe I just didn’t configure Xbindkeys correctly as the guide was old.

I just want to remap these keys.  I actually already know the keycode.  For example, the media key Play/Pause is keycode 172 and I would like to map it to the letter P which is keycode 33.  
Anyone having done this successfully I would be grateful for assistance.

---

### Post by MoebusNet on 2015-03-13
This may not directly answer your question, but have you looked at:

[https://www.mythtv.org/wiki/MythTV-HOWTO_-_0.27#Keyboard_commands](https://www.mythtv.org/wiki/MythTV-HOWTO_-_0.27#Keyboard_commands)

I have read that the current Linux kernel versions do not support keycodes above ~100 or so and that one of the changes to come in future kernel versions will be to support higher keycode numbers to enable multimedia keys in the kernel.

I'm currently just using the assigned keys (not the multimedia keys) on my wireless keyboard.

---

### Post by MoebusNet on 2015-05-04
Update: In Mythfrontend 0.27.4+fixes, Setup>Edit Keys opens keylinks menu. Unlink or assign keys here; you may need to unlink a key before you can assign it (eg VolumeDown = F10 so unlink then assign F11). Numerous keys are already linked. Note: Fn+(eg,F11) won't link but F11 will.

---

