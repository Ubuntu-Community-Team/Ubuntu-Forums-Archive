---
title: "i810 driver issue"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by marksten on 2007-08-07
Hello-

I'm using Ubuntu Feisty Fawn (7.04) 64-bit. My computer has the Intel 945GT chipset and I'm using the Intel i810 video drivers. I'm connected to an HDTV via HDMI cable.

The driver would not recognize any widescreen resolutions - my only options were some standard resolutions (640x480, 800x600, 1024x768, and 1280x1024). So the system was usable but only a small portion of the display was active. According to the HDTV manual the TV should advertise 640x480, 720x480, and 1920x1080 resolutions. In Windows Vista these are detected and everything works fine.

After snooping around the Xorg.0.log file it appears the system is correctly detecting the TV's output modes. The file even includes the detailed Modelines for the three resolutions it advertises.

I added these to the xorg.conf file but had no success (the available resolutions did not change). I then upgraded the drivers from i810 to intel but that turned out to be a semi disaster. The desktop area was enormous and the display was a window on a small section. I could not scroll around the desktop. Furthermore when I attempted to change the resolution the Screen Resolution app was reporting bizarre resolutions (1920x1920 among others I cannot remember).

After restoring the i810 drivers, installing 915resolution, and creating a startup script to over-write the 1600x1200 resolution in the video BIOS (based on a posting I saw in these fora) I was finally able to use 1920x1080. However, the system defaults back to 1280x1024 upon restart. I have to force an xserver restart for the system to see the 1920x1080 resolution and adopt it.

Anyone have any ideas how I can avoid forcing xserver to restart? or even better have any clue why the updated intel drivers fail to work?

Thanks for your help!

---

