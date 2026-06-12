---
title: "Sysytem not remembering nVidia settings"
date: 2008-08-02
forum: Multimedia Software
---

### Post by pravin03 on 2008-08-02
i installed new nVidia driver for my GeForce 8400GS using EnvyNG. But the system is not remembering the screen resolution,refresh rate and other settings I keep in nVidia-settings.

I saved the configuration to /usr/X11 as xorg.conf.10. Then also the error is repeating.

(The refreshrate I set(75Hz) is not displayed in Screen Resolution settings(System->Preferences->Screen Resolution.)There it is 66Hz.
I am using LCD monitor(LG L177WSB)but in settings it is shown as CRT-0.

---

### Post by mikewhatever on 2008-08-02
Run **gksudo displayconfig-gtk** and set the correct parameters for your screen. Before doing that, backup xorg with **sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup**

---

### Post by pravin03 on 2008-08-02
The name of my monitor is not there in the list

---

### Post by mikewhatever on 2008-08-02
Never mind the name, select 'generic monitor', correct resolution, etc.

---

### Post by pravin03 on 2008-08-02
No its not remembering it even now.
I uninstalled the driver using envy and reinstalled the one that was working for me from repo. Now the same problem reappears.What may be wrong with my system?

---

### Post by pravin03 on 2008-08-04
[http://ubuntuforums.org/showthread.php?t=879476](http://ubuntuforums.org/showthread.php?t=879476)


AS in this thread I reinstalled the whole thing.

I got Driverophobia. please don't tell me anything that will make me remember that pretty old problem.

---

