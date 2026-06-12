---
title: "Audio stops working randomly?"
date: 2008-05-13
forum: Multimedia Software
---

### Post by Roasted on 2008-05-13
There's times I sit here and I go to start a song, and it just doesn't work. When it loads in Audacious, it doesn't even activate as if it's playing. It just says 00:00 and the time never goes up. When I hit play, nothing happens. If I CTRL ALT Backspace, it backs out to the login screen, however, the sound isn't restored then. I must reboot for the sound to be re-activated. 

Why?

---

### Post by zeav on 2008-05-15
Same here, or when I login again, it only appears a grey box, and it shows its an text area there.. but I can't see anything :( Then I have to shutdown the computer by holding in the shutdown button.

I have a Dell Inspiron 1501 with all the drivers installed from Ubuntu except the Wireless and the graphics card.

---

### Post by Roasted on 2008-05-15
I just might reinstall Gutsy.

Again.

---

### Post by ubuntu-freak on 2008-05-15
Are you both Hardy users? Try explicitly selecting PulseAudio in System > Preferences > Sound, instead of Auto Detect. If there is no improvement, even after a reboot, switch to ALSA instead (Gutsy used ALSA as default). You will have to tell non-GNOME apps (VLC, MPlayer etc) that you are now using ALSA, which you can do in their preferences. Reboot if anything weird happens, then test again.
 
Nathan

---

