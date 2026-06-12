---
title: "I may have just wrecked everything....wrong screen resolution on a laptop?"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by NoPantsJim on 2007-12-23
I am running a 17" Dell laptop w/ screen resolution 1920x1200. I tried changing it to 1920x1080 for a multimedia presentation on an HDTV. After restarting, I get the Ubuntu loading screen with the progress bar, but then a black screen where the login screen should be. If I type my username, hit enter, then type my password, I hear the normal Ubuntu startup sound, but the screen remains blank.

I am able to login to a terminal and get a command prompt, but at that point I'm stuck. Having to re-install Ubuntu wouldn't be the end of the world, but there are a few small things on the hard drive I would lose in the process.

The laptop has a 128MB NVIDIA GeForce Go 8400 graphics card and was running the latest Nvidia linux drivers at the time of death. Ubuntu was version 7.10.

---

### Post by reidy90 on 2007-12-23
You'll be right mate. Plug your laptop into an external computer monitor that can handle that sort of resolution and you will be able to change the resolution back to what suits your laptop. I have done this myself in the past.

Alternatively if you can get to the CLI via the GRUB bootloader you can manually edit your /etc/X11/xorg.conf configuration file. But the first option should be easier.

---

### Post by NoPantsJim on 2007-12-23
Thanks. Unfortunatly I'm still at work and there's no 1080p tvs around here, gotta wait til I get home.

It's a good thing you posted when you did, I had pretty much decided to just FTP a select few files and then wipe the HD/reinstall after getting off work, but this will be much easier.

---

### Post by NoPantsJim on 2007-12-23
Darn, didn't work, and I honestly haven't got the time to go through the xconf files. :(

Luckily, the bootable live cd worked just fine and I was able to save all my files.

---

