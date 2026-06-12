---
title: "Nvidia TNT2 board"
date: 2010-09-30
forum: Multimedia Software
---

### Post by jgw on 2010-09-30
I have an Nvidia NV5M64[Riva TNT2 Model 64] display (board).  I am currently told by Hardware Drivers that I am using the Nvidia Accelerated Grap;hics Driver (Verson Current) 195.36.24 Oubuntu1-10.04  
I just downloaded, from Nvidia their latest and greatest:
(Linux-X86-71.76.14.pkg1.run).

When I went to NVIDIA X server settings I was told that I was not using an Nvidia driver and I should do an X configuration, I did that and created a new xorg.conf file.  I then re-booted and the machine told me that it could not initialize the Nvidia kernal and could not find the driver. I then went back to the original screen as installed when I installed 10.04.

I had thought everything was dandy.  The screen came up as 1024x768, I was told by the hardware manager that I was using the right driver and so I left everything alone.  Then I tried to install and play a game and was told that there was no 3d, etc.  So, here I am,  The hardware drivers tells me one thing, the nvidia settings tells me something else and the automatically generated xorg.conf file doesn't work (it does, however, know that we are dealing with an Nvidia board.  I downloaded the Nvidia driver, from Nvidia on spec but have no idea what to do with it.

Any thoughts on this one would be appreciated as I have no clue.  
Thank you..............

Since the above was written I have gone into the network tools and removed the nvidia driver just to see what would happen.  What happened was absolutely NOTHING.  Now I am going to try and install the run file from Nvidia and see what that does.

Failed with the run file (even with sudo I didn't have permission)  then I went to the package manager and re-installed all the nvidia stuff and re-started.  Checked the hardware drivers and activated same and re-started yet again.  Then I checked the hardware drivers and it told me that the driver was installed, activated and being used.  I then went to the nvidia settings and was told that I was not using an nvidia board so do a nvidia-configure which would take care of the problem.  I did that and re-booted.  It blew up again and then brought up my desktop.  Checked nvidia settings and saw the same thing.  I then took the xorg.conf file, that I had on another machine (which works just fine), and put it on this machine.  After re-booting it then told me "(EE) No Devices Detected".  Now I am back to run, reconfigure, etc. (been here before).

I am running out of things to do!

I have now pretty much given up.  I have no idea if that means this is solved or not.  I finally read a log file that explained that the latest drivers will not recognize my board as its simply too old.  The driver that will work is not available although there are a couple of other drivers but they are either in development or not supported.

---

