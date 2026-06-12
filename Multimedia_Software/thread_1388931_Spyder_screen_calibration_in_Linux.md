---
title: "Spyder screen calibration in Linux"
date: 2010-01-23
forum: Multimedia Software
---

### Post by Turin Turambar on 2010-01-23
I received a bunch of letters asking me whether it is possible to use Spyder or other calibrators in Linux.

Well, I'm YET to try Spyder PRO in VirtualBox under Vistax64 (I HIGHLY recommend VirtualBox for anything windows-related!), but you CAN use the calibrated file that Spyder made it in windows.
Just locate the *.icm file under Windows dir and copy it to the linux partition. Then apt-get the program "xcalib" that will load the file in video memory.

Run xcalib with the file you provided. You'll have a perfectly calibrated display right away!
Go to System>Preferences>Startup Apps and add it to the startup programs.
This way, xcalib will run on boot. The loading is instant - way quicker and Linux/Ubuntu doesn't try to overwrite the video memory like windows does, nor it uses any resources. Way to go!

---

