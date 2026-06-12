---
title: "saving settings - Gnome alsa mixer"
date: 2009-11-19
forum: Multimedia Software
---

### Post by hotshot247 on 2009-11-19
my sound hasn't been working on my laptop for a while and i figured out that i can uncheck the "external amplifier" in gnome alsa mixer and the sound will work. for some reason though, it doesn't save when i shutdown my computer and restart it. how do i save the settings?

---

### Post by howl at the moon on 2010-01-17
Hi hotshot247.  I was having same problem and found this ;)

Log in as usual, setup your volume controls to your satisfaction. Then, open a terminal, and give the command     Code:
     sudo alsactl store 0
sudp cp -p /etc/asound.state . 
.

This will store your current sound settings to a file in /etc/asound.state, and create a copy of that file in your home directory.

You can now reboot and check if the saved values  "stick". If they don't try reloading the saved settings with the command     Code:
     sudo alsactl restore 
 Your saved sound settings should be loaded immediately.

If they don't, you may not have permissions on /etc/asound.state, or the file itself may be marked immutable.

In this case, copy back the asound.state file saved in your home directory, then restore:      Code:
     sudo cp -p asound.state /etc/asound.state && alsactl restore 
 If this works, then you need to check why your asound.state file is getting replaced on every bootup.

You can copy your custom asound.state file to /etc, and make it immutable (unchangeable) with the command     Code:
     sudo chattr +i /etc/asound.state 
 WARNING: With this, your laptop will always START with the custom set volume levels; you can adjust the settings, but they will not be "remembered" across reboots.

it comes from here
[http://ubuntuforums.org/showthread.php?t=1298630&highlight=settings+save+gnome+alsa](http://ubuntuforums.org/showthread.php?t=1298630&highlight=settings+save+gnome+alsa)

***sorry, all the boxes didn't come through, making it hard to read.  go to thread***

---

### Post by Zen SoSo on 2010-03-03
This problem bugged me for awhile, after creating an XBMC-only box. I don't know if it's because the XBMC session didn't load gnome or any of its associated geegaws, or what. What I ended up finding out was that the sound state is set and restored when the system changes runlevel, meaning every time you turn it off or on. You need to make sure that this is happening correctly.

In /etc/rcS.d, you should find a file named something like S50alsa-utils.

If you don't, find out if you've got one in one of the other runlevel directories. Do it like this:

```
find /etc/rc* | grep alsa
```

Or you can copy mine to your computer, if you're brave. I'm using 9.04 (Jaunty). I've uploaded it as an attachment.

---

### Post by .Japanish on 2011-01-28
Hi, thanks for commands. I'm new for Linux, recently installed Xbuntu 10.10 (ja) on VersaPro with same issue of External Amplifier and saving the setting. Alsa setting sure was saved, but my Xbuntu doesn't have asound.state so I made a launcher with the command of restore and put it in /home/user/autostart
it works as a workaround, but still looking for the correct way of setting.

---

