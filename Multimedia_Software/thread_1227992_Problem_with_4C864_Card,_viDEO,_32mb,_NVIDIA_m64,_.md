---
title: "Problem with 4C864 Card, viDEO, 32mb, NVIDIA m64, AGP"
date: 2009-07-31
forum: Multimedia Software
---

### Post by Kawa800 on 2009-07-31
I am trying to get better than 600x800 resolution on a recent install of Ubuntu 9.04 on a Dell Dimension 4100.  The video card is 4C864 Card, viDEO, 32mb, NVIDIA m64, ACCELERATED GRAPHICS PORT...

Installed EnvyNG, selected compatable/recommended driver - NVIDIA 71.86.08.0ubuntu1 and clicked apply.  Successfully installed and required reboot.

Upon reboot I get:
Ubuntu is running in low-graphics mode
The following error was encountered.  You may need to update your configuration to solve this.

(EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available

Then get: 

"What would you like to do?
o RunUbuntu in low-graphics mode for just one session
o Reconfigure graphics
o Troubleshoot the error
o Exit to console login"

I choose to run in low graphics mode, then get:

"There already appears to be an X server running on display :0.  Should another display number by tried? Answering no will causeGDM to attempt starting the server on :0 again.  (You can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go to consol 7.  Xservers usually run on consoles 7 and higher.)"

Select the default, "yes"

Ubuntu loads.


When running System>Administration>Nvidia X Server Settings, I get:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

In terminal:
kids@kids-desktop:~$ sudo nvidia-xconfig
[sudo] password for kids: 
sudo: nvidia-xconfig: command not found

This popped up once when I went back into Nvidia X Server Settings
"EnvyNG - The KDE Crash Handler
A Fatal Error Occurred
The application EnvyNG () crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at [http://bugs.kde.org](http://bugs.kde.org). Useful details include how to reproduce the error, documents that were loaded, etc."

Anyone have any tips?  I suspect something should happen when I type "sudo nvidia-xconfig".  Am I doing something wrong?

In previous versions of Ubuntu the card was listed under hardware drivers and I was able to just enable it there and be off and running with no problem.

---

