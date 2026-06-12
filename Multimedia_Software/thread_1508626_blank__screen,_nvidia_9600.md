---
title: "blank  screen, nvidia 9600"
date: 2010-06-13
forum: Multimedia Software
---

### Post by gleft on 2010-06-13
hello friends, i have a problem with my laptop. It's a hp dv7 1020ev and i just installed ubuntu 9.10. Everything was fine until i installed the recommended nvidia drivers. After the reboot, i hear the sound but i see nothing. I followed the instructions here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) but the problem remains. I can only use recovery mode, but there is only the command line, the display doesn't work on normal startup. Anyone has any suggestions?

---

### Post by Deadite81 on 2010-06-13
Running this command will automatically configure your xconf file.  Helped me, but I can't say for sure whether it'll help you (won't hurt anyway:))

```
sudo nvidia-xconfig
```

Then "sudo reboot".

Perhaps that'll help.

---

### Post by gleft on 2010-06-13
it was the first thing i tried my friend, it didn't work. then i tried to make the change that i found in help.ubuntu in the new file but again nothing..

---

### Post by gleft on 2010-06-14
doesn't anyone have any ideas?

---

### Post by Deadite81 on 2010-06-14
I have never delt with your particular problem,but since I use Nvidia and have delt with many other issues perhaps I can give maybe help at least knock out some possibilities. (This maybe rather long, sorry about that :).)

First, you should check to see that your startup entry to load your Nvidia configuration exists.  I don't know how familiar you are with the command line or file locations, so...
(Using a virtual term maybe easier, see the bottom.)

After you've logged in type:
```
cd ~/.config/autostart
```Then type:
```
ls
```You should see a list of .desktop files, one of which should be "nvidia-autostart.desktop".  These are the executable files loaded at boot.  To see what yours says, assuming you have one, type:
```
nano ~/.config/autostart/nvidia-autostart.desktop
```Mine reads:
```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=NVIDIA X Server Settings
Comment=Configure NVIDIA X Server Settings
Exec=sh -c '/usr/bin/nvidia-settings --load-config-only'
Terminal=false
Icon=nvidia-current-settings
Categories=System;Settings;

```The "Exec" line is the command actually run (sh -c '/usr/bin/nvidia-settings --load-config-only'), the rest is pretty much irrelevant.  Instead of logging into failsafe, if you can get to your blank screen with sound, press :Ctrl+Alt+F1".  This should drop you into a virtual terminal, which is actually separated from your graphical xsession.  (Virtualization on newer computers won't work unless it is enabled in the systen bios, btw.)

You will have to type your username and password, then you can try running that command and see what the output is.  If it works, if this is in fact the problem, you can then press "Ctrl+Alt+F7" to return to your xsession without all the rebooting.  You shouldn't have to reboot because this command is run at the time your desktop is loaded, not when your computer is booted up.  You never specified whether you can see your login screen but not your desktop, so I don't know if this is applicable at all.

If you would like me to post my xconf file for comparison, let me know.

---

### Post by gleft on 2010-06-15
i do not see nothing, i hear the sound, but nothing appears on the screen, not even the login screen, so i do not think that what you say might work

---

