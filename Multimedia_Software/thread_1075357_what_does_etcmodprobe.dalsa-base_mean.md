---
title: "what does /etc/modprobe.d/alsa-base mean"
date: 2009-02-20
forum: Multimedia Software
---

### Post by PhiJ on 2009-02-20
My friend has a laptop with hardy on it.  I was fiddling around trying to fix an audio problem she's had, and I found that I probably need to understand the content of alsa-base.  It's a lot of code which I don't understand, and I can't seem to find any well commented examples or documentation for it on the internet.  
Anyone know what all the code does?

---

### Post by markbuntu on 2009-02-20
In a nutshell the alsa-base file is where modprobe looks for options to load the sound driver into the kernel with. The driver itself should be autodetected and loaded automatically but the alsa-base file is used to set some parameters for the driver such as loading order and optional configurations which the modprobe autodetection may not be able to parse.

For example, You tell modprobe to load the snd-hda-intel with the option snd-hda-intel model=hp and it will configure the driver to match the particular configuration used in some hp machines.

---

### Post by PhiJ on 2009-02-22
What do the commands 'install' [S]and 'option'[/S] mean then?  Also, just out of interest, does alias mean anything?  Because on my (gentoo) system there is what seems to be a similar file (same location, called alsa), but it contains lots of code saying 'alias' and no 'install' [S]or 'option'[/S] commands

---

### Post by markbuntu on 2009-02-22
Alias is a way to use ther names of your choosing for sound device drivers. You can find out more about that at alsa.org.
The install command was originally used to install the drivers directly but now is used to direct modprobe where to install the drivers if you need to explicitly direct it to. If you notice, all the install commands also have an --ignore command. This is basically a left over from before automatic detection.

---

### Post by PhiJ on 2009-02-25
Am I right in thinking that modprobe detects what sound driver you need to load, looks in modprobe.d to see if any special options are needed, and then loads it?

Also, what's the
install sound-slot-0 /sbin/modprobe snd-card-0
for?  Is that old OSS stuff?

---

### Post by markbuntu on 2009-02-25
No, I think that tells modprobe.d where to put the driver in the kernel stack.

---

