---
title: "Help with x window"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by jester805 on 2006-10-10
I just re-installed Ubuntu and was trying to get my sound working.  I followed the instructions under **Getting the ALSA drivers from a *fresh* kernal** located here:  **[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)**.

I did this:
**sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils**

Then this:
**sudo apt-get install linux-sound-base alsa-base alsa-utils**

And finally this:
**sudo apt-get install gdm ubuntu-desktop**

It keeps telling me the following packages have unmet dependencies:
ubuntu-desktop:
[INDENT]Depends:  gnome-applets but it is not going to be installed[/INDENT]
[INDENT]Depends:  gnome-panel but it is not going to be installed[/INDENT]
[INDENT]Depends:  gnome-terminal but it is not going to be installed[/INDENT]
E:  Broken packages

I have also tried doing this:
[B]sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start[/B]

I'm not sure what else to do.  Can you please help me to get my desktop back?  Right now it just sits at a command line.

Thanks!

---

### Post by CatKiller on 2006-10-10
I don't know a huge amount about this, but does ```
sudo apt-get install gdm ubuntu-desktop gnome-applets gnome-panel gnome-terminal
```work any better for you?

---

