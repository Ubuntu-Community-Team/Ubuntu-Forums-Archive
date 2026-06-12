---
title: "Need Help With BFG Nvidia 6800 OC AGP &amp; Dell 2001 FP"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by shoki on 2006-07-18
Hello All,

I am a beginner with ubuntu 6.06. I can not seem to get the 8762 Nvidia Drivers to work with my system. I have tried tseliot's methods 1 and 2 I have used his script, I tried the Automatix script and installing the driver with Nvidia's package.

My xorg.conf file seems correct but when I restart gdm the screen just come back with a black screen. The system is running but the monitor is essentially off. I can even hear the login sound.

Are there any logs I can post or or anything I am missing?

Thanks and sorry for the silly question. I have been at this for several days now and I would just be super psyched to be running 1600x1200 at full speed.

Thanks again,
--Shoki

---

### Post by tseliot on 2006-07-18
Try point 4 of the Problems Section of my guide:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by shoki on 2006-07-19
TS,

Well thank you so much for all your efforts. I reinstalled everything and tried method 1 again... Still blank screen. No mouse just black screen as if it is receiving no signal.

The screen is an LCD flat screen and I am using the DVI port. I did add the option lines as noted in section 4 including turning off the 3d Accel... Still no luck.

If you have any other ideas or if there are any logs or reports i can create just let me know. I guess I'll head over to the NvFourms and see if they can give me another push in the right direction.

Thank you again,
--Shoki

---

### Post by shoki on 2006-07-19
Yippie!!!!:D 

Not sure a big wet kiss is in order here but just let me say thank you once again.

Looks like I did not need Section 4... I removed all the option lines with the exception of AGP 0

I also found and added

    Option "ConnectedMonitor" "DPF"

and that seemed to be the magic bullet for me.

Thank The Lor... I mean TS :)

now to start work on my Canon iP4000 and my Skype Account working!!!

AWESOME

Thank you!
--Shoki

---

