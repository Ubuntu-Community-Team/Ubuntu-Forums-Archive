---
title: "NVIDIA X Server settings not saved after reboot?"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by LadyFox on 2007-09-23
I'm having a real issue with NVIDIA X Server settings (under Apps).   Each time, i make the appropriate changes to activate my second monitor and change the resolution. This is all fine until i reboot and the changes are lost.  I have to re-make all these changes again.  Can anyone advise where i am going wrong?

When i make the changes in NVIDIA X Server settings, under Display Configuration, i click 'save to X configuration file' and i get the message "Unable to remove old x config backup file ;etc/X11/xorg.conf.backup'.   I have tried rm that file, but then it tells me that it cant create that file.  Im not sure what the issue is there, or if that is why it cant save my changes. 

Can anyone advise?  The only similar thread to this topic i found is [this one]("http://ubuntuforums.org/showthread.php?t=259469"), though the solution link is dead. 

Any help would be most appreciated!!

---

### Post by niller on 2007-09-23
Hi there

Try follow this instructions, seems to work ):P

[http://www.linuxmint.com/forum/viewtopic.php?t=3908&sid=4a49d9fff8c6134e45dc5540ac22b641](http://www.linuxmint.com/forum/viewtopic.php?t=3908&sid=4a49d9fff8c6134e45dc5540ac22b641)

---

### Post by Tech^CF on 2007-09-23
Run the program with administrative permissions:

Press: ALT + F2
Then write: *gksudo nvidia-settings* and press ENTER

Remember to save X configuration file (there is a button in the nvidia-settings application for that.

---

### Post by LadyFox on 2007-09-23
> **Tech^CF said:**
> Run the program with administrative permissions:

Press: ALT + F2
Then write: *gksudo nvidia-settings* and press ENTER

Remember to save X configuration file (there is a button in the nvidia-settings application for that.

Tried that, but its knocked the whole thing out.  Now it cant see my NV card at all, and its switched back to X server on my onboard i810 VGA.  Grr.

---

### Post by middlewordie on 2007-09-23
I've had similar problems, using the Nvidia Drivers (which seem to result in X server failing to start) and Envy (which works, but uses an older linux driver).

Eventually, I realised that Xorg.conf is only stays changed when you are logged in as Root.

So I logged in as Root and ran Envy. Now the drivers are installed.

---

### Post by fenian on 2007-09-23
Try this run...

> sudo gedit /etc/X11/xorg.conf

Don't change anything and save as xorg.conf.backup

then run...

> sudo nvidia-settings

enter your settings,save to X configuration file and restart X (ctrl+alt+backspace).

---

### Post by LadyFox on 2007-09-24
> **fenian said:**
> Try this run...



Don't change anything and save as xorg.conf.backup

then run...



enter your settings,save to X configuration file and restart X (ctrl+alt+backspace).


Nope, exactly the same as before.  Goes back to X Server on my onboard graphics card rather than the NVIDIA.  Looks like there might be something wrong somewhere but i dont know what.

---

### Post by dabl on 2007-09-24
> **middlewordie said:**
> 

 and Envy (which works, but uses an older linux driver).



Not any more -- Envy now installs ver. -100.14.19.  :popcorn:

---

### Post by raashell on 2007-09-28
I have the same problem.  I've tried both approaches, running and saving as root, and following all the instruction's in Niller's link.

  What is worth adding, is that I did Niller's link's instructions first without luck and then tried to run as root.  I actually logged in as root, changed the Nvidia Settings and then restarted.  As my normal user, the settings did not stick, but when I logged in as root, they did.  Using gksudo to save the config file had no impact as a normal user.

  These are from my Xsession Error File and might be of some use, the first dealing with Niller's mintLinux link and the second with trying to save NVidia's settings:

1. /etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "[COLOR="SeaGreen"]" -l ":0"[/COLOR] "john"

2.ERROR: Unable to create backup file '/etc/X11/xorg.conf.backup'.

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

   And here are a few sections of my xorg.conf:

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1680x1050 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Note: 1680 x 1050 is what I am trying to maintain.   Also, when I play WOW (oh yes), it will change the resolution slightly upon entering the program, and when I exit it reverts to 1024 x 768.

John

---

