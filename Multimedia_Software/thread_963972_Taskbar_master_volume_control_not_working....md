---
title: "Taskbar master volume control not working..."
date: 2008-10-30
forum: Multimedia Software
---

### Post by s1mple_M4N on 2008-10-30
Hi all.

Really enjoying Hardy installation, everything is running well with one odd exception - the master volume control in my taskbar will not adjust sound volume in any of my media applications (Totem, audacious, banshee, Firefox flash videos).

Volume can be adjusted in each application but I would like to be able to do it from the taskbar.

I don't want to play around with too many settings, so not sure if it's something simple or I have to download drivers...

In System > Preferences > Sound everything is set to 'Autodetect', and when opening the sound properties of 'SiS SI7012 (Alsa mixer)' everything looks OK.

Is this a known bug or something I may have done??

Thanks in advance for any advice,

RoyJ

---

### Post by JebusWankel on 2008-11-16
The volume control applet may be set to adjust the wrong audio interface. Try creating a new one by right-clicking the panel, clicking add to panel, and pick the volume control applet. If that doesn't work, right click the applet and select open volume control and try different devices from the drop down.

---

### Post by fredbird67 on 2008-11-23
Jebus, you've pointed me in the right direction, but that didn't quite do it for me.  Here's what did it for me instead:

I right-clicked the volume control, selected "Preferences", and selected "PCM", and that did the trick!  Now, I can control the volume of ANYTHING from that one single volume control! :guitar:

---

