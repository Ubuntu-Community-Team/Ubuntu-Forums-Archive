---
title: "Revert to Ubuntu's default video drivers."
date: 2010-06-17
forum: Multimedia Software
---

### Post by artursm on 2010-06-17
When Lucid Lynx came out I did a clean install on my laptop by burning an iso. Unfortunately, I got an annoying bug in which the image would always be wiggly (wavy) in the external monitor. In an attempt to fix the issue, I tried to installed Ati's restricted drivers. Unfortunately, my graphics card (Radeon x1200) isn't supported by them on Ubuntu 10.04, and trying to install it anyway only made things worse. 

Right now, I just want it to be back to what it was when I first installed Lucid. Following the instructions on [this]("https://help.ubuntu.com/community/RadeonDriver") page, I have already removed the fglrx drivers, and I think I installed the open-source driver. However, I can tell that things are not the way they were when I first installed. By going in "Main menu > System > Preferences > Monitors" I get the usual menu to configure the monitors, except I can't actually configure anything. There's only one monitor (listed as Unknown), and the system doesn't let me change any of the settings (such as resolution or frequency). The external monitor is showing the same output as the laptop monitor, and doesn't get recognized by the system.

What can I do to fix this? **I just want to use the exact graphics drivers that came installed in Ubuntu 10.04 Lucid Lynx.**But I don't want to do a clean install.

Thanks

---

### Post by artursm on 2010-06-18
Ok, I feel stupid now. I had already checked xorg.conf for any mentions of fglrx, but I hadn't actually tried removing the file entirely. I just removed my /etc/X11/xorg.conf file, and everything is back the way it was. 

I'm still getting extreme wavy/wigglyness in the external monitor, but at least it's being recognized and stuff. 

If anyone has any hints on how to fix the wavyness, please I'm getting desperate.

---

