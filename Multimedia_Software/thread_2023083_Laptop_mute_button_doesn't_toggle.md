---
title: "Laptop mute button doesn't toggle"
date: 2012-07-12
forum: Multimedia Software
---

### Post by DanBender on 2012-07-12
Heyyo!

I'm having a problem with muting and unmuting sound on my laptop.

Just to avoid confusion - sound works. Software volume controls and mute/unmute work. Hardware volume control buttons work.

Hardware mute button...half works. When I press the "mute" key, it throws the mute flag; there's an indicator that flashes onto the screen (I think it's hardware-driven) which comes up when the volume buttons are used, which also shows that it's been muted. The xfce4-indicator also confirms that the mute flag has been set.

However, when I press the "mute" button again, the *hardware* indicator claims the sound is back on, but there is no sound. The xfce4-indicator shows that the sound is still muted. I can keep pressing the mute key and the hardware indicator switches back and forth, but I don't get any sound until I pop the xfce4-indicator up and set it to "Unmute."

If I use the software mute from the indicator plugin, the hardware indicator follows suit. So it looks like what's going on is the operating system is mis-interpreting the hardware mute button as always sending a "set mute" command instead of a "toggle mute" command, or something like that. But I'm not finding any information to verify what the button is commanding or how to change it. The poster in [this thread]("http://ubuntuforums.org/showthread.php?t=2001690") seems to be having a very similar problem, but he didn't provide enough details for me to find the files he mentioned.

I'm running xubuntu 12.04 (actually a qimo-session, but I doubt that's the problem) on a Dell Latitude D610, and I believe it's set to be using PulseAudio (the hardware volume buttons are working more consistently with that selection than the ALSA selection - as in, they currently work at all).

Thank you in advance for your help!

---

### Post by LewisTM on 2012-07-12
These two bug reports offer several ways to solve your problem. The one using xfce4-settings-editor worked for me.

[https://bugs.launchpad.net/ubuntu/+source/xfce4-volumed/+bug/885956](https://bugs.launchpad.net/ubuntu/+source/xfce4-volumed/+bug/885956)
[https://bugs.launchpad.net/bugs/883485](https://bugs.launchpad.net/bugs/883485)

---

### Post by DanBender on 2012-07-13
Excellent excellent. The settings-editor method was it. Had to figure out the proper value to apply, but that was easy enough to work out from the suggestion in m321v123m's post in the first launchpad thread and the other mixer settings shown.

I see I'll need to start paying attention to the launchpad system in the future when I have problems. Haven't really followed bugtrackers before.

Thank you, LewisTM.

---

