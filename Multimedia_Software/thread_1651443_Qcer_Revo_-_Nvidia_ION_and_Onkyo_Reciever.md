---
title: "Qcer Revo - Nvidia ION and Onkyo Reciever"
date: 2010-12-23
forum: Multimedia Software
---

### Post by slice16 on 2010-12-23
Hi All,

I recently purchased an Acer Revo R3760 which came bundled with Windows 7.  The intention was to use this PC for a media centre.

Before I get into the issue, this is my setup:

Acer Revo R3760 &#61664; hdmi &#61664; Onkyo HT-R380 &#61664; hdmi &#61664; Hitachi LCD TV

So, out of the box I boot up Windows 7 and everything displays fine.  I install Ubuntu still using my TV and not PC monitor and everything is fine.  Once Ubuntu is on there I have 1024x768 display which is the maximum the standard drivers will show for my TV.

The issue occurs when I install the nVidia ION drivers via the additional driver function in Ubuntu (I have also attempted to download them manually from the nVidia site).  Once I install the driver and reboot, I see the loading screen for Ubuntu then the display screws up (blue screen, black screen, a little of the Ubuntu background fuzzy, blue screen … and so on).  

If I attach the hdmi directly to the TV, I get 1080p resolution and it looks perfect.  Plug back into the amp and issue still occurs.

If I plug a monitor into the Revo, I can see that nVidia is detecting my hdmi display as ONK … 

While the PC monitor is attached I run gdm stop, and my TV will display the console perfectly.  

I’ve googled around and can’t find any fix so far.  The HDMI out on the Revo supports audio out which is why I need it running through the amp.  I think this may have something to do with the issue I’m having.  At first I thought it could be the EDID pass through on the amp, but this wouldn’t explain why it worked on windows 7 and Ubuntu post driver install.

Any ideas would be welcome.

---

### Post by tjones00 on 2010-12-23
If this setup pc > amp > tv works properly in windows then issue you're having probably has to do with something called EDID.

EDID is the display information that your TV sends your nvidia card/hardware upon probe listing all it's display values.

To me it appears that if you place the amp between your tv and the pc the edid information isn't being gathered properly in linux.

I don't have a lot of time so I'll try to get you on the right track.

Look up the "customEDID" command for xorg.conf and get the working edid.bin from windows then use this file in linux.

You can gather an edid.bin linux with nvidia-settings or in windows with numerous 3rd party software.

---

### Post by slice16 on 2010-12-29
Thanks TJones00, I will give this a try and get back to you.

Cheers,

Paul

---

