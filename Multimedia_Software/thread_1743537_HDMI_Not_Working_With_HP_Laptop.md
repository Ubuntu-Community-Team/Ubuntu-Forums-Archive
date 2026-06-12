---
title: "HDMI Not Working With HP Laptop"
date: 2011-04-29
forum: Multimedia Software
---

### Post by malalation on 2011-04-29
Hello Experts,

I recently installed Ubuntu 11.04 on my** HP Pavilion dv4-1040ee** laptop which was shipped with **nVidia GeForce 9200M GS** graphics card, the only problem that I'm currently facing is that the computer was not able to detect my screen by using the HDMI port. So, I thought that may be it was a driver's issue so I installed the latest nVidia dirvers by using the command 

```
sudo apt-get install nvidia-current
```

When I restarted the computer nVidia's logo appeared during booting and** nVidia X Server Settings** program was installed which indicates that the driver was installed successfully on the machine!

But still I was not able to connect to my screen by using HDMI.

Can you please help me out there??

Is there a command that I'm suppose to issue to switch to HDMI or it's suppose to detect it automatically?

---

### Post by malalation on 2011-04-30
Hey guys,

The problem was solved!

In **nVidia X Server Settings** go to **X Server Display Configuration** and then click the button **Detect Displays** (make sure that your HDMI cable is connected to the computer and the TV is set to the HDMI input before clicking the button), this should show you the screen and then you can click on the screen's box, click on **configure...  **button, do your configs ;)

The video worked, but still I'm not able to get the audio!!!

---

### Post by martinob on 2011-09-25
any news about audio?

---

### Post by gawryl77 on 2011-09-26
i had the same problem. don't remember where i have found the solution, but to enable the audio in (my favorite) mplayer i have to write:

mplayer -ao alsa:device=hw=0.3 movie.avi

and it works. so, maybe look for this magic commands ;) good luck! ;)

---

### Post by BicyclerBoy on 2011-09-26
Post the output from
aplay -l

cat /proc/asound/card1/*

dmesg | grep HDMI

I'm fairly sure the 9200m chipset only supports 2ch stereo PCM & AC3 over HDMI.

---

